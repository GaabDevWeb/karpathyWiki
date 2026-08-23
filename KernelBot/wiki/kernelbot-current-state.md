---
id: kernelbot-current-state
tipo: current-state
status: atual
atualizado: 2026-08-23
fonte:
  - "/home/gaab/Documentos/gitHub/KernelBot/main.py"
  - "/home/gaab/Documentos/gitHub/KernelBot/app/factory.py"
  - "/home/gaab/Documentos/gitHub/KernelBot/README.md"
---

# Estado atual do KernelBot

Branch auditada: `feature/kernel-orbit-v1-hardening` (2026-08-23).  
Repo: `/home/gaab/Documentos/gitHub/KernelBot`. `main` remota **não** foi tomada como oficial.

## O que está implementado

- backend FastAPI em `main.py` e `app/factory.py` (porta 8001)
- RAG léxico BM25 (`kernel/rag/search.py`) sobre MySQL `knowledge`
- LLM via OpenRouter ou Cursor SDK (`kernel/providers/chat_provider.py`)
- API legada `POST /chat`, `POST /search`
- API v1 `GET /v1/health`, `POST /v1/chat` (contrato Orbit)
- streaming SSE opcional (`stream: true`); Orbit usa `stream: false`
- catálogo ISS (`kernel/knowledge/catalog_sync.py`) quando enabled
- Ops Center `/ops/*` e Traces `/traces/*` (Jinja) — UI **operacional interna**
- adapters: WhatsApp outbound HTTP para Orbit; Discord = stub
- **sem** frontend público de chat (`frontend/` ausente)

## O que o README diz e o código não confirma

- README: "Não inclui interface web" — **falso** para `/ops` e `/traces`.
- README: produto pronto para publicação pública — **em tensão** com o bug de boot abaixo e testes que importam `engine.*`.

## Bug confirmado (código não alterado)

`main.py` linha ~42 chama `bootstrap_catalog_state(settings)` sem import. Definição em `kernel/knowledge/catalog_sync.py`. `build_services()` deve falhar com `NameError`.

## Fluxo principal

1. `create_app()` monta routers (legado, v1, ops, traces, internal, knowledge, comms, users, lab, adapters, settings).
2. `/v1/chat` → `ContextManager` + BM25 + gates + `ChatProvider`.
3. Transcript/pin in-memory; group memory SQLite se enabled.

## Conclusão

Backend cognitivo educacional **com** retrieval real (BM25) e **com** UI ops. Não é plataforma genérica. Não confundir com a GaabWiki (que não tem RAG runtime).
