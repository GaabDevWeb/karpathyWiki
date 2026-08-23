---
id: kernelbot-ecosystem-history
tipo: history
status: atual
atualizado: 2026-08-23
---

# História do ecossistema — pontos relevantes

Síntese temporal (resumo curto)

- 2024..2025: protótipos iniciais e ingest de conteúdo educativo (KB, scripts de ingest)
- 2026-07: esforço de consolidação e PRDs para unificação Kernel ↔ Orbit (PRD 2026-07-28)
- 2026-07-29: auditoria sobre a migração de OrbitBot → adapter interno (AUDIT.md)
- 2026-08-xx: branches de hardening, observability e integração (`feature/kernel-orbit-integration`, `feature/orbit-kernel-tracing`)

Branches e marcos

- `feature/kernel-orbit-integration`: introdução do contrato `/v1/chat` e schemas canal-agnósticos
- `feature/orbit-kernel-tracing`: tracing/observability para unificação
- `trueKernel` / `kernel-observability-*`: experiências experimentais e auditoria de monitorização

Decisões históricas

- Escolha por BM25 (léxico) como motor de retrieval (trade-off entre precisão e simplicidade operacional)
- Mantê-lo como monólito Python/FastAPI, evitando filas/Redis inicialmente
- Design de adapters finos (Orbit) que delegam contexto e RAG ao Kernel (ADR-0002 / PRD)

Fontes e evidências

- `docs/prd/2026-07-28-kernel-orbit-integration.md`
- `memory/orbit-kernel-unification/AUDIT.md`
- histórico de branches (`git branch -a`)

fonte:
	- "raw/docs-wiki/02-arquitetura.md"
	- "memory/orbit-kernel-unification/AUDIT.md"
	- "raw/related/OrbitBot-docs/2026-07-26-refactor-baileys.md"
