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

## Resolvido na remediação de blockers (2026-08-23)

| Tema | Estado |
|------|--------|
| Branch provenance `main` vs `feature/kernel-orbit-v1-hardening` | **Documentado** em [[kernelbot-branches]]; `main` ≠ True Kernel |
| Colisões wikilinks `[[kernel]]`/`[[rag]]`/`[[memory]]` | **Corrigido** — convenção `{escopo}-{conceito}` em [schema.md](../../schema.md) §12 |
| GaabWiki sem Git próprio | **Corrigido** — repositório Git local inicializado nesta remediação |
| Declaração factual "Freeze V1 aceite" na wiki | **Removida** — freeze só via gate externo |

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
- Wikilinks em ISS/Portifolio/Xray podem ainda usar stems locais não prefixados — **PARTIAL** na remediação global.
