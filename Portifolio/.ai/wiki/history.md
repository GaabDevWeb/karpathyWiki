---
tipo: arquitetura
status: atual
atualizado: 2026-08-23
fonte:
  - "[[raw-git-log]]"
  - "[[raw-ascii-engine-platform]]"
  - "[[raw-product-decisions]]"
---

# História do projeto

## Fase 1 — Portfólio e shell ROOT OS

A origem do repositório estava ligada a um portfólio com identidade de sistema operacional e janelas interativas. Esse contexto aparece no README e no histórico anterior do projeto, mas não representa o produto atual em execução.

## Fase 2 — motor de interação ASCII

A base `main` e a branch `asciiEngine` documentam a introdução do `AsciiInteractionEngine` e da arquitetura associada. Esse ponto marca a consolidação do motor de render e processamento que sustenta a conversão ASCII.

## Fase 3 — extração do produto

A branch `ascii-engine-next` adiciona a fachada `ascii-engine`, shell de studio e estrutura de SDK/CLI. Essa fase é a primeira grande separação entre produto e engine.

## Fase 4 — product pivot para converter-first

A branch atual `ascii-engine-platform` remarca o produto como `converter-first`, reduz a UI principal a conversão e animação e move interfaces experimentais para `src/legacy/`.

## Elementos históricos relevantes

- `README.md` ainda carrega a visão antiga de portfólio
- `PRODUCT_DECISIONS.md` registra a decisão explícita do pivô
- `docs/architecture/ASCII-ENGINE-PLATFORM.md` consolida a visão atual da arquitetura
- as fases P0–P12 e W0–W8 documentam a evolução do produto em ciclos

## Status

Status: atual

O projeto tem uma história clara de evolução arquitetural e de produto, com a fase atual sendo um produto standalone de conversão ASCII, sem apagar o contexto histórico das fases anteriores.
