---
id: kernelbot-memory
tipo: memory
status: atual
atualizado: 2026-08-23
fonte:
	- "memory/kb-trimestre3/REPORT.md"
	- "raw/docs-wiki/05-bm25-chunking.md"
---

# Memória e KB

Visão geral

O projeto usa múltiplos mecanismos de memória/knowledge:

1. KB indexada (MySQL) — tabela `knowledge` contendo chunks e metadados por disciplina/silo.
2. Retrieval léxico (BM25) — `rank-bm25` como mecanismo principal de busca.
3. Session pin / Transcript in-process — `PinnedSessionStore` e `TranscriptStore` mantêm contexto efémero por sessão (configurável por env vars).
4. Artefatos persistentes de auditoria/tracing (SQLite `traces.sqlite3`).

Evidências

- `requirements-prod.txt` menciona `rank-bm25`.
- `memory/kb-trimestre3/REPORT.md` documenta ingest, contagens e rebuild BM25.
- `kernel/memory` contém stores e código para pin/transcript.

Classificação

- Persistente: KB MySQL + traces SQLite
- Semi-persistente: ingest scripts e jsons em `jsons/` e `content/`
- Efémera: in-process transcript/pin (não adequado para múltiplos workers sem adaptação)

Recomendações rápidas

- Se for necessário escalonar, migrar transcript/pin para uma store durável (Redis/SQL) e coordenar rebuild BM25 via orchestration.
