---
id: iss-project
tipo: projeto
status: atual
projeto: iss
dominio: content-platform
escopo: projeto
atualizado: 2026-08-23
confianca: alta
aliases:
  - ISS
  - Infet Students Summary
fontes:
  - ISS/raw/requirements/README-2026-08-22.md
  - ISS/index.md
relacionados:
  - gaabwiki-projects
  - gaabwiki-ecosystem
tags:
  - iss
  - content
  - publication
---

# Wiki — ISS

> Mapa do conhecimento do projecto **ISS** (repositório `GaabDevWeb/ISS`).  
> Actualizar quando páginas forem criadas, removidas ou alteradas significativamente.

## Identidade rápida

| Campo | Valor |
|-------|--------|
| Nome | ISS — Infet Students Summary *(marca no README; ver [[iss-known-issues]])* |
| Propósito | Plataforma estática de estudo (aulas Markdown + exercícios + progresso local) + pipeline VTT→lições |
| Repo origem | `https://github.com/GaabDevWeb/ISS` (local: `/home/gaab/Documentos/gitHub/ISS`) |
| Site | `https://gaabdevweb.github.io/ISS/` |
| Branch estado actual | `main` @ `778166e` (2026-06-22) |
| Última análise wiki | 2026-08-22 |

## Entrada

- [[iss-current-state]] — o que realmente existe hoje
- [[iss-architecture]] — site estático + pipeline GHA + ecossistema
- [[iss-domain]] — disciplinas, catálogo, modelo de conteúdo

## Decisões e convenções

- [[iss-decisions]] — decisões técnicas relevantes (e status)
- [[iss-conventions]] — padrões observados no código e configs

## História e branches

- [[iss-history]] — fases da evolução
- [[iss-branches]] — `main`, `features`, branches Cursor

## Problemas e planeamento

- [[iss-known-issues]] — contradições, lacunas, dívidas
- [[iss-roadmap]] — só itens com evidência (não inventar backlog)

## Integrações

- [[iss-integrations]] — StripperScrapper, Cursor SDK, Discord, KernelBot (branch `features`)

## Fontes

- [[fonte-readme]] — README (snapshot 2026-08-22)
- [[fonte-documentation]] — `documentation.md` do site
- [[fonte-orquestrer]] — prompt `agents/orquestrer.md`
- [[fonte-relatorio-analise]] — relatório histórico (removido do repo)
- [[fonte-documentation-features]] — `Documentation.md` na branch `features` (KernelBot)

## Vocabulário de tipos

| tipo | Páginas |
|------|---------|
| estado | 1 |
| arquitetura | 1 |
| dominio | 1 |
| decisao | 1 |
| convencao | 1 |
| historia | 1 |
| branch | 1 |
| problema | 1 |
| roadmap | 1 |
| integracao | 1 |
| fonte | 5 |
