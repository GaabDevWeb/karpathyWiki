---
id: known-unknowns
tipo: problema
status: atual
projeto: gaabwiki
dominio: governance
escopo: meta
atualizado: 2026-08-23
confianca: media
aliases:
  - Lacunas conhecidas
  - Gaps de conhecimento
fontes:
  - /home/gaab/Documentos/gitHub/KernelBot
  - /home/gaab/Documentos/gitHub/OrbitBot
  - listagem /home/gaab/Documentos/gitHub
relacionados:
  - gaabwiki-health
  - gaabwiki-auditoria
  - gaabwiki-index
tags:
  - known-unknowns
  - governance
  - gaps
---

# Known Unknowns

Lacunas após auditorias V1 (2026-08-23). Visíveis por desenho — não são "aceitáveis por omissão".

## Resolvido na remediação adversarial (2026-08-23)

| Tema | Estado |
|------|--------|
| H1–H5 gate adversarial | **Corrigido** — branch provenance, Kernel≠KernelBot, paths, ecosystem, orbitbot-kernel |
| M1 links `rag.md` | **Corrigido** → `kernelbot-rag.md` |
| M2 `orbitbot-branches` | **Corrigido** — paridade com `kernelbot-branches` |
| M3 stems satélites | **Corrigido** — prefixos `iss-`, `portifolio-`, `xray-spec-` |
| M4 Portifolio duplicado | **Corrigido** — canónico `Portifolio/wiki/`; `.ai/wiki/` excluído do corpus current |

## Ainda não confirmado

### 1. Merge `feature/kernel-orbit-v1-hardening` → `main`
- Status: NÃO CONFIRMADO
- `main` de KernelBot ainda é `engine/` + `frontend/`; feature é árvore distinta.

### 2. Operação conjunta em produção
- Status: NÃO CONFIRMADO
- Integração HTTP existe no código da feature; E2E WhatsApp+Kernel não executado nesta auditoria.

### 3. Relação `gaabFaculty/KernelBot` (git pai) vs `GaabDevWeb/KernelBot`
- Status: NÃO CONFIRMADO

### 4. AGENTS / CursorSKILLS / MegaBrain
- Status: PARCIAL — inventariados; sem ligação runtime ao chat.

### 5. ISS / Portifolio / Xray-Spec vs HEAD actual
- Status: NÃO RE-AUDITADO

### 6. Portifolio ↔ ASCII-LAB-readme
- Status: NÃO CONFIRMADO

### 7. Freeze V1
- Status: **PENDENTE** — aguarda novo gate externo pós-remediação de blockers.

## Conflitos documentados (código vence)

### A. README OrbitBot vs `kernelProvider`
### B. README KernelBot "sem interface web" vs `/ops` e `/traces`
### C. `raw/docs-wiki/` cita `engine/`; feature usa `kernel/`
### D. `main.py` chama `bootstrap_catalog_state` sem import
### E. Testes KernelBot importam `engine.*` / `core.*`
### F. OpenRouter no OrbitBot — código morto no fluxo da feature

## Por desenho V1

- Retrieval técnico sobre a GaabWiki: não implementado.
- Stems satélites: prefixados (`iss-*`, `portifolio-*`, `xray-spec-*`).
