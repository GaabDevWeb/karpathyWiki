---
tipo: problema
status: atual
atualizado: 2026-08-22
relacionado:
  - "[[current-state]]"
  - "[[branches]]"
  - "[[fonte-readme]]"
---

# Problemas conhecidos e contradições

Classificação por evidência. Nem todo TODO é crítico.

## Contradições documentadas

### C1 — `WIKI.md` referido mas inexistente

- **Fonte A:** README.md e `documentation.md` linkam `WIKI.md`
- **Fonte B:** ficheiro ausente; `git log --all -- WIKI.md` vazio
- **Status:** conflito não resolvido (doc aponta para artefacto nunca versionado neste repo)
- **Estado provável:** documentação escrita antecipando wiki técnica que não chegou a ser commitada, ou vive noutro sítio não analisado

### C2 — Expansão do acrónimo ISS

- **Fonte A:** README / `index.html` / `documentation.md` → “Infet Students Summary”
- **Fonte B:** `agents/content-summary-agent.md` → “Interactive Study System”
- **Fonte C:** relatório histórico → “Interactive Study System”; README antigo → “Plataforma Interativa de Estudos”
- **Status:** conflito não resolvido (marca vs prompt)
- **Nota:** “Infet” vs instituição “Infnet” — possível typo; não confirmado como intencional

### C3 — Mapa downloads → disciplina

- **Fonte A (código `main`):** `config/vtt-to-content.json` via `iss-content.mjs`
- **Fonte B:** `agents/orquestrer.md` exige `agents/discipline-map.yaml`
- **Fonte C:** branches Cursor adicionaram `discipline-map.yaml`
- **Status:** conflito docs/agente vs implementação GHA
- **Estado actual pelo código:** JSON em `config/`

### C4 — KernelBot reports sem workflow em `main`

- **Fonte A:** `.github/reports/ingest-report.json` e `validate-report.json` presentes em `main` (introduzidos em `83e1c8b`)
- **Fonte B:** único workflow em `main` é `summarize-transcripts.yml`
- **Fonte C:** workflow + scripts de sync só em `features`
- **Status:** inconsistência de árvore; reports não provam que sync corre em `main`

### C5 — Cópia `agents/documentation.md` vs raiz

- `agents/documentation.md` espelha documentação do site mas **sem** a secção de pipeline automático presente em `documentation.md` da raiz (observado na leitura)
- Risco: agente orquestrador a usar cópia desactualizada

## Dívidas / lacunas

| Item | Classificação | Evidência |
|------|---------------|-----------|
| Sem suite de testes do site | dívida | ausência de testes automatizados |
| `study-path.json` não populado | PARCIAL | código sim, ficheiros não |
| Aula órfã `fluencia-ia/aula-01-arquivo-de-testes.md` | dados | em disco, fora de `lessons.json` |
| Dependência CDN (Tailwind/Marked/…) | risco operacional | HTML |
| ActionTests “legado” | DESCONHECIDO | só menção README; repo não analisado aqui |
| Layout home / escala de disciplinas | possivelmente mitigado desde relatório | relatório antigo vs código actual — não revalidado UI nesta passagem |

## Comentários TODO/FIXME no código de app

Procura limitada fora de `content/`/`downloads/`: sem concentração crítica listada nesta análise. Não transformar ausência de matches em “código limpo” absoluto — pesquisa não foi exaustiva em todos os binários.

## Problemas só na branch `features`

- Secrets `KB_DB_*`, `KERNELBOT_*` necessários para sync
- Runners GitHub não alcançam KernelBot em `127.0.0.1` (documentado na Documentation da branch)
- Backlog pós-deploy B2 mencionado na doc da branch (LIMIT SQL, sanitizer) — **PLANEJADO** naquela doc, não estado de `main`
