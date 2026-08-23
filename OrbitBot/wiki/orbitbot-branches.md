---
id: orbitbot-branches
tipo: historico
status: atual
projeto: orbitbot
dominio: git
escopo: projeto
atualizado: 2026-08-23
confianca: alta
fontes:
  - /home/gaab/Documentos/gitHub/OrbitBot
relacionados:
  - orbitbot-current-state
  - orbitbot-architecture
  - orbitbot-kernel
  - kernelbot-branches
tags:
  - branches
  - provenance
---

# Branches relevantes do OrbitBot

> Repositório: `/home/gaab/Documentos/gitHub/OrbitBot`  
> Evidência Git: 2026-08-23

## Classificações

| Tag | Significado |
|-----|-------------|
| **CURRENT (workspace)** | Checkout local verificado |
| **IMPLEMENTED** | Ficheiro/comportamento confirmado no código |
| **BRANCH-SPECIFIC** | Não assumir em `main` |
| **HISTORICAL** | Legado em `main` |
| **TARGET / UNKNOWN** | Merge ou produção não confirmados |

---

## O que existe em `OrbitBot/main`?

**Classificação:** CURRENT-de-`main` / HISTORICAL relativamente ao contrato Kernel.

| Artefacto | Em `main`? | Evidência |
|-----------|------------|-----------|
| `src/providers/kernelProvider.js` | **Não** | `git cat-file -e main:src/providers/kernelProvider.js` → ausente |
| Integração `POST /v1/chat` | **Não** | Fluxo OpenRouter/WPPConnect legado |
| Baileys (versão feature) | Parcial | `main` pode divergir; não re-auditado linha-a-linha aqui |

`main` = bot WhatsApp **sem** delegação ao KernelBot via `kernelProvider`.

---

## O que existe em `feature/kernel-orbit-v1-hardening`?

**Classificação:** CURRENT (workspace) / IMPLEMENTED / BRANCH-SPECIFIC.

| Artefacto | Na feature? | Evidência |
|-----------|-------------|-----------|
| `src/providers/kernelProvider.js` | **Sim** | Presente no HEAD |
| `src/openai.js` → `kernelProvider.chat()` | **Sim** | Fluxo principal de geração |
| Baileys 6.7.18 | **Sim** | `package.json` |
| HTTP interno `:8010` | **Sim** | `src/outbound/internalHttp.js` |
| OpenRouter no fluxo principal | **Não** | Código morto/legado no ficheiro; Kernel é autoritativo |

---

## Mapa de branches (observadas)

| Branch | Classificação | Nota |
|--------|---------------|------|
| `feature/kernel-orbit-v1-hardening` | **CURRENT (workspace)** / BRANCH-SPECIFIC | Par com KernelBot; contrato `/v1/chat` |
| `main` | HISTORICAL (relativamente à integração Kernel) | Sem `kernelProvider` |
| `feature/orbit-kernel-provider` | HISTORICAL / experimental | Evolução da integração |
| `feature/orbit-kernel-tracing` | EXPERIMENTAL | Traces |
| `refactor/wppconnect-to-baileys` | HISTORICAL | Migração transporte |
| `refactor/test-trigger-mode` | EXPERIMENTAL | Testes |

## Par KernelBot ↔ OrbitBot

Mesmo nome `feature/kernel-orbit-v1-hardening` em ambos repos — evidência de desenvolvimento paralelo. **Merge para `main`:** UNKNOWN.

## Implicação para agentes

1. `git branch --show-current` em `/home/gaab/Documentos/gitHub/OrbitBot` antes de editar.
2. Não assumir `kernelProvider` em `main`.
3. Contrato Orbit→Kernel = `POST /v1/chat` **só na feature** (ver [[orbitbot-kernel]]).
