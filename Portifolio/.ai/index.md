# Índice da Wiki — Portifolio / ASCII Engine

> **SUPERSEDED / AUXILIARY:** Esta cópia em `Portifolio/.ai/` é **histórica**. Fonte canónica CURRENT: [Portifolio/index.md](../index.md) e `Portifolio/wiki/portifolio-*.md`. Excluída do corpus `current` em `corpus.yaml`.

## Visão geral

Este projeto começou como um portfólio orientado a um ambiente de sistema operacional (ROOT OS), mas o estado atual do código e da documentação indica uma transição para um produto focado em conversão de mídia em ASCII: a `ASCII Engine`.

### Estado atual observado

- Branch atual: `ascii-engine-platform`
- App principal: `src/app/page.tsx` renderiza `AsciiLab`
- Shell principal: `src/studio/AsciiLab.tsx`
- Produto: `Convert · Animate · Library · Docs`
- Experimentos e superfícies antigas: movidas para `src/legacy/`

## Mapa da Wiki

- [[portifolio-current-state]] — resumo do que realmente existe hoje
- [[portifolio-architecture]] — arquitetura actual e principais módulos
- [[portifolio-ascii-engine-product]] — visão profunda do produto ASCII Engine (link canónico; `.ai/wiki/` é SUPERSEDED)
- [[portifolio-decisions]] — decisões arquiteturais e de produto relevantes
- [[portifolio-branches]] — análise das branches locais/remotas e do estado histórico
- [[portifolio-history]] — evolução do projeto em fases
- [[portifolio-roadmap]] — plano documentado e itens implementados vs abandonados
- [[portifolio-source-index]] — índice das fontes preservadas e da evidência de origem

## Fontes primárias preservadas

- [[raw-readme]]
- [[raw-product-decisions]]
- [[raw-ascii-engine-platform]]
- [[raw-git-branches]]
- [[raw-git-log]]

## Observações importantes

- O README do repositório descreve um “ROOT OS Portfolio”, mas o código atual e a documentação arquitetural do branch `ascii-engine-platform` descrevem uma mudança clara de foco para conversão ASCII profissional.
- Essa mudança não é uma remoção completa do passado: os artefactos legados permanecem como contexto histórico e como referência para produto futuro, mas não fazem mais parte do shell principal.
- Não há evidência de banco de dados, backend ou API própria neste estado atual. O projeto é entregue como app Next.js + React + TypeScript, com render e processamento no cliente.
