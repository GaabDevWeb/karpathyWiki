---
id: kernelbot-rag
tipo: rag
status: atual
atualizado: 2026-08-23
fonte:
	- "raw/docs-wiki/05-bm25-chunking.md"
	- "raw/README.md"
---

# RAG — Retrieval-Augmented Generation do Kernel

Resumo

O Kernel usa uma estratégia RAG léxica centrada em BM25 (rank-bm25) sobre chunks derivados do catálogo ISS e de conteúdos de curso. A decisão de retrieval aplica gates e thresholds antes de enviar trechos para o LLM.

Componentes

- Indexador / ingest: scripts `bin/ingest-jsons.sh` que atualizam JSONs e acionam rebuild do índice.
- SearchEngine: `kernel/rag/search.py` — execução de BM25 por silo/discipline.
- Policies: `kernel/policies` define grounding, prompts e validações pós-geração.

Evidência

- `README.md` e `raw/docs-wiki/05-bm25-chunking.md` documentam BM25 como a estratégia de RAG.
- `memory/kb-trimestre3/REPORT.md` descreve contagens e processo de rebuild.

Observações

- Abordagem léxica intencional: preferir evidência e previsibilidade em vez de embeddings semânticos.
- Possui trade-offs: sinônimos e parafraseamentos podem não recuperar trechos relevantes sem enriquecimento léxico.
