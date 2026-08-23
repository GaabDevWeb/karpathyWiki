---
id: kernelbot-ecosystem
tipo: ecosystem
status: atual
atualizado: 2026-08-23
---

# Ecossistema — mapa de alto nível

Visão resumida

Este projecto (KernelBot / Kernel) faz parte de um ecossistema formado por:

- Kernel (núcleo Python/FastAPI)
- Orbit / OrbitBot (adapters WhatsApp, Baileys — Node.js)
- Consumidores e integrações (Discord, CLI, outros adapters)
- Repositórios auxiliares e histórico (branches com feature/orbit-*, trueKernel, kernel-observability)

Relações confirmadas

- Orbit depende do Kernel para RAG e geração (via HTTP `/v1/chat`) — `docs/prd/2026-07-28-kernel-orbit-integration.md`.
- Kernel provê interfaces, políticas e armazenamento de conhecimento; adapters consomem.

Componentes compartilhados

- BM25 index (MySQL) e ingest scripts
- Policies / system prompts
- Trace/Audit store

Histórico curto

- Branches relevantes: `feature/kernel-orbit-integration`, `feature/orbit-kernel-tracing`, `trueKernel` e várias `feat/*` voltadas a providers e history.
- PRD e auditoria datam de 2026-07-24..29 (PRD + AUDIT) com decisões sobre unificação e deploy.

Notas de classificação

- Depende diretamente de: MySQL, LLM provider (Cursor/OpenRouter)
- Depende indiretamente de: Orbit (para transporte se unificado)
- Compartilha componente com: projetos que adotarem `kernel/orchestrator` e `kernel/rag`

Fontes principais

- `raw/docs-wiki/02-arquitetura.md`
- `docs/prd/2026-07-28-kernel-orbit-integration.md`
- `memory/orbit-kernel-unification/AUDIT.md`

fonte:
	- "raw/docs-wiki/02-arquitetura.md"
	- "raw/related/OrbitBot-README.md"
	- "raw/related/KernelBot-Deploy-README.md"
	- "raw/related/KernelBot.wiki/Visao-geral.md"
## Repositórios relacionados (detectados no mesmo diretório)

- `OrbitBot` — adapter WhatsApp em Node.js (Baileys). Fonte: `/home/gaab/Documentos/gitHub/OrbitBot` (README preservado em `raw/related/OrbitBot-README.md`).
- `KernelBot-Deploy` — repositório de deploy auxiliar (possível infraestrutura compartida).
- `KernelBot.wiki` — wiki histórica/ancoragem do projeto (a analisar se necessário).

## Evidências preservadas

- `raw/related/OrbitBot-README.md` — copia do README do repositório `OrbitBot` (Node.js / Baileys).
- `raw/related/OrbitBot-docs/2026-07-26-refactor-baileys.md` — PRD preservado (resumo do PRD de refactor Baileys).
- `raw/related/KernelBot-Deploy-README.md` — resumo do repositório `KernelBot-Deploy` (deploy, docker, env examples).
- `raw/related/KernelBot.wiki/Visao-geral.md` — snapshot da wiki histórica do projeto.

Observação: apenas `OrbitBot` foi automaticamente confirmada como projeto adapter com evidência direta; demais repositórios requerem investigação adicional para confirmar dependências.