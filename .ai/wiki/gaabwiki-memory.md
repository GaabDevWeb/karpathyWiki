---
id: gaabwiki-memory
tipo: conceito
status: atual
projeto: gaabwiki
dominio: knowledge-base
escopo: meta
atualizado: 2026-08-23T14:00
confianca: alta
aliases:
  - Memory layer
  - Memória
fontes:
  - /home/gaab/Documentos/gitHub/KernelBot/kernel/memory/
  - /home/gaab/Documentos/gitHub/OrbitBot/database/
  - KernelBot/wiki/kernelbot-memory.md
  - OrbitBot/wiki/orbitbot-memory.md
relacionados:
  - gaabwiki-kernel
  - gaabwiki-kernelbot
  - gaabwiki-orbitbot
  - gaabwiki-rag
  - gaabwiki-agent
  - gaabwiki-security
tags:
  - gaabwiki-memory
  - context
  - persistence
---

# Memory

> "Memory" não é um componente único. São mecanismos distintos. Misturá-los é erro.

## Tipos confirmados no código

| # | Tipo | Onde | Persistência | Papel |
|---|------|------|--------------|-------|
| 1 | Wiki Carpaccio | GaabWiki `.ai/wiki/`, sub-wikis | Git | memória de **desenvolvimento**; não entra no chat |
| 2 | KB / índice RAG | KernelBot MySQL `knowledge` | MySQL + BM25 em RAM | conhecimento de aulas |
| 3 | Contexto institucional | `KernelBot/context/*.md`, `calendar.json` | ficheiros | identidade, regras, calendário |
| 4 | Transcript de sessão | `TranscriptStore` (KernelBot) | **in-memory** (processo) | SSOT de conversa para `POST /v1/chat` — **IMPLEMENTED / BRANCH-SPECIFIC** (`feature/kernel-orbit-v1-hardening`); **ausente** em `KernelBot/main` (sem `/v1/chat`) |
| 5 | Pin RAG | `PinnedSessionStore` | **in-memory** | disciplina/sticky |
| 6 | Idempotência | `IdempotencyStore` | in-memory + TTL | dedupe de requests |
| 7 | Group memory / profile | `GroupMemoryStore` | SQLite `data/group_memory.sqlite3` | grupos (se enabled) |
| 8 | Traces | `TraceStore` | SQLite | observabilidade, não conhecimento |
| 9 | Comms / users ops | stores Kernel | SQLite | campanhas e bloqueios |
| 10 | SQLite OrbitBot | `database/` | SQLite | clientes, historico admin, config — **não** enviado como contexto ao Kernel |
| 11 | Buffer grupo Orbit | `src/groups/groupBuffer.js` | RAM | observabilidade; pergunta limpa vai ao Kernel |
| 12 | Pasta `memory/` nos repos | KernelBot/OrbitBot | Markdown de planos | **não** é store runtime |

## O que não existe

- Cache de respostas LLM no path Kernel (planos de optimização proíbem; Orbit `core/cache.js` não está no fluxo).
- Vector store / embeddings.
- Memória de "agente" partilhada entre MegaBrain e o bot.

## Relação com RAG

- KB MySQL alimenta [[gaabwiki-rag]] (BM25).
- Transcript alimenta continuidade de conversa.
- GaabWiki **não** alimenta o runtime de chat.
