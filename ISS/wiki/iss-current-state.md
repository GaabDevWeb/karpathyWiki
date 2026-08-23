---
id: iss-current-state
tipo: estado
status: atual
atualizado: 2026-08-22
fonte:
  - "[[fonte-readme]]"
  - "[[fonte-documentation]]"
relacionado:
  - "[[iss-architecture]]"
  - "[[iss-domain]]"
  - "[[iss-known-issues]]"
---

# Estado actual

Snapshot verificável do repositório ISS. Branch de referência: **`main`** (`778166e`, 2026-06-22).

Pergunta-guia: *Se eu entrar neste projecto hoje, o que realmente existe?*

## Propósito (IMPLEMENTADO)

Plataforma **estática** (HTML/CSS/JS) para estudar no browser: aulas em Markdown, exercícios, Mermaid, highlight, progresso em `localStorage`. Conteúdo em `content/`; a app faz `fetch()` e renderiza.

Fonte: README.md, `documentation.md`, `index.html`.

## Stack observada

| Camada | Tecnologia | Evidência |
|--------|------------|-----------|
| Site | HTML + JS vanilla + CSS; Tailwind via CDN | `index.html`, `public/*.html` |
| Markdown / diagramas | Marked.js 9.1.6, Highlight.js 11.9.0, Mermaid 10 (CDN) | `public/aula.html` |
| Persistência utilizador | `localStorage` (prefixo `iss-`) | `public/js/state.js` |
| Hosting | GitHub Pages (`.nojekyll` na raiz) | README; ficheiro `.nojekyll` |
| Pipeline | Node 22 + `@cursor/sdk` + LibreOffice + poppler | `.github/workflows/summarize-transcripts.yml` |
| Backend no site | **Nenhum** | README / documentation |
| `package.json` na raiz | **Ausente** — deps do pipeline instaladas no job CI | observação em disco |

## Estrutura principal (disco)

| Caminho | Papel |
|---------|--------|
| `index.html` | Home |
| `public/` | Páginas HTML + `css/` + `js/` |
| `content/` | Disciplinas, `lessons.json`, `search-index.json`, exercícios |
| `jsons/` | Export estruturado por lição (gerado pelo pipeline) |
| `downloads/` | Fontes VTT + documentos (entrada do scraper) |
| `config/` | `vtt-to-content.json`, `documents-context.json` |
| `agents/` | Prompts do agente de geração de lições |
| `.github/` | Workflow + scripts Node do pipeline |

## Funcionalidades do site (IMPLEMENTADO)

- Home com disciplinas, pesquisa (`search-index.json`), filtro 1º/2º/Ambos trimestres
- Páginas disciplina / aula / exercícios / exercício / stats / editor / train / about
- Progresso: aulas lidas, exercícios, checklists, revisões, streak, conquistas
- Render de frontmatter YAML, Mermaid, exercícios embutidos na aula

## Conteúdo (IMPLEMENTADO — contagens em `main`)

- **7** disciplinas em `content/disciplines.json`
- **109** aulas em `content/lessons.json` (ficheiros `.md` registados existem)
- **1** ficheiro `.md` órfão (em disco sem entrada em `lessons.json`): `content/fluencia-ia/aula-01-arquivo-de-testes.md`
- **529** exercícios em `content/exercises/exercises.json`
- **0** ficheiros `study-path.json` presentes (funcionalidade de trilha: código existe, dados ausentes → PARCIAL)

## Pipeline VTT → content (IMPLEMENTADO em `main`)

- Workflow `summarize-transcripts.yml`: cron diário 09:30 America/Sao_Paulo + `workflow_dispatch`
- Conversão Office→PDF; geração via Cursor Agent; publicação; export `jsons/`; Discord opcional
- Mapeamento canónico: `config/vtt-to-content.json` (não `discipline-map.yaml` — ver [[iss-known-issues]])

## Sync KernelBot / MySQL (EXPERIMENTAL — só `features`)

Scripts e workflow `sync-kernelbot-knowledge.yml` **existem na branch `features`**, não no workflow tree de `main`. Em `main` há artefactos `.github/reports/*.json` sem o workflow correspondente — ver [[iss-branches]] e [[iss-known-issues]].

## Testes automatizados

Status: **DESCONHECIDO / ausente** no sentido de suite de testes de aplicação. Não há pasta `test/` nem framework de testes do site. Há validação de catálogo na branch `features` (`validate-catalog.mjs`).

## Limitações relevantes

- Sem sync de progresso entre dispositivos (só `localStorage`)
- Site depende de CDNs externos
- `WIKI.md` referenciado no README **não existe** no histórico Git analisado
- Contribuição automática preferida; edição manual de lições é excepção documentada

## Em aberto / não confirmado nesta análise

- Estado operacional real dos secrets GitHub (`CURSOR_API_KEY`, Discord, etc.)
- Relação e estado actual do repositório **ActionTests** (mencionado como legado)
- Se o layout da home já foi refatorado relativamente ao diagnóstico antigo em [[fonte-relatorio-analise]]
