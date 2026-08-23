---
id: kernelbot-kernel
tipo: kernel
status: atual
atualizado: 2026-08-23
fonte:
	- "raw/docs-wiki/02-arquitetura.md"
	- "raw/README.md"
---

# Kernel — Núcleo do ecossistema

Resumo executivo:

O `Kernel` (nome operacional do projeto também referido como `KernelBot`) é o núcleo Python/FastAPI que fornece:

- Orquestração de chat e montagem de contexto (`kernel/orchestrator`)
- RAG léxico baseado em BM25 (`kernel/rag/search.py`, `kernel/rag/retrieval.py`)
- Armazenamento de conhecimento indexado em MySQL (`kernel/knowledge`, tabela `knowledge`)
- Memory / transcript in-process (`kernel/memory`)
- Providers LLM configuráveis (Cursor SDK / OpenRouter em `kernel/providers`)
- Políticas de grounding e post-generation (`kernel/policies`)
- Ferramentas operacionais (`kernel/tools`) e trace emit (`kernel/trace`)

Evidências:

- `docs/ARCHITECTURE.md` / `raw/docs-wiki/02-arquitetura.md` descreve os módulos e fronteiras (Kernel vs Adapters).
- Código-fonte: pasta `kernel/` contém `orchestrator`, `rag`, `memory`, `knowledge`, `providers`.
- `README.md` descreve stack (FastAPI, BM25, MySQL) e scripts de deploy/ingest.

Status arquitetural:

- Implementado como monólito Python/FastAPI; componentes desenhados para serem reutilizáveis internamente.
- `Kernel` é a "fonte de verdade" para RAG, políticas e decisões de grounding — a wiki assume código > docs em caso de conflito.

Relação com Orbit (resumo):

- Orbit opera como adapters/clients fora do Kernel; o Kernel expõe endpoints HTTP versionados (`/v1/chat`) para integração (veja `docs/prd/2026-07-28-kernel-orbit-integration.md`).

Referências (fontes preservadas):

- `raw/README.md`
- `raw/docs-wiki/02-arquitetura.md`
- código: `kernel/` (orchestrator, rag, memory, providers)