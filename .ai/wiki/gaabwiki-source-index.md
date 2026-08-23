---
id: gaabwiki-source-index
tipo: fonte
status: atual
projeto: gaabwiki
dominio: knowledge-sources
escopo: meta
atualizado: 2026-08-23
confianca: alta
aliases:
  - Índice de fontes da GaabWiki
  - Source index
fontes:
  - /home/gaab/Documentos/gitHub/KernelBot/README.md
  - /home/gaab/Documentos/gitHub/OrbitBot/README.md
  - schema.md
  - .ai/CLAUDE.md
relacionados:
  - gaabwiki-overview
  - gaabwiki-architecture
  - gaabwiki-decisions
tags:
  - gaabwiki
  - sources
  - provenance
---

# Índice de fontes da GaabWiki

Uma página da wiki **não** é fonte primária de outra página da wiki. Fontes primárias = código, config, testes, git, README dos repos de origem.

## Fontes primárias (código)

| Fonte | Path | Uso |
|-------|------|-----|
| KernelBot código | `/home/gaab/Documentos/gitHub/KernelBot/` | estado CURRENT do Kernel |
| OrbitBot código | `/home/gaab/Documentos/gitHub/OrbitBot/` | estado CURRENT do canal |
| ISS código | `/home/gaab/Documentos/gitHub/ISS/` | conteúdo / catálogo |
| Portifolio código | `/home/gaab/Documentos/gitHub/Portifolio/` | produto visual |
| Xray-Spec código | `/home/gaab/Documentos/gitHub/Xray-Spec/` | qualidade de specs |
| AGENTS / CursorSKILLS | siblings | tooling MegaBrain |

## Fontes documentais dos repos (tratar como possivelmente stale)

- KernelBot `README.md` — omite Ops UI; afirma "sem interface web".
- OrbitBot `README.md` — descreve OpenRouter como fluxo principal (**conflito** com código).
- `KernelBot/raw/docs-wiki/` nesta GaabWiki — snapshot histórico; cita `engine/`.
- `OrbitBot/raw/*.md` — snapshots; podem divergir da branch actual.

## Fontes da própria GaabWiki (meta, não verdade de produto)

- `.ai/CLAUDE.md`, `schema.md`, `corpus.yaml`, `.ai/log.md`, `.agent_history.md`.

## Observação

Citar uma página `.ai/wiki/*` como única fonte de outra página `.ai/wiki/*` é circular. Preferir o path do repo de origem.
