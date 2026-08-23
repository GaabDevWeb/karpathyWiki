---
id: kernelbot-known-issues
tipo: known-issues
status: atual
atualizado: 2026-08-23
---

# Problemas, riscos e limitações conhecidas

## 1) Catálogo curricular indisponível em staging

### Observação

No ambiente de staging, `GET /api/curriculum` pode responder `503` por design quando `ACL_CATALOG_ENABLED=false`.

### Evidência

- `README.md` explica o comportamento esperado em staging
- `api/routes.py` devolve 503 se o catálogo não estiver disponível

### Status
Conforme ao design do ambiente, não é necessariamente um erro do sistema

## 2) Rate limit do endpoint de chat

### Observação

`POST /chat` está limitado a 30 requisições por IP a cada 60 segundos.

### Evidência

- `README.md` documenta o rate limit
- `api/routes.py` implementa `allow_request` com `limit=30` e `window=60s`

### Status
Implementado e documentado

## 3) Dependência crítica de MySQL para o índice funcional

### Observação

Sem banco MySQL e sem tabela `knowledge` corretamente alimentada, o núcleo de BM25 do projeto deixa de funcionar como esperado.

### Evidência

- `README.md` e `kernel/config.py` exigem DB settings
- `main.py` e `kernel/knowledge/database.py` dependem do banco para os chunks

### Status
Restrição arquitetural atual

## 4) Limitação de recall por BM25 léxico

### Observação

O projeto usa busca por termos e chunks; isso significa que sinónimos, paráfrases e perguntas vagas podem resultar em recall ruim se os termos não aparecerem no corpus.

### Evidência

- `docs/wiki/01-visao-geral.md` e `docs/wiki/06-gates-e-decisoes.md` registram limitações do BM25

### Status
Conhecida e documentada

## 5) Histórico e pin como solução POC

### Observação

O histórico e o pin são voltados para sessão local e não para um sistema de usuários autenticados ou persistência robusta.

### Evidência

- `kernel/memory/pinned_store.py`, `kernel/memory/transcript_store.py` e `api/routes_v1.py` tratam transcript/pin como contexto de sessão in-process

### Status
Conhecido; funcional para uso local/demo, não como solução de produção multiusuário

## 6) Divergência possível entre catálogo ISS e índice

### Observação

O sistema possui `catalog_drift_report` e endpoints de saúde para comparar catálogo e índice. Isso é um sinal de que o projeto trata como risco operacional diferença de dados entre ISS e índice.

### Evidência

- `api/routes.py` expõe `/health/catalog`
- `kernel/knowledge/catalog_sync.py` e `kernel/config.py` tratam de variáveis de catálogo e drift

### Status
Risco operacional conhecido; precisa de monitoramento e manutenção

## 7) `bootstrap_catalog_state` sem import em `main.py`

### Observação

`build_services()` chama `bootstrap_catalog_state` sem o importar. A função existe em `kernel/knowledge/catalog_sync.py`.

### Evidência

- `/home/gaab/Documentos/gitHub/KernelBot/main.py`
- `/home/gaab/Documentos/gitHub/KernelBot/kernel/knowledge/catalog_sync.py`

### Status
Bug CURRENT. Wiki não altera código.

## 8) README nega UI; Ops/Traces existem

### Observação

README: "Não inclui interface web". `app/factory.py` inclui `ops_router` e `traces_router` e monta estáticos Jinja.

### Status
Conflito docs vs código. Código vence.

## 9) Testes e pastas vazias `engine/` / `core/`

### Observação

Alguns testes ainda importam `engine.*` / `core.*`. Pastas sem código. CI da feature branch não dispara em push (só `main`/`master`).

### Status
Dívida. Taxa verde NÃO CONFIRMADA nesta auditoria.

## 10) Discord adapter é stub

`adapters/discord/outbound.py` devolve `discord_not_implemented`. Não documentar Discord como canal activo.
