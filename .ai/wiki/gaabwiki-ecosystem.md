---
id: gaabwiki-ecosystem
tipo: ecossistema
status: atual
projeto: gaabwiki
dominio: ecosystem
escopo: meta
atualizado: 2026-08-23
confianca: alta
aliases:
  - Ecossistema da GaabWiki
  - Wiki ecosystem
fontes:
  - /home/gaab/Documentos/gitHub/OrbitBot/src/providers/kernelProvider.js
  - /home/gaab/Documentos/gitHub/OrbitBot/src/openai.js
  - /home/gaab/Documentos/gitHub/KernelBot/api/routes_v1.py
  - /home/gaab/Documentos/gitHub/KernelBot/adapters/whatsapp/outbound.py
relacionados:
  - gaabwiki-overview
  - gaabwiki-projects
  - gaabwiki-terminology
  - gaabwiki-kernelbot
  - gaabwiki-orbitbot
  - kernelbot-branches
  - orbitbot-branches
tags:
  - gaabwiki
  - ecosystem
  - gaabwiki-kernel
  - gaabwiki-orbit
  - branch-provenance
---

# GaabWiki — Ecossistema e relações transversais

## Proveniência de integração Orbit ↔ Kernel

| Estado | KernelBot | OrbitBot | Integração `/v1/chat` |
|--------|-----------|----------|------------------------|
| **`main`** | `engine/` + `frontend/`; sem `kernel/` | OpenRouter/WPPConnect legado; **sem** `kernelProvider.js` | **Ausente** |
| **`feature/kernel-orbit-v1-hardening`** | `kernel/`, `routes_v1.py` | `kernelProvider.js`, Baileys | **IMPLEMENTED** |
| **Merge feature → main** | — | — | **UNKNOWN** |
| **Produção conjunta E2E** | — | — | **UNKNOWN** |

Não tratar a feature branch como estado universal de `main`.

---

## IMPLEMENTED / BRANCH-SPECIFIC

**Repos:** KernelBot + OrbitBot  
**Branch:** `feature/kernel-orbit-v1-hardening`  
**Evidência:** checkout local + `git cat-file` (2026-08-23)

```text
WhatsApp
  → OrbitBot (Baileys, src/bot.js)
  → filtros (@orbit / menção / mutex / dedupe)
  → src/openai.js → kernelProvider.chat()
  → POST {KERNEL_API_URL}/v1/chat   (default http://127.0.0.1:8001)
  → KernelBot FastAPI (api/routes_v1.py)
  → BM25 + grounding + LLM
  → JSON { answer }
  → OrbitBot formata e envia no WhatsApp
```

Canal inverso (código presente; produção **NÃO CONFIRMADA**):

```text
KernelBot adapters/whatsapp/outbound.py
  → ORBIT_INTERNAL_URL  default http://127.0.0.1:8010
  → OrbitBot src/outbound/internalHttp.js
  → envio proactivo WhatsApp
```

Traces: OrbitBot `src/traceClient.js` → KernelBot `POST /internal/traces/events`.

---

## CURRENT-de-`main` (HISTORICAL para True Kernel)

Em **`main`**, KernelBot e OrbitBot **não** expõem o contrato Orbit→Kernel descrito acima. OrbitBot usa fluxo OpenRouter legado; KernelBot usa `engine/` + frontend web.

---

## TARGET / PLANNED

- Merge `feature/kernel-orbit-v1-hardening` → `main`: **UNKNOWN**
- Operação WhatsApp+Kernel em produção: **UNKNOWN**

---

## O que cada peça é (e não é)

| Entidade | Papel | NÃO é |
|----------|-------|-------|
| **Kernel** | Conceito cognitivo | Repositório |
| **KernelBot** | Repo que implementa Kernel (feature: `kernel/`) | O conceito Orbit |
| **Orbit** | Conceito de canal | Repositório |
| **OrbitBot** | Adapter WhatsApp (npm `orbit`) | Motor RAG |
| **GaabWiki** | Memória Markdown | Runtime |
| **AGENTS / CursorSKILLS** | Tooling dev MegaBrain | Runtime de chat |

**Não existem** repos `/Kernel` ou `/Orbit` no filesystem.

## Conceitos transversais

- **Agents / Skills:** skills Cursor, AGENTS repo — **não** runtime WhatsApp. Ver [[gaabwiki-agent]], [[gaabwiki-skill]].
- **Memory:** [[gaabwiki-memory]]
- **RAG:** BM25 no KernelBot (branch-specific); prep documental na GaabWiki — [[gaabwiki-rag]]
- **Security:** [[gaabwiki-security]]

## Relações satélite (evidência parcial)

- ISS → catálogo para KernelBot (`ACL_CATALOG_ENABLED`). Wiki ISS: [[iss-integrations]].
- KernelBot-Deploy, KernelPlanner: deploy/prompts — não SSOT da API.
- Xray-Spec, Portifolio: sem dependência runtime confirmada com Kernel/Orbit.

## Status

- Integração Orbit↔Kernel na **feature branch**: confirmada no código
- Integração em **`main`**: **ausente**
- Merge / produção: ver [[known-unknowns]]
