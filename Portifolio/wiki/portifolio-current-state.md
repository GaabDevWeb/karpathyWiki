---
id: portifolio-current-state
tipo: estado
status: atual
atualizado: 2026-08-23
fonte:
  - "[[raw-readme]]"
  - "[[raw-product-decisions]]"
  - "[[raw-ascii-engine-platform]]"
  - "src/app/page.tsx"
  - "src/studio/AsciiLab.tsx"
---

# Estado atual do projeto

## Identidade

O projeto no estado atual é uma aplicação web de conversão de mídia em ASCII, entregue como produto standalone sob o nome `ASCII Engine`.

A evidência principal é:
- `src/app/page.tsx` exporta uma página que renderiza `<AsciiLab />`
- `src/studio/AsciiLab.tsx` define o shell principal com as tabs `Convert`, `Animate`, `Library` e `Docs`
- `PRODUCT_DECISIONS.md` explicitamente remove editor, playground, stats e studio da experiência principal

## Stack tecnológico

Com base no `package.json` e na estrutura do repositório:

- Next.js 15
- React 19
- TypeScript
- Tailwind CSS
- Vitest para testes
- ESLint e TypeScript checks
- Scripts Node para engenharia ASCII e benchmarks

## Arquitetura atual observada

### Camadas principais

1. App shell (`src/app`)
   - página raiz
   - metadata do produto

2. Studio shell (`src/studio`)
   - navegação por tabs
   - UI de conversão/animção/documentação
   - integração com presets e galeria

3. Runtime de processamento (`src/features/ascii-interaction`)
   - pipeline de image/animation
   - render, influência e física

4. Fachada de produto (`src/features/ascii-engine`)
   - re-exporta módulos públicos e SDK de produto
   - expõe CLI e conversores

5. Legado experimental (`src/legacy`)
   - superfícies extras preservadas para estudo posterior
   - não fazem parte do shell principal

## Funcionalidades implementadas no estado atual

- conversão de imagem para ASCII
- conversão de GIF / animação
- presets e refinamento de pipeline
- galeria e ícones
- exportação em TXT / PNG / SVG / JSON / GIF / ZIP
- CLI com `info`, `benchmark` e `convert`
- documentação embutida em `docs/` e módulos de produto

## Funcionalidades planejadas ou abandonadas

O projeto mantém uma linha de arquitetura que previa editor de cena, node graph, painel de plugins, efeitos e UI de projeto, mas a decisão de produto explicitamente moveu isso para fora do escopo principal.

Dessa forma, a documentação distingue:

- Implementado: conversão e animação
- Planejado: extensões do editor/scene/node-graph
- Abandonado para este ciclo: editor/painter/scene compositor como produto principal
- Histórico: superfícies ROOT OS e estúdios experimentais foram desacopladas

## Limitações e riscos

- O documento arquitetural registra que o canvas/image pipeline ainda possui gargalos de performance em main thread.
- A app ainda é fundamentada em cliente-side processing; não há backend ou persistência server-side em estado atual.
- O trabalho do branch `ascii-engine-platform` é uma plataforma de produto, mas a documentação reforça que não deve ser mergeada para `main` sem revisão, indicando uma linha de desenvolvimento paralela e não totalmente integrada.

## Status final

Status: atual

A implementação actual é coerente com a visão de produto “converter-first”, e não com a visão antiga de “portfolio do sistema operativo”. A raiz histórica permanece presente como memória e contexto de evolução, mas não como identidade operacional do produto agora em execução.
