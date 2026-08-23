---
id: gaabwiki-kernel
tipo: conceito
status: atual
projeto: gaabwiki
dominio: architecture
escopo: meta
atualizado: 2026-08-23
confianca: alta
aliases:
  - Kernel layer
  - Camada cognitiva
  - Kernel API
fontes:
  - /home/gaab/Documentos/gitHub/KernelBot
  - KernelBot/wiki/kernelbot-branches.md
  - KernelBot/wiki/kernelbot-kernel.md
relacionados:
  - gaabwiki-kernelbot
  - gaabwiki-orbit
  - gaabwiki-rag
  - gaabwiki-memory
  - gaabwiki-security
tags:
  - gaabwiki-kernel
  - architecture
  - context
  - branch-provenance
---

# Kernel

> **Kernel** = conceito/camada arquitectural de cognição (contexto, RAG, grounding, LLM). **Kernel ≠ KernelBot.** KernelBot é o repositório que **implementa** essa camada. Não existe repo `/home/gaab/Documentos/gitHub/Kernel`.

## Proveniência (leia primeiro)

| Classificação | Repo | Branch | O que significa |
|---------------|------|--------|-----------------|
| **IMPLEMENTED / BRANCH-SPECIFIC** | KernelBot | `feature/kernel-orbit-v1-hardening` | Pacote `kernel/`, `/v1/chat`, True Kernel HTTP |
| **CURRENT-de-`main`** | KernelBot | `main` | Monólito `engine/` + `frontend/`; **sem** `kernel/` |
| **TARGET** | KernelBot | merge feature → `main` | **UNKNOWN** — não confirmado |
| **HISTORICAL** | KernelBot | `raw/docs-wiki/` | Documentação legada que cita `engine/` |

Evidência Git (2026-08-23): `git cat-file -e main:kernel/rag/search.py` → ausente; HEAD da feature → presente.

## Definição (conceito)

O Kernel agrupa responsabilidades cognitivas: orchestrator, RAG, memory, knowledge, providers, policies, trace. No código **da feature branch**, vivem sob `kernel/` dentro do repo KernelBot.

## O que existe em `KernelBot/main`

**Classificação:** CURRENT-de-`main` / HISTORICAL relativamente ao True Kernel documentado na wiki meta.

| Artefacto | Em `main`? |
|-----------|------------|
| Pacote `kernel/` | **Não** |
| `api/routes_v1.py`, `POST /v1/chat` | **Não** |
| Pacote `engine/` | **Sim** (~13 paths) |
| `frontend/` (UI web pública) | **Sim** |
| BM25 via `kernel/rag/` | **Não** (legado sob `engine/`) |

## O que existe em `KernelBot/feature/kernel-orbit-v1-hardening`

**Classificação:** IMPLEMENTED / BRANCH-SPECIFIC (workspace auditado 2026-08-23).

| Artefacto | Na feature? |
|-----------|-------------|
| Pacote `kernel/` | **Sim** |
| `POST /v1/chat` | **Sim** (`api/routes_v1.py`) |
| `engine/` | **Não** (substituído) |
| `frontend/` | **Não** (ausente no HEAD) |
| `adapters/whatsapp/outbound.py` | **Sim** (path real: `adapters/`, não `kernel/adapters/`) |

Pastas `engine/` e `core/` **vazias no HEAD da feature** — afirmação **falsa** em `main`, onde `engine/` está populado.

## Relação com Orbit

Orbit (conceito; OrbitBot = implementação) é o **canal**. Kernel **processa**. Contrato Orbit→Kernel na feature: `POST /v1/chat` (HTTP). **Não** existe em `main` de OrbitBot (`kernelProvider.js` ausente).

## Relação com projectos

- [[gaabwiki-kernelbot]]: repositório que hospeda a implementação.
- [[gaabwiki-orbitbot]]: adapter WhatsApp que consome `/v1/chat` na feature branch.
- [[kernelbot-branches]]: tabela completa main vs feature.
