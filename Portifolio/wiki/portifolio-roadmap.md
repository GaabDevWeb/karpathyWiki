---
id: portifolio-roadmap
tipo: planejamento
status: atual
atualizado: 2026-08-23
fonte:
  - "[[raw-ascii-engine-platform]]"
  - "[[raw-product-decisions]]"
---

# Roadmap observado

## Implementado no estado atual

- conversão de imagem para ASCII
- conversão de GIF / animação
- presets e refinamento de pipeline
- shell `Convert · Animate · Library · Docs`
- exportação em vários formatos
- CLI básico de `info`, `benchmark` e `convert`
- estrutura de SDK/fachada `ascii-engine`

## Planejado formalmente na arquitetura

A documentação de arquitetura documenta fases de evolução para:

- `P0` a `P12` — construção e hardening da plataforma ASCII Engine
- `W0` a `W8` — standalone scene editor e outros módulos
- `workspaces`, `timeline`, `node graph`, `plugins`, `AI` e exportadores mais avançados

## Abandonado ou fora de escopo neste ciclo

O plano de produto suprime explicitamente como fora de escopo:

- pintura / editor de ASCII em estilo Photoshop
- scene compositor e node editor como centro do produto
- efeitos e playground como primeira experiência do usuário
- editor timeline e painéis de projeto como prioridade principal

## Observação de rastreabilidade

O roadmap real do projeto não é genérico: ele está documentado em `docs/architecture/ASCII-ENGINE-PLATFORM.md` e reforçado por `PRODUCT_DECISIONS.md`. Isso torna a linha de planejamento parcialmente observável e parcialmente histórica.

## Status

Status: atual

Há evolução planejada e implementada, mas o projeto explicitamente escolheu um escopo reduzido: ser um conversor profissional de mídia para ASCII, não um editor completo ou ambiente de criação visual.
