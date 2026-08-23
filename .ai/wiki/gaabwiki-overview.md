---
id: gaabwiki-overview
tipo: conceito
status: atual
projeto: gaabwiki
dominio: knowledge-memory
escopo: meta
atualizado: 2026-08-23
confianca: alta
aliases:
  - Visão geral da GaabWiki
  - Wiki overview
fontes:
  - README.md
  - .ai/index.md
  - /home/gaab/Documentos/gitHub/KernelBot/README.md
  - /home/gaab/Documentos/gitHub/OrbitBot/src/providers/kernelProvider.js
relacionados:
  - gaabwiki-ecosystem
  - gaabwiki-projects
  - gaabwiki-terminology
  - gaabwiki-auditoria
tags:
  - gaabwiki
  - overview
  - gaabwiki-memory
---

# GaabWiki — Visão geral da memória do ecossistema

## Propósito

A GaabWiki é a camada de conhecimento persistente **documental** do workspace local. Não substitui o código nem a documentação oficial dos projetos. Organiza síntese de arquitetura, decisões, histórico, fontes e relações para reduzir redescoberta.

A GaabWiki **não contém código de aplicação**. É Markdown + Git + wikilinks. Path: `/home/gaab/Documentos/gitHub/GaabWiki`. O workspace pai é `/home/gaab/Documentos/gitHub` (casing confirmado; `~/Documentos/GitHub` não existe).

## Papel do repositório

Este repositório guarda:

1. **Meta-wiki** em `.ai/` — índice, contrato, páginas canónicas.
2. **Wikis derivadas por projeto** em `ISS/`, `KernelBot/`, `OrbitBot/`, `Portifolio/`, `Xray-Spec/` — cópias de conhecimento, **não** os repos de código.
3. **Schema e corpus** na raiz: `schema.md`, `schema-example.md`, `corpus.yaml`.

Os repositórios de código vivem **ao lado**, no mesmo directório pai.

## Precedência de evidência

```text
código actual do repo de origem
>
configuração / testes
>
documentação actual do repo de origem
>
decisões registadas
>
wiki derivada
>
inferência marcada
```

Quando o código contradiz a wiki, o código vence. Quando a evidência é insuficiente, marcar `nao-confirmado`.

## O que a V1 cobre e o que não cobre

**Coberto em profundidade (código auditado 2026-08-23):** KernelBot, OrbitBot, e o mapa da própria GaabWiki.

**Coberto por wikis locais anteriores (não re-auditadas linha-a-linha nesta passagem):** ISS, Portifolio, Xray-Spec.

**Inventariados, sem sub-wiki V1:** AGENTS, CursorSKILLS, EchoRoute, KernelBot-Deploy, KernelPlanner, KernelBot.wiki, STRIPPERscrapper, e dezenas de repos locais. Ver [[gaabwiki-projects]] e [[known-unknowns]].

## Navegação recomendada

- [[gaabwiki-projects]] — inventário (documentados + satélites).
- [[gaabwiki-ecosystem]] — relações reais Kernel↔Orbit.
- [[gaabwiki-terminology]] — nomes canónicos vs aliases.
- [[known-unknowns]] — o que ainda não está confirmado.
- [[gaabwiki-auditoria]] — relatório da auditoria.

## Status

- estrutura geral: actualizada 2026-08-23
- relações Kernel↔Orbit: reconciliadas com código (branch `feature/kernel-orbit-v1-hardening`)
- freeze V1: **pendente** — decisão exclusiva de gate externo; ver [[known-unknowns]] e eventos em [[gaabwiki-auditoria]]
