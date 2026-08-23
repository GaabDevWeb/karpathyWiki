---
tipo: roadmap
status: atual
atualizado: 2026-08-22
relacionado:
  - "[[fonte-relatorio-analise]]"
  - "[[fonte-documentation-features]]"
  - "[[branches]]"
---

# Roadmap

Só itens com evidência. Separação explícita de origem. **Não** é backlog oficial do produto além do que as fontes dizem.

## Planejado explicitamente (documentação de branch / relatório)

### A — Integração KernelBot (branch `features`)

Fonte: `Documentation.md` em `features` ([[fonte-documentation-features]]).

- Workflow de sync validate → ingest → reload → verify
- Opção B2 já implementada **nessa branch**
- Backlog pós-deploy citado na mesma doc: validação OOM/`LIMIT` SQL; expandir sanitizer de logs no KernelBot

Estado relativamente a `main`: **não integrado** → tratar como planejado/experimental fora da linha canónica.

### B — Melhorias de produto do relatório de análise (histórico)

Fonte: `docs/RELATORIO-ANALISE-ISS.md` (removido; snapshot em raw). Exemplos propostos na altura:

- Treino por “conceitos fracos”
- Spaced repetition / próxima revisão
- Ligação mais forte aula ↔ exercício no modelo de dados
- Escalabilidade do layout da home
- Mais disciplinas com exercícios no formato programático

Estado: **ideias / recomendações de documento histórico** — não há issues tracker local confirmado a validar adopção. Algumas áreas (ex. `state.js`) podem já ter evoluído; não marcar como “ainda em falta” sem revalidação.

## Inferido (não oficial)

- Continuidade do cron VTT→content e crescimento de `content/` (padrão de commits do bot)
- Possível intenção de `WIKI.md` nunca materializada (inferência a partir de links mortos)

## Abandonado / substituído

| Item | Nota |
|------|------|
| `discipline-map.yaml` como mapa canónico | Substituído em `main` por `config/vtt-to-content.json` |
| Relatório em `docs/` no repo | Removido; não é roadmap activo |
| Nome “Plataforma Interativa de Estudos” no README | Substituído em mai/2026 |

## Ausência

Não foi encontrada pasta `planning/`, `roadmap.md` no repo, nem issues locais exportadas nesta análise.
