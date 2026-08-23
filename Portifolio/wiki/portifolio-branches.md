---
id: portifolio-branches
tipo: arquitetura
status: atual
atualizado: 2026-08-23
fonte:
  - "[[raw-git-branches]]"
  - "[[raw-git-log]]"
---

# Histórico e estado das branches

## Branch considerada estado atual

- `ascii-engine-platform`
- HEAD: `91f96f3` — `feat(ascii-engine): ship converter-first v1.0 product shell`

Essa é a branch que melhor representa o estado atual do produto observado no código e na documentação.

## Visão resumida por branch

| Branch | Status | Papel observável |
|---|---|---|
| `main` | histórico | baseline estrutural + engine e documentação antiga |
| `ascii-engine-next` | relevante | fachada de produto e shell de studio |
| `ascii-engine-platform` | atual | shell converter-first, foco em produto standalone |
| `ascii-lab-main` | histórico / paralelo | apresentação da ASCII Lab e documentação visual |
| `asciiEngine` | histórico | nome antigo do esforço estrutural |
| `feature` | experimental | refatoração e atualização de dependências |
| `penpen` | experimental | gestão de janelas e pointer tracking |
| `projectsSecion` | histórico | limpeza de arquivos e detalhes de projetos |
| `refactor` | histórico | ajustes de README e modo workspace |

## Evolução observada

### Fase 1 — ROOT OS / portfólio

O projeto iniciou como um portfólio visual e de sistema operacional, com forte identidade de shell interativo.

### Fase 2 — ASCII Engine Next

A branch `ascii-engine-next` marca a transição para uma fachada `ascii-engine` e um shell baseado em SDK/CLI. A documentação menciona um produto modular que evolui a partir do ROOT OS.

### Fase 3 — ASCII Engine Platform

A branch `ascii-engine-platform` representa o foco corrente: converter, animar, explorar biblioteca e docs. A estratégia foi reduzir a UI do produto para o que era efetivamente central para a ferramenta.

### Fase 4 — legado preservado

Branches e módulos experimentais não desapareceram sem rastreio: em vez disso, a documentação e `src/legacy/README.md` registram a decisão de manter o legado para possível extração futura.

## Contradição observada

O nome do repositório e o README sugerem um portfólio, mas o estado atual do código e a arquitetura em `docs/architecture/ASCII-ENGINE-PLATFORM.md` apontam para um produto independente. A correta leitura é histórica e evolutiva, e não simultânea.

## Status

Status: atual

A branch `ascii-engine-platform` é a melhor representação do estado atual do projeto, mas a evolução das outras branches continua sendo parte importante do contexto operacional.
