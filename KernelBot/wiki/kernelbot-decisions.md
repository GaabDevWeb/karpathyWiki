---
id: kernelbot-decisions
tipo: decisions
status: atual
atualizado: 2026-08-23
fonte:
	- "raw/docs-wiki/06-gates-e-decisoes.md"
---

# Decisões arquitéticas e técnicas relevantes

## 1) Persistência do conteúdo de ensino em MySQL

### Contexto

O projeto precisa responder com base em material indexado de aulas e manter um corpus utilizável em produção.

### Decisão

O conteúdo é guardado em MySQL e consultado por BM25 em memória via `SearchEngine`.

### Motivo

- mantém um corpus centralizado e consultável
- suporta `reload` e reconciliação do catálogo ISS
- reduz a dependência de um serviço externo de vector DB

### Evidência

- `README.md` documenta MySQL e `knowledge`
- `main.py` e `core/config.py` referem-se a `db_host`, `db_name` e `knowledge`
- `docs/wiki/04-dados-e-mysql.md` explica a tabela e a lógica de chunking

### Status
Atual

## 2) Retrieval léxico em vez de embeddings semânticos

### Contexto

O projeto prioriza resposta ancorada e sem alucinação, com foco pedagógico.

### Decisão

O kernel usa BM25/Okapi e gates de retrieval para escolher chunks antes da geração.

### Motivo

- coerência com material acadêmico e resposta baseada em fontes
- controlo explícito de confiança e de termos informativos
- combate à alucinação usando `reason` e flags de pós-geração

### Evidência

- `docs/wiki/05-bm25-chunking.md`
- `docs/wiki/06-gates-e-decisoes.md`
- `kernel/rag/search.py` e `kernel/rag/retrieval.py`

### Status
Atual

## 3) Provider LLM configurável

### Contexto

O projeto deve funcionar com múltiplos provedores sem reescrever a camada de chat.

### Decisão

O provider é selecionado por variável de ambiente e o código aceita `openrouter` ou `cursor`.

### Motivo

- adaptabilidade operacional
- possibilidade de alternar entre provedores sem mexer na lógica da aplicação

### Evidência

- `core/config.py` define `LLMProvider = Literal["openrouter", "cursor"]`
- `README.md` menciona OpenRouter ou Cursor SDK

### Status
Atual

## 4) Separação entre staging e produção

### Contexto

O projeto precisa ter comportamento operacional distinto em ambiente local de desenvolvimento e em produção pública.

### Decisão

Os scripts de staging usam `KERNELBOT_ENV=staging`, `ACL_CATALOG_ENABLED=false` e um banco local para testes; a produção exige catálogo e token de reload.

### Motivo

- reduzir risco de erro em ambiente de desenvolvimento
- manter um comportamento explícito para CI e operacionais

### Evidência

- `README.md` — sessão “Staging vs produção”
- `bin/staging-serve.sh` e `docker-compose.*`

### Status
Atual

## 5) Política de grounding e advisory orientada a evidência

### Contexto

O projeto quer dar respostas úteis sem abandonar a ancoragem ao material.

### Decisão

A resposta usa `ACL_GROUNDING_POLICY` com valores `strict`, `anchored` e `hybrid`; a política `anchored` é default.

### Motivo

- priorizar fontes do corpus
- rotular extensão pedagógica quando houver espaço para complementar sem inventar
- manter avisos em vez de responder com veemência quando a evidência é débil

### Evidência

- `kernel/config.py`: `grounding_policy` e prompts de grounding
- `docs/wiki/06-gates-e-decisoes.md`
- `kernel/rag/retrieval.py`

### Status
Atual

## 6) Histórico de conversa e pin em sessão

### Contexto

O sistema tem necessidade de manter contexto e continuar discussões em sequência.

### Decisão

O projeto usa pin por sessão; em `/v1/chat` o transcript é gerido pelo `TranscriptStore` in-process (SSOT no Kernel para OrbitBot). Não é autenticação de utilizador.

### Motivo

- permitir continuidade simples sem gerenciar contas
- preservar foco do tema do usuário em conversa curta
- OrbitBot delega histórico ao Kernel via `POST /v1/chat` (confirmado em `src/openai.js`)

### Evidência

- `kernel/memory/transcript_store.py`, `kernel/memory/pinned_store.py`
- `kernel/orchestrator/context.py`
- `tests/test_v1_chat.py`
- UI legada com `localStorage` documentada em `raw/docs-wiki/` (histórico; frontend ausente na branch auditada)

### Status
Atual para `/v1/chat`; UI browser legada permanece POC/histórico

## Decisão histórica relevante a preservar

Há branches experimentais e históricas que apontam para trabalho em scraping, prompt interno e refactors de infraestrutura. A branch auditada `feature/kernel-orbit-v1-hardening` consolida integração Kernel↔Orbit com API v1; `main` remota pode divergir até merge.
