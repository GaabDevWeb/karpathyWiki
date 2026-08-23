---
id: gaabwiki-current-state
tipo: conceito
status: atual
projeto: gaabwiki
dominio: project-state
escopo: meta
atualizado: 2026-08-23
confianca: alta
aliases:
  - Estado atual da GaabWiki
  - Current state
fontes:
  - README.md
  - .ai/index.md
  - .ai/log.md
  - /home/gaab/Documentos/gitHub/KernelBot/main.py
  - /home/gaab/Documentos/gitHub/OrbitBot/src/openai.js
relacionados:
  - gaabwiki-overview
  - gaabwiki-auditoria
  - gaabwiki-architecture
  - known-unknowns
tags:
  - gaabwiki
  - current-state
  - meta
---

# Estado atual da GaabWiki

> Se um agente entrar hoje: a GaabWiki é wiki-only; o estado de produto CURRENT de Kernel/Orbit está nas feature branches auditadas, não necessariamente em `main`.

## Observável nesta pasta

- Meta-wiki em `.ai/` com contrato, índice, log e páginas canónicas.
- `schema.md` e `corpus.yaml` na **raiz** (CLAUDE.md antigo dizia que estavam em `.ai/` — incorrecto).
- Wikis derivadas de 5 projectos.
- Sem código de aplicação; `.venv/` local (pip); `.obsidian/` para edição.
- `.github/workflows/` e `scripts/` na GaabWiki estão **vazios** (placeholders).

## Estado do ecossistema (código sibling)

- KernelBot + OrbitBot em `feature/kernel-orbit-v1-hardening`.
- Integração HTTP `/v1/chat` **implementada**.
- README do OrbitBot **desatualizado**.
- README do KernelBot omite Ops/Traces e afirma ausência de UI.
- `main.py` do KernelBot: `NameError` latente em `bootstrap_catalog_state`.
- Produção conjunta: **NÃO CONFIRMADA**.

## Limitações

- Sub-wikis ISS / Portifolio / Xray-Spec não foram re-auditadas contra HEAD nesta passagem.
- Portifolio tem wiki duplicada (`wiki/` e `.ai/wiki/`).
- Dezenas de repos locais só inventariados.
- Frontmatter canónico incompleto nas sub-wikis (muitas páginas sem `id`).
