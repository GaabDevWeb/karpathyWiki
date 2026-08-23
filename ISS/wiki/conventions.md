---
tipo: convencao
status: atual
atualizado: 2026-08-22
fonte:
  - "[[fonte-documentation]]"
  - "[[fonte-readme]]"
relacionado:
  - "[[domain]]"
  - "[[architecture]]"
---

# Convenções

Padrões **observados** neste repositório (não “boas práticas” genéricas).

## Nomenclatura de conteúdo

- Slugs de disciplina e aula: **kebab-case**
- Ficheiros de aula frequentes: `aula-NN-titulo-curto.md` sob `content/<disciplina>/`
- VTT de entrada: `Aula_NN_-_DDMMYYYY.vtt` — `NN` corresponde a `order` em `lessons.json`
- Pastas em `downloads/`: nomes do portal (ex. `Introducao_a_Programacao_com_Python`) mapeados em `config/vtt-to-content.json`
- Export `jsons/`: `<disciplina>__NN__<slug>.json`

## Catálogo

- Chave canónica de aula: `(discipline, slug)` única
- `file` em `lessons.json` relativo a `content/`
- Frontmatter pode repetir `slug`/`discipline`/`order` mas **não** governa URLs
- Pesquisa: actualizar `search-index.json` quando full-text importa; ausência não bloqueia acesso por URL

## Frontend

- Scripts em `public/js/` carregados por `<script defer>` nas páginas HTML
- Dependências de render via **CDN** (sem bundler no repo)
- Tailwind via `cdn.tailwindcss.com` nas páginas observadas
- Prefixo de estado: `iss-` (excepção: `iss_home_trimester` com underscore em `app.js`)

## Pipeline / CI

- Commits automáticos de lições: mensagem `chore: lições ISS automáticas (VTT → content/) [skip ci]`
- Commits de scraper: `chore: dados do scraper` (com ou sem `[skip ci]`)
- Secrets documentados: `CURSOR_API_KEY` (obrigatório), `CURSOR_MODEL_ID` (var opcional), `DISCORD_WEBHOOK_URL` (opcional)
- Checkout do workflow fixo em `ref: main`

## Prompts de agente

- Contrato pedagógico: `agents/content-summary-agent.md` + `content-summary-style-guide.md`
- Orquestração agentic documentada em `agents/orquestrer.md` (pode divergir do pipeline GHA — ver [[known-issues]])
- Cópia espelhada parcial: `agents/documentation.md` ≈ documentação do site (sem secção pipeline na cópia analisada)

## Contribuição

- Preferir fluxo automático (VTT → Actions) a edição manual de aulas
- Manual: disciplina em `disciplines.json` → `.md` → `lessons.json` → opcional `search-index.json`
- Branch naming sugerido no README: `feature/descricao-curta`

## Excepções / legado observados

- `content/fluencia-ia/aula-01-arquivo-de-testes.md` no disco sem registo em `lessons.json`
- Relatórios `.github/reports/` em `main` sem workflow KernelBot correspondente
- Branch `features` usa `Documentation.md` (D maiúsculo) vs `documentation.md` em `main`
