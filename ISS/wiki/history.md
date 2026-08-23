---
tipo: historia
status: atual
atualizado: 2026-08-22
relacionado:
  - "[[branches]]"
  - "[[decisions]]"
  - "[[fonte-relatorio-analise]]"
---

# História

Evolução de alto nível com base em Git e documentos. Não é changelog commit-a-commit.

## Fase 1 — Núcleo estático (fev 2026)

- Commits iniciais (`1cac9ff`, `a7c8885`, …): HTML, CSS, JSON de conteúdo, deploy
- Produto como site de estudo / anotações Markdown no browser

## Fase 2 — Expansão de produto educacional (mar 2026)

- Tag `v0.1-alpha` (2026-03-24): exercícios de programação e metadados de conceitos
- Crescimento de aulas, stats, editor, exercícios

## Fase 3 — Análise e reorganização estrutural

- Documento `docs/RELATORIO-ANALISE-ISS.md` diagnosticou LXP estática, limitações (conceitos inconsistentes, layout home, ausência de state unificado na altura, etc.)
- Commit `f624761`: move assets para `public/`; **remove** o relatório `docs/`
- Parte das recomendações do relatório (ex. `state.js` unificado) **parece** ter sido endereçada depois — Status: parcial / verificar caso a caso vs relatório antigo

## Fase 4 — Pipeline de conteúdo e rebranding (mai 2026)

- Integração scraper → `downloads/` versionado; Actions com Cursor SDK
- README reescrito para ecossistema de 3 etapas; nome “Infet Students Summary” (`93dfad9`, 2026-05-10)
- Branches Cursor publicam aulas e experimentam `discipline-map.yaml`
- Discord notifications no workflow
- Export `jsons/` estruturado

## Fase 5 — KernelBot (branch `features`, mai 2026)

- Pipeline validate → ingest MySQL → reload → verify
- Opção B2 (documento unificado por lição)
- **Não merged** em `main` até à data da análise

## Fase 6 — Operação contínua em `main` (mai–jun 2026)

- Bot `github-actions[bot]` publica lições regularmente (`chore: lições ISS…`)
- Melhorias Discord, resolução de contexto de documentos (ranges, filename patterns — commit `c545afa`)
- Tip actual `778166e` (2026-06-22): novas lições (agentes IA, SQL aggregations, Flask, etc.)

## Remoções / abandonos notáveis

| Item | Evidência |
|------|-----------|
| `docs/RELATORIO-ANALISE-ISS.md` | Removido em `f624761` — preservado em `raw/research/` desta wiki |
| `agents/discipline-map.yaml` | Só em branches Cursor; não em `main` |
| Sync KernelBot em `main` | Código na branch `features` apenas |
| `WIKI.md` referenciado | Nunca encontrado no histórico Git analisado |
| Páginas HTML na raiz (exceto `index.html`) | Movidas para `public/` |

## Autores observados (shortlog)

GaabDevWeb, Gaab, `github-actions[bot]`, Cursor Agent — contagens aproximadas no `git shortlog` local.
