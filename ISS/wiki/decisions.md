---
tipo: decisao
status: atual
atualizado: 2026-08-22
relacionado:
  - "[[architecture]]"
  - "[[integrations]]"
  - "[[branches]]"
---

# Decisões

Decisões técnicas com evidência. Status: **Atual** / **Substituída** / **Abandonada** / **Experimental (outra branch)**.

---

# Decisão: Site 100% estático sem backend

## Contexto

Necessidade de plataforma de revisão de aulas/exercícios hospedável de forma simples para estudantes.

## Decisão

HTML/CSS/JS com `fetch` a ficheiros em `content/`; progresso só em `localStorage`; deploy GitHub Pages.

## Motivo

Baixa complexidade operacional; alinhado a conteúdo versionado em Git; sem custo de servidor de aplicação.

## Alternativas

- SPA com build (React/Vite) — não adoptada no estado actual
- Backend + auth + sync de progresso — não presente

## Evidência

README; `documentation.md`; ausência de servidor/API no repo.

## Status

Atual

---

# Decisão: `lessons.json` como SSOT de navegação

## Contexto

Aulas têm frontmatter YAML e ficheiros em pastas; URLs usam `d` + `a`.

## Decisão

O par `(discipline, slug)` em `content/lessons.json` define existência e URL. Frontmatter é documentação/metadados; não substitui o JSON.

## Motivo

Catálogo único para home, disciplina, pesquisa e pipeline de publicação.

## Alternativas

- Descoberta só por filesystem — rejeitada na prática do código (`getLesson` no JSON)

## Evidência

`documentation.md` (“Quem manda na navegação é `lessons.json`”); `iss-content.mjs` actualiza o catálogo na publicação.

## Status

Atual

---

# Decisão: Pipeline VTT → lições via Cursor SDK no GitHub Actions

## Contexto

Gerar material de ensino a partir de transcrições Infnet sem editar cada aula à mão.

## Decisão

Workflow `summarize-transcripts.yml` com `@cursor/sdk`, prompts em `agents/`, commit automático do bot em `main`, skip se já publicado.

## Motivo

Automação end-to-end após push de `downloads/`; validação de contrato de saída no orquestrador.

## Alternativas

- Geração local manual / orquestração por agentes humanos (`orquestrer.md` descreve fluxo agentic paralelo)
- Python local obrigatório no ISS — README afirma que **não** há script Python/local obrigatório no ISS para esta etapa

## Evidência

`.github/workflows/summarize-transcripts.yml`; `summarize-transcripts.mjs`; README Etapa 2.

## Status

Atual

---

# Decisão: Mapeamento downloads → disciplina em JSON de config

## Contexto

Pastas do scraper têm nomes longos; slugs ISS são estáveis.

## Decisão

`config/vtt-to-content.json` é a fonte de mapeamento usada pelo código de publicação (`mapDownloadsFolder` em `iss-content.mjs`).

## Motivo

Determinismo: `discipline` vem da config, não do modelo.

## Alternativas

- `agents/discipline-map.yaml` — usado em branches Cursor e citado em `orquestrer.md`; **não** está em `main` nem é lido pelo script actual

## Evidência

`iss-content.mjs`; README; contraste com `orquestrer.md` e commits Cursor.

## Status

Atual (substitui / diverge da abordagem YAML das branches Cursor — ver [[branches]])

---

# Decisão: Separação StripperScrapper (repo) vs ISS (hub)

## Contexto

Scraping autenticado Infnet vs publicação de conteúdo e site.

## Decisão

Scraper noutro repositório ([STRIPPERscrapper](https://github.com/GaabDevWeb/STRIPPERscrapper)); ISS versiona `downloads/` + pipeline + site.

## Motivo

Separar credenciais/sessão local do site público e do Actions.

## Evidência

README “Repositórios relacionados”.

## Status

Atual

---

# Decisão: Sync ISS → KernelBot (MySQL + BM25)

## Contexto

Chatbot KernelBot precisa do catálogo/conteúdo ISS em MySQL e índice em RAM.

## Decisão (na branch `features`)

Workflow `sync-kernelbot-knowledge.yml`: validate → ingest Python/pymysql → reload → verify. Opção **B2**: um documento por lição, `MAX_CONTENT` pré-UPSERT.

## Motivo

Alinhar SSOT do ISS com knowledge base do bot.

## Alternativas

- Sem sync automático (só site estático) — estado de **`main`**
- Chunking no MySQL — substituído por B2 unificado na documentação da branch `features`

## Evidência

Branch `features` commits `b80775d`, `d67107f`, `b432a6f`; `Documentation.md` nessa branch; reports em `main` sem workflow.

## Status

Experimental / não integrado em `main` (estado do código canónico = sem este workflow)

---

# Decisão: Reorganização HTML sob `public/`

## Contexto

Páginas e assets na raiz misturados com conteúdo.

## Decisão

Mover páginas auxiliares e `css/`/`js/` para `public/`; manter `index.html` na raiz; router ajusta paths.

## Evidência

Commit `f624761` (move + remoção de `docs/RELATORIO-ANALISE-ISS.md`).

## Status

Atual

---

# Decisão: Nome público “Infet Students Summary”

## Contexto

Nome anterior no README: “Plataforma Interativa de Estudos” (commit `93dfad9`, 2026-05-10).

## Decisão

Rebranding do título para “ISS — Infet Students Summary”.

## Nota

“Infet” vs “Infnet”; agente ainda diz “Interactive Study System”. Status de naming: ver [[known-issues]].

## Status

Atual na UI/README; expansão do acrónimo **em conflito** entre fontes
