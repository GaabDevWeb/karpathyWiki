---
id: gaabwiki-rag
tipo: conceito
status: atual
projeto: gaabwiki
dominio: retrieval
escopo: meta
atualizado: 2026-08-23
confianca: alta
aliases:
  - Retrieval augmentation
  - Recuperação contextualizada
fontes:
  - .ai/wiki/gaabwiki-terminology.md
  - KernelBot/wiki/rag.md
  - KernelBot/index.md
  - README.md
  - .ai/CLAUDE.md
relacionados:
  - gaabwiki-memory
  - gaabwiki-kernel
  - gaabwiki-kernelbot
  - gaabwiki-security
  - gaabwiki-overview
  - gaabwiki-architecture
tags:
  - gaabwiki-rag
  - retrieval
  - knowledge
---

# RAG

> Resumo: RAG é recuperação de contexto relevante para alimentar geração ou decisão. **Dois níveis distintos** coexistem no ecossistema e não devem ser confundidos.

## Dois níveis (obrigatório distinguir)

### 1. RAG no KernelBot (implementado)

**Status: CONFIRMADO no código** (branch `feature/kernel-orbit-v1-hardening`).

- BM25 léxico (`rank-bm25`) sobre chunks MySQL
- Gates de retrieval e grounding em `kernel/rag/retrieval.py`
- Ingest via scripts e catálogo ISS
- **Não** usa embeddings nem vector DB
- Evidência: `KernelBot/wiki/rag.md`, `kernel/rag/search.py`, `requirements-prod.txt`

### 2. RAG na GaabWiki (não implementado)

**Status: preparação documental apenas.**

A meta-wiki GaabWiki preparou corpus, schema e metadata para futura indexação **sem** implementar infraestrutura de retrieval sobre si mesma:

- `corpus.yaml` define inclusões/exclusões
- `schema.md` define campos para futura busca
- **Nenhuma** vector DB, embedding ou pipeline de retrieval existe no repositório GaabWiki

## Limite conceitual

- RAG no KernelBot = runtime de produção para chat educacional
- RAG-readiness na GaabWiki = corpus humano/agente pronto para uma camada futura de indexação
- A Wiki Carpaccio **não é** RAG; é memória derivada em Markdown

## Fontes

- [KernelBot/wiki/rag.md](../../KernelBot/wiki/rag.md)
- [corpus.yaml](../../corpus.yaml)
- [.ai/CLAUDE.md](../CLAUDE.md)
