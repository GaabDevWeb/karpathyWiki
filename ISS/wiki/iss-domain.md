---
id: iss-domain
tipo: dominio
status: atual
atualizado: 2026-08-22
fonte:
  - "[[fonte-documentation]]"
  - "[[fonte-readme]]"
relacionado:
  - "[[iss-current-state]]"
  - "[[iss-conventions]]"
---

# Domínio

Conhecimento de domínio do ISS: estudo académico INFNET, conteúdo versionado, catálogo de aulas.

## Produto

- **Nome de marca no UI/README:** “ISS — Infet Students Summary”
- **Expandido no agente de ensino:** “Interactive Study System” (`agents/content-summary-agent.md`) — ver [[iss-known-issues]]
- **Instituição referida:** Infnet / INFNET (portal `infnet.online` no ecossistema do scraper)
- **Slogan (README):** “Teoria que vira código. Revisão que vira domínio.”

## Entidades

| Entidade | Identificador | Notas |
|----------|---------------|--------|
| Disciplina | `slug` em `disciplines.json` | Tem `trimester` (`1`, `2` ou `[1,2]`), `order`, professor |
| Aula / lição | Par `(discipline, slug)` | Único por disciplina; `order` alinha com `NN` do VTT |
| Ficheiro aula | `file` relativo a `content/` | Convenção frequente: `aula-NN-titulo.md` |
| Exercício | `slug` global em `exercises.json` | Independente das aulas; pode ligar por `concepts` / `discipline` |
| Pesquisa | chave lógica `discipline/slug` no índice | Sem entry → aula acessível, pesquisa só por títulos |

## Disciplinas em `main` (2026-08-22)

| slug | Título (UI) | Trimestre | # aulas (`lessons.json`) |
|------|-------------|-----------|---------------------------|
| `python` | Python | 1 | 16 |
| `fluencia-ia` | Fluência em IA | 2 | 9 |
| `visualizacao-sql` | Introdução à Visualização de Dados e SQL | 1 | 21 |
| `sql-modelagem-relacional` | SQL e Modelagem Relacional | 2 | 16 |
| `planejamento-curso-carreira` | Planejamento de Curso e Carreira | 1 | 10 |
| `projeto-bloco` | Projeto de Bloco — Fundamentos de Processamento de Dados | 1 e 2 | 17 |
| `python-processamento-dados` | Python para Processamento de Dados | 2 | 20 |

Total: **109** entradas em `lessons.json`.

## Contrato pedagógico da lição gerada (IMPLEMENTADO no prompt)

O agente de conteúdo (`content-summary-agent.md`) exige lição completa (não resumo), incluindo:

- Frontmatter YAML
- Corpo estruturado ISS
- ≥1 diagrama Mermaid
- Secção **Laboratório de Prática**
- Blocos comentados `CONCEPT_EXTRACTION`, `EXERCISES_JSON`, `LESSONS_JSON_HINT`

O pipeline rejeita saídas que sejam meta-texto ou entrega parcial.

## Progresso do estudante (IMPLEMENTADO)

Chaves `localStorage` (entre outras) em `state.js`: `iss-read-lessons`, `iss-exercises-completed`, `iss-checklist`, `iss-reviewed-exercises`, `iss-revision-*`, `iss-activity-dates`, `iss-achievements-unlocked`, `iss-last-visited`. Sem servidor.

## Trilha `study-path.json` (PARCIAL)

Código em `content.js` / `app.js` suporta `content/<disciplina>/study-path.json`. Em `main` **não há** nenhum ficheiro desse tipo — feature de UI pronta, dados não populados.
