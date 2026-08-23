---
id: gaabwiki-health
tipo: problema
status: atual
projeto: gaabwiki
dominio: governance
escopo: meta
atualizado: 2026-08-23
confianca: alta
aliases:
  - Health check da wiki
  - Status da base
fontes:
  - .ai/CLAUDE.md
  - schema.md
  - corpus.yaml
  - .ai/wiki/known-unknowns.md
relacionados:
  - gaabwiki-overview
  - gaabwiki-auditoria
  - known-unknowns
  - gaabwiki-index
tags:
  - health
  - governance
  - quality
---

# Health da GaabWiki

> Pós segunda passagem forense (2026-08-23). Honestidade > "estável" cosmética.

## Checklist

| Critério | Status | Notas |
|----------|--------|-------|
| Path workspace | ✅ | `/home/gaab/Documentos/gitHub` |
| Meta-wiki vs código Kernel/Orbit | ✅ | reconciliada nesta passagem |
| Distinção Kernel vs KernelBot | ✅ | |
| Distinção RAG Kernel vs RAG-wiki | ✅ | |
| Agent/Skill sem runtime inventado | ✅ | corrigido |
| Security sem overclaim | ✅ | três planos |
| README Orbit documentado como stale | ✅ | |
| Ops UI Kernel documentada | ✅ | |
| Bug `bootstrap_catalog_state` visível | ✅ | |
| IDs meta-wiki | ✅ | |
| Frontmatter sub-wikis (`id`) | ⚠️ | incompleto |
| `tipo: documento` | ✅ | substituído por `problema` em health/known-unknowns |
| Wikis ISS/Portifolio/Xray vs HEAD | ⚠️ | não re-auditadas agora |
| Repos satélites | ⚠️ | inventário só |
| Duplicata Portifolio `wiki/` vs `.ai/wiki/` | ⚠️ | conhecida |
| Contradições abertas | ⚠️ | ver [[known-unknowns]] |

## Status final

**HEALTH: USÁVEL COM RESSALVAS — freeze V1 não declarado**

Memória humana/agente válida para Kernel↔Orbit, desde que [[known-unknowns]] permaneça visível e o código continue a vencer. Validação de freeze é responsabilidade de gate externo.
