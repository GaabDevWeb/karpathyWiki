---
id: gaabwiki-kernelbot
tipo: conceito
status: atual
projeto: gaabwiki
dominio: project-definition
escopo: meta
atualizado: 2026-08-23
confianca: alta
aliases:
  - KernelBot
  - Kernel Bot
  - Kernel API
fontes:
  - /home/gaab/Documentos/gitHub/KernelBot/main.py
  - /home/gaab/Documentos/gitHub/KernelBot/app/factory.py
  - /home/gaab/Documentos/gitHub/KernelBot/api/routes_v1.py
  - /home/gaab/Documentos/gitHub/KernelBot/README.md
  - KernelBot/index.md
relacionados:
  - gaabwiki-kernel
  - gaabwiki-orbitbot
  - gaabwiki-memory
  - gaabwiki-rag
  - gaabwiki-security
tags:
  - gaabwiki-kernelbot
  - project
  - core
---

# KernelBot

> Backend cognitivo educacional: FastAPI + BM25 + LLM. Repo: `/home/gaab/Documentos/gitHub/KernelBot`.

## Estado atual (auditado 2026-08-23)

| Aspecto | Evidência |
|---------|-----------|
| Branch auditada | `feature/kernel-orbit-v1-hardening` |
| `main` remota | existe; **não** foi tratada como estado oficial nesta auditoria |
| Stack | Python 3.11+/3.12, FastAPI, Uvicorn, MySQL, `rank-bm25`, OpenRouter ou Cursor SDK |
| Porta | 8001 (`main.py`) |
| API v1 | `GET /v1/health`, `POST /v1/chat`, grupos |
| API legada | `POST /chat`, `POST /search` |
| RAG | BM25 léxico — **implementado**; sem embeddings / vector DB |
| Memória | transcript/pin/idempotency **in-memory**; group memory SQLite |
| Frontend público de chat | **ausente** (`frontend/` não existe nesta branch) |
| UI operacional | **presente**: Ops Center `/ops/*` e Traces `/traces/*` (Jinja) — contradiz o README ("Não inclui interface web") |
| Discord adapter | stub (`discord_not_implemented`) |
| WhatsApp outbound | cliente HTTP para Orbit (`ORBIT_INTERNAL_URL`) |
| CI | `.github/workflows/ci.yml` em push `main`/`master` e PRs — **não** cobre a feature branch por push |
| Testes | 42 ficheiros `test_*.py`; alguns ainda importam `engine.*` / `core.*` (pastas vazias) |

## Bug confirmado no código (não corrigido — regra: wiki não altera código)

`main.py` chama `bootstrap_catalog_state(settings)` **sem import**. A função existe em `kernel/knowledge/catalog_sync.py`. Boot via `build_services()` deve levantar `NameError`.

## Relação com OrbitBot

```text
OrbitBot → POST /v1/chat → KernelBot
KernelBot → BM25 + grounding + LLM → { answer }
KernelBot → (opcional) ORBIT_INTERNAL_URL → outbound WhatsApp
```

OrbitBot não duplica RAG.

## Temporalidade

- **CURRENT:** `kernel/`, `/v1/chat`, BM25, Ops/Traces.
- **HISTORICAL:** pacote `engine/`/`core/` (vazio); frontend público; docs em `raw/docs-wiki/` que ainda citam `engine/`.
- **EXPERIMENTAL / NÃO CONFIRMADO:** unificação Orbit→Kernel num só repo (planos em `memory/` do KernelBot); Discord activo.

## Fontes

- Código: `/home/gaab/Documentos/gitHub/KernelBot/`
- Wiki derivada: [KernelBot/index.md](../../KernelBot/index.md)
