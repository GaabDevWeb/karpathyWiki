---
id: kernelbot-identity
tipo: projeto
status: atual
projeto: kernelbot
dominio: identity
escopo: projeto
atualizado: 2026-08-23
confianca: alta
fontes:
  - raw/README.md
  - KernelBot/wiki/kernelbot-branches.md
relacionados:
  - kernelbot-kernel
  - kernelbot-current-state
tags:
  - kernelbot
  - identity
---

# KernelBot — o projecto (repositório)

## KernelBot ≠ Kernel

| | KernelBot | Kernel |
|---|-----------|--------|
| Tipo | Repositório / projecto | Conceito / camada arquitectural |
| Path | `/home/gaab/Documentos/gitHub/KernelBot` | Namespace `kernel/` **dentro** do KernelBot (feature branch) |

KernelBot **implementa** o Kernel. Não são nomes intercambiáveis. Ver [[kernelbot-kernel]].

## Propósito

- Serviço HTTP para chat e search sobre conteúdo educacional indexado.
- BM25 → chunks → grounding → LLM.
- Backend consumível por adapters (OrbitBot, Discord stub, CLI).

## Branch auditada

`feature/kernel-orbit-v1-hardening` (2026-08-23). **`main`** tem arquitectura legada — [[kernelbot-branches]].

## O que implementa (feature branch)

- `POST /v1/chat`, `GET /v1/health` — contrato Orbit
- `POST /chat`, `POST /search` — legado
- RAG BM25 em `kernel/rag/`
- Ops `/ops/*`, Traces `/traces/*`

## Naming histórico (HISTORICAL)

README e docs antigos usam "Kernel API" como branding do produto — isso refere-se ao **conceito** servido pelo **repo** KernelBot, não prova que Kernel = KernelBot como entidades.

## Fontes

- `raw/README.md`
- [[kernelbot-branches]]
