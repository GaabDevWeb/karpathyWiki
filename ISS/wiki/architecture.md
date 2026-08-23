---
tipo: arquitetura
status: atual
atualizado: 2026-08-22
fonte:
  - "[[fonte-readme]]"
  - "[[fonte-documentation]]"
relacionado:
  - "[[current-state]]"
  - "[[integrations]]"
  - "[[decisions]]"
---

# Arquitectura

Visão verificada em 2026-08-22 contra `main`.

## Visão em três fases (ecossistema)

```text
Infnet (portal)
    → StripperScrapper (repo separado, local)
        → downloads/ no ISS
            → GitHub Actions (Cursor SDK)
                → content/ + lessons.json + search-index + jsons/
                    → GitHub Pages (browser)
```

O site **não executa** o pipeline. O pipeline **não serve** UI.

## Componentes do site

| Componente | Responsabilidade | Localização |
|------------|------------------|-------------|
| Home | Disciplinas, pesquisa, filtro trimestre | `index.html` + `public/js/app.js` (`initHome`) |
| Content loader | Fetch JSON/MD; base path `content/` vs `../content` | `public/js/content.js` |
| Router | Query params `d=`, `a=`, `slug=`; prefixo `public/` | `public/js/router.js` |
| Markdown | Frontmatter, Mermaid, exercícios embutidos, checklists | `public/js/markdown.js` |
| Estado | Progresso unificado em `localStorage` | `public/js/state.js` |
| Exercícios | Lista, página, editor/testes quando aplicável | `public/js/exercises.js`, `code-editor.js`, `code-runner.js` |
| Stats / train | Estatísticas e treino | `public/js/stats.js`, `train.js` |

### Fluxo ao abrir uma aula

1. `aula.html?d=<disciplina>&a=<slug>`
2. `fetch` `lessons.json` → `getLesson(discipline, slug)`
3. `fetch` do path em `lesson.file` sob `content/`
4. Parse frontmatter + render + Mermaid/Highlight

Fonte: `documentation.md`.

## Dados canónicos

| Artefacto | Papel |
|-----------|--------|
| `content/disciplines.json` | Catálogo de disciplinas |
| `content/lessons.json` | **Registo canónico** de aulas — chave `(discipline, slug)` |
| `content/search-index.json` | Excerpts para pesquisa |
| `content/<disciplina>/*.md` | Corpo das aulas |
| `content/exercises/` | Banco de exercícios independente |
| `jsons/` | Export estruturado por lição (consumo externo / KernelBot) |

**Quem manda na navegação:** `lessons.json`, não o frontmatter do `.md`.

## Pipeline (Actions)

Ficheiro: `.github/workflows/summarize-transcripts.yml`

| Step | Script / ferramenta |
|------|---------------------|
| Office→PDF | `convert-office-documents.mjs` + LibreOffice |
| Gerar lições | `summarize-transcripts.mjs` + `@cursor/sdk` |
| Publicar | `iss-content.mjs` (`publishLessonMarkdown`, estados published/orphan/missing) |
| Contexto docs | `document-context.mjs` + `config/documents-context.json` |
| Export JSON | `export-lessons-json.mjs` / `lesson-json-export.mjs` |
| Commit bot | `github-actions[bot]` com `[skip ci]` |
| Notify | `discord-notify.sh` (opcional) |

Prompts: `agents/content-summary-*.md`. Validação de saída rejeita meta-texto / resumos parciais (`summarize-transcripts.mjs`).

## Configuração de mapeamento

- **IMPLEMENTADO em `main`:** `config/vtt-to-content.json` — pasta em `downloads/` → `discipline` + `content_dir`
- **Histórico / Cursor branches:** `agents/discipline-map.yaml` — ver [[branches]]; **não** está em `main`
- Contexto de PDFs: `config/documents-context.json` (`per_lesson` vs `discipline_all`, ranges, filename patterns)

## O que não é arquitectura do site

- Autenticação de utilizadores finais — ausente
- API HTTP própria — ausente
- Base de dados do site — ausente (progresso só local)

Integração MySQL/KernelBot: [[integrations]], branch `features`.
