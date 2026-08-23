---
id: kernelbot-kernel
tipo: conceito
status: atual
projeto: kernelbot
dominio: architecture
escopo: projeto
atualizado: 2026-08-23
confianca: alta
fontes:
  - /home/gaab/Documentos/gitHub/KernelBot/kernel/
  - KernelBot/wiki/kernelbot-branches.md
  - raw/docs-wiki/02-arquitetura.md
relacionados:
  - kernelbot-identity
  - kernelbot-architecture
  - kernelbot-branches
tags:
  - kernel
  - concept
  - branch-provenance
---

# Kernel (conceito) vs KernelBot (projeto)

## Kernel ≠ KernelBot

| | **Kernel** | **KernelBot** |
|---|------------|---------------|
| Natureza | Conceito / camada arquitectural | Repositório / projecto |
| Onde vive | Namespace `kernel/` **dentro** do repo KernelBot (feature branch) | `/home/gaab/Documentos/gitHub/KernelBot` |
| Papel | Cognição: RAG, grounding, LLM, transcript | Hospeda código, deploy, API HTTP, adapters |

**Proibido confundir:** KernelBot **não** é sinónimo de Kernel. KernelBot **implementa** o Kernel.

## Implementação do Kernel (BRANCH-SPECIFIC)

**Repo:** KernelBot  
**Branch:** `feature/kernel-orbit-v1-hardening`  
**Classificação:** IMPLEMENTED — **não** assumir em `main`

Módulos sob `kernel/` (evidência HEAD 2026-08-23):

- `kernel/orchestrator` — montagem de contexto
- `kernel/rag/search.py`, `kernel/rag/retrieval.py` — BM25 + gates
- `kernel/knowledge/` — MySQL `knowledge`
- `kernel/memory/` — transcript, pin, group (in-process / SQLite parcial)
- `kernel/providers/` — OpenRouter / Cursor SDK
- `kernel/policies/`, `kernel/trace/`, `kernel/tools/`

## O que NÃO é Kernel (fronteiras)

- **OrbitBot** — canal WhatsApp; chama o Kernel via HTTP.
- **GaabWiki** — memória documental; sem runtime.
- **`adapters/`** na raiz do repo — outbound WhatsApp/Discord; **não** está sob `kernel/adapters/` (path `kernel/adapters/` **não existe**).

## Em `main` (HISTORICAL / legado)

- Domínio cognitivo legado em `engine/` + UI em `frontend/`.
- **Sem** pacote `kernel/` nem contrato `/v1/chat`.
- Ver [[kernelbot-branches]].

## Relação com Orbit

Orbit (OrbitBot) delega geração via `POST /v1/chat` na feature branch. Kernel expõe HTTP; Orbit não importa código Python.

## Fontes

- Código: `kernel/` (feature branch)
- Proveniência: [[kernelbot-branches]]
- Histórico: `raw/docs-wiki/` (cita `engine/` — imutável)
