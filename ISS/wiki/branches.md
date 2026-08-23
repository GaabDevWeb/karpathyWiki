---
tipo: branch
status: atual
atualizado: 2026-08-22
relacionado:
  - "[[history]]"
  - "[[decisions]]"
  - "[[integrations]]"
---

# Branches

Análise read-only em 2026-08-22. Estado actual do produto = **`main`**.

## Inventário

| Branch | Tipo | Tip (commit) | Data tip |
|--------|------|--------------|----------|
| `main` / `origin/main` | canónica | `778166e` | 2026-06-22 |
| `features` / `origin/features` | feature / integração | `b432a6f` | 2026-05-22 |
| `origin/cursor/pipeline-iss-conte-do-153f` | Cursor Agent (conteúdo) | `9b54240` | 2026-05-15 |
| `origin/cursor/pipeline-iss-conte-do-494f` | Cursor Agent (conteúdo) | `bf1a932` | 2026-05-17 |
| `origin/cursor/pipeline-iss-conte-do-7363` | Cursor Agent (conteúdo) | `b84f4cd` | 2026-05-14 |
| `origin/cursor/pipeline-iss-conte-do-f5b2` | Cursor Agent (conteúdo) | `717250b` | 2026-05-16 |

Locais: `main`, `features`. Remotas: as acima + `origin/HEAD → origin/main`.

## `main` — estado actual

- Site + `content/` + pipeline `summarize-transcripts.yml`
- Contém commits posteriores a `features` (≈20 commits à frente do merge-base `1d69de6`)
- Continua a receber lições automáticas e conteúdo manual

## `features` — KernelBot sync (não merged em `main`)

**Propósito:** sincronizar catálogo ISS → MySQL KernelBot + reload BM25 + verificação.

**Commits exclusivos (3):**

1. `d67107f` — `.gitignore` de reports; rename/docs
2. `b80775d` — ingest **Opção B2** unificado + `MAX_CONTENT` pré-UPSERT
3. `b432a6f` — melhorias Discord notify

**Artefactos exclusivos (exemplos):**

- `.github/workflows/sync-kernelbot-knowledge.yml`
- `.github/scripts/ingest-knowledge.py`, `validate-catalog.mjs`, `reload-kernelbot.mjs`, `verify-kernelbot-sync.mjs`, `ops-notify.sh`
- `agent.md`, `.agent_history.md`, `Documentation.md` (com secção Fase 5b)

**Estado:** divergente; **não** está na árvore de workflows de `main`. Relatórios JSON semelhantes existem em `main` (adicionados em `83e1c8b`) **sem** o workflow — possível leftover / cópia parcial; tratar como inconsistência ([[known-issues]]).

## Branches `origin/cursor/pipeline-iss-conte-do-*`

**Propósito:** PRs/agentes Cursor a publicar aulas a partir de VTT e introduzir `agents/discipline-map.yaml`.

| Branch | Conteúdo típico exclusivo |
|--------|---------------------------|
| `…-7363` | Aulas Python dados 9–10, SQL 7; discipline-map; updates lessons/search-index |
| `…-153f` | SQL aulas 7–8; discipline-map |
| `…-f5b2` | Fluência IA aula 4; discipline-map |
| `…-494f` | Projeto-bloco aula 14 + mapeamento |

**Estado aparente:** historicamente abandonadas relativamente a `main` (tips antigas; trabalho de conteúdo provavelmente absorvido por commits em `main` / bot). O ficheiro `discipline-map.yaml` **não** permanece em `main` — substituído operacionalmente por `config/vtt-to-content.json`.

## Diagrama conceptual

```text
main (canónica — site + pipeline VTT)
 │
 ├─ features ─── sync KernelBot / MySQL / B2 (não integrado)
 │
 └─ cursor/pipeline-iss-conte-do-* ─── publicações pontuais + discipline-map.yaml
         (histórico; tips atrás de main)
```

## O que não fazer

- Não assumir que `features` é “melhor” ou “pior” — documenta integração **outra**
- Não fazer checkout destrutivo para “sincronizar” branches a partir da wiki
