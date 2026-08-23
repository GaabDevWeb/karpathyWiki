---
id: kernelbot-architecture
tipo: arquitetura
status: atual
projeto: kernelbot
dominio: architecture
escopo: projeto
atualizado: 2026-08-23
confianca: alta
fontes:
  - /home/gaab/Documentos/gitHub/KernelBot/app/factory.py
  - /home/gaab/Documentos/gitHub/KernelBot/api/routes_v1.py
  - /home/gaab/Documentos/gitHub/KernelBot/adapters/whatsapp/outbound.py
relacionados:
  - kernelbot-branches
  - kernelbot-current-state
tags:
  - architecture
  - branch-provenance
---

# Arquitetura do KernelBot

**Branch auditada:** `feature/kernel-orbit-v1-hardening` (BRANCH-SPECIFIC).  
**`main`:** arquitectura diferente (`engine/` + `frontend/`) — ver [[kernelbot-branches]].

Pacote legado `engine/` → `kernel/` na feature. `raw/docs-wiki/` ainda cita `engine/` (HISTORICAL).

```text
OrbitBot / cliente HTTP
  -> POST /v1/chat  (ou POST /chat legado)
  -> api/routes_v1.py / api/routes.py
  -> ContextManager (kernel/orchestrator)
  -> SearchEngine BM25 (kernel/rag)
  -> MySQL knowledge
  -> retrieval.py (gates)
  -> ChatProvider
  -> JSON (Orbit) ou SSE (opcional)
```

UI interna (não é o chat público):

```text
/ops/*   Ops Center (api/ops_routes.py, templates/ops)
/traces/*  flight recorder (api/traces_routes.py)
```

Outbound (path **real** verificado no repo):

```text
adapters/whatsapp/outbound.py -> ORBIT_INTERNAL_URL default http://127.0.0.1:8010
adapters/discord/outbound.py -> stub discord_not_implemented
```

**Nota:** `kernel/adapters/` **não existe** no filesystem.

## Módulos

- `main.py` / `app/factory.py` — composition root
- `api/routes.py`, `api/routes_v1.py`, `api/chat_pipeline.py`
- `kernel/config.py` — settings
- `kernel/knowledge/database.py`, `catalog_sync.py`
- `kernel/rag/search.py`, `retrieval.py`
- `kernel/orchestrator/context.py`
- `kernel/providers/chat_provider.py`
- `kernel/memory/` — transcript, pin, group, idempotency
- `kernel/trace/`, `kernel/comms/`, `kernel/users/`

## Trade-offs

- BM25 previsível, fraco em sinónimos.
- Transcript in-process: não é multi-worker.
- Ops UI aumenta superfície; README ainda a nega.
