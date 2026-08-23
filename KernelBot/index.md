---
id: kernelbot-project
tipo: projeto
status: atual
projeto: kernelbot
dominio: ai
escopo: projeto
atualizado: 2026-08-23
confianca: alta
aliases:
  - KernelBot
  - Kernel Bot
fontes:
  - KernelBot/raw/README.md
  - KernelBot/index.md
relacionados:
  - orbitbot-project
  - gaabwiki-ecosystem
  - gaabwiki-terminology
tags:
  - kernelbot
  - ai
  - retrieval
---

# KernelBot

## Identidade do projeto

Projeto: KernelBot
Tipo: assistente educacional com recuperação léxica e integração LLM
Repositório de origem: /home/gaab/Documentos/gitHub/KernelBot
Branch auditada como estado atual: `feature/kernel-orbit-v1-hardening` (2026-08-23)
Branch `main` remota existe; o estado verificado no código local corresponde à branch de integração Kernel↔Orbit.
Data da análise: 2026-08-23

## Visão resumida

O KernelBot é um backend cognitivo educacional que usa BM25 sobre aulas indexadas em MySQL e envia trechos como evidência primária para um modelo LLM. O fluxo principal verificado é: `main.py` → `app/factory.py` → `api/routes.py` / `api/routes_v1.py` → `kernel/orchestrator/context.py` / `kernel/rag/search.py` / `kernel/rag/retrieval.py` → `kernel/providers/chat_provider.py`.

> **Nota histórica:** documentação em `raw/docs-wiki/` ainda referencia o pacote legado `engine/`. No código atual da branch auditada, os módulos vivem sob `kernel/` (ver [[kernelbot-architecture]]).

A arquitetura atual combina:
- backend FastAPI + Uvicorn (True Kernel HTTP)
- MySQL como fonte de dados indexados (`knowledge`)
- provider LLM configurável (Cursor SDK ou OpenRouter)
- políticas de grounding e gates de retrieval para reduzir alucinação
- API v1 multi-canal (`GET /v1/health`, `POST /v1/chat`) para integração com OrbitBot
- adapters em `adapters/` (whatsapp outbound HTTP; discord = stub `discord_not_implemented`) — não confundir com o repo OrbitBot

## Estado atual

- Branch auditada: `feature/kernel-orbit-v1-hardening`
- Stack verificada no código: FastAPI, BM25 (`rank-bm25`), MySQL, OpenRouter/Cursor, SSE opcional via `stream=true`
- Frontend público de chat: **ausente** (`frontend/` não existe)
- UI operacional: **presente** — Ops Center `/ops/*` e Traces `/traces/*` (README que nega "interface web" está desatualizado)
- Bug CURRENT: `main.py` chama `bootstrap_catalog_state` sem import (ver [[kernelbot-known-issues]])
- Infra relevante: Docker, scripts de staging, suporte a catálogo ISS e reload de índice
- Limitação principal: o sistema depende de um índice MySQL e de credenciais de provider válidas

## Mapa da wiki

- [[kernelbot-current-state]] — visão objetiva do que existe hoje
- [[kernelbot-architecture]] — arquitetura e runtime
- [[kernelbot-branches]] — análise das branches relevantes
- [[kernelbot-decisions]] — decisões arquiteturais importantes
- [[kernelbot-history]] — evolução em alto nível
- [[kernelbot-domain]] — domínio e conceitos do projeto
- [[kernelbot-conventions]] — convenções observadas
- [[kernelbot-known-issues]] — riscos, limitações e problemas conhecidos
- [[kernelbot-roadmap]] — planejamento evidenciado, sem confundir com inferência

## Páginas adicionais relevantes

- [[kernelbot-kernel]] — o núcleo (kernel) do projeto e seus módulos centrais
- [[kernelbot-identity]] — identificação do projecto KernelBot
- [[kernelbot-orbit]] — conceito Orbit / adapters e relação com Kernel
- [[kernelbot-orbitbot]] — notas sobre o OrbitBot (adapter WhatsApp)
- [[kernelbot-components]] — inventário de componentes compartilháveis
- [[kernelbot-memory]] — KB, BM25 e transcript store
- [[kernelbot-rag]] — pipeline de retrieval e políticas
- [[kernelbot-security]] — seções sobre autenticação, ACL e rate-limit
- [[kernelbot-ecosystem]] — mapa do ecossistema e repositórios relacionados
- [[kernelbot-ecosystem-history]] — histórico do ecossistema e branches relevantes

## Fontes principais preservadas

- `raw/README.md`
- `raw/docs-wiki/`
- `docs/wiki/` no repositório fonte
- histórico Git (`git branch -a`, `git log --all`)

## Leitura recomendada

1. [[kernelbot-current-state]]
2. [[kernelbot-architecture]]
3. [[kernelbot-branches]]
4. [[kernelbot-decisions]]
5. [[kernelbot-known-issues]]

> O código-fonte continua sendo a fonte de verdade para o estado atual; a wiki registra síntese, histórico e decisões.
