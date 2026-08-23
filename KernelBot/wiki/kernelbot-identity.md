---
id: kernelbot-identity
tipo: project
status: atual
atualizado: 2026-08-23
fonte:
	- "raw/README.md"
	- "raw/docs-wiki/KernelBot.md"
---

# KernelBot — O projecto (nome histórico e identidade)

O que é

KernelBot é a instância operacional do `Kernel` — um backend Python/FastAPI que oferece chat RAG orientado a conteúdo educacional indexado (aulas). Historicamente também referido como "Kernel" e sujeito a movimentos de renome e refactor (ver branches e PRD).

Propósito

- Fornecer um serviço HTTP canónico para chat e search sobre conteúdos educacionais.
- Ancorar respostas em evidência (BM25 → chunks → grounding) para reduzir alucinação.
- Servir como backend consumível por adapters (Orbit, Discord, CLI).

O que implementa hoje (evidência)

- Endpoints HTTP verificados: `POST /chat` (legado), `POST /search`, `GET /v1/health`, `POST /v1/chat` (contrato Orbit), endpoints de grupo em `api/routes_v1.py`.
- RAG: BM25 + MySQL (`kernel/rag/search.py`, `kernel/knowledge/database.py`).
- Ingest pipeline: `./bin/ingest-jsons.sh`, sincronização com catálogo ISS e rebuild BM25.
- Providers LLM configuráveis: Cursor SDK ou OpenRouter.
- Rate limiting e ACL para operações sensíveis (`/reload`, `/health/catalog`).

Reutilização e componentes potencialmente reaproveitáveis

- `kernel/orchestrator` (montagem de mensagens) — utilidade alta para outros projetos
- `kernel/rag` (BM25) — pode ser isolado como serviço de retrieval léxico
- `kernel/providers` (abstração de LLM) — adaptador pluggable para diferentes SDKs

Fontes

- `raw/README.md`
- `raw/docs-wiki/02-arquitetura.md`
- `memory/kb-trimestre3/REPORT.md`