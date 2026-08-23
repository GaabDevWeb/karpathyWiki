---
id: kernelbot-components
tipo: components
status: atual
atualizado: 2026-08-23
fonte:
  - "raw/docs-wiki/03-estrutura-codigo.md"
  - "raw/README.md"
---

# Componentes compartilhados e reusáveis

Lista de componentes com evidência de existência e potencial de reutilização:

- `Orchestrator` (`kernel/orchestrator`)
  - Função: montar mensagens, resolver pin, montar contexto para RAG e provider
  - Reutilização: alto (pode ser extraído como biblioteca de montagem de prompts)

- `RAG` (`kernel/rag/`)
  - Função: índice BM25 por silo/discipline, retrieval policy, thresholds
  - Reutilização: alto (serviço de retrieval léxico)

- `Knowledge` / ingest pipeline (`kernel/knowledge`, `bin/ingest-jsons.sh`)
  - Função: ingest de catálogo ISS → estrutura de tabelas MySQL + chunks
  - Reutilização: moderado (scripts de ingest e normalização)

- `Providers` (`kernel/providers`)
  - Função: abstrair LLMs (Cursor SDK, OpenRouter)
  - Reutilização: alto (plugin para LLMs)

- `Memory` (`kernel/memory`, `PinnedSessionStore`, `TranscriptStore`)
  - Função: pin por sessão e transcript in-process
  - Reutilização: condicional (dependente de estratégia de persistência)

- `Trace` (`kernel/trace`, `traces.sqlite3`)
  - Função: observabilidade e auditoria operacional
  - Reutilização: operacional, não core

- `Policies` (`kernel/policies`, system prompts)
  - Função: grounding, post-generation validators
  - Reutilização: elevado (roteiros de prompt & rules)

Observação sobre acoplamento

- Alguns componentes (ex.: Baileys/Orbit) pertencem a outro runtime (Node.js) — migração direta não é trivial.`
