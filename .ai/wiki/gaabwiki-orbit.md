---
id: gaabwiki-orbit
tipo: conceito
status: atual
projeto: gaabwiki
dominio: architecture
escopo: meta
atualizado: 2026-08-23T14:00
confianca: alta
aliases:
  - Orbit layer
  - Camada de transporte
fontes:
  - /home/gaab/Documentos/gitHub/OrbitBot/package.json
  - /home/gaab/Documentos/gitHub/OrbitBot/src/mentionTrigger.js
  - OrbitBot/index.md
relacionados:
  - gaabwiki-orbitbot
  - gaabwiki-kernel
  - gaabwiki-security
tags:
  - gaabwiki-orbit
  - interface
  - transport
---

# Orbit

> Orbit é o **conceito** de canal/transporte. Não existe repo `/home/gaab/Documentos/gitHub/Orbit`.

## Definição

No código, Orbit aparece como:

- `name: "orbit"` em `OrbitBot/package.json`
- trigger de menção `@orbit` / `@~Orbit` (`src/mentionTrigger.js`)
- persona em `prompts/SYSTEM.md`
- `service` name `'orbit'` em traces (`src/traceClient.js`)

A materialização do conceito Orbit é o **OrbitBot** (repositório). Orbit ≠ OrbitBot.

## Estado actual — proveniência

| Classificação | Repo | Branch | Comportamento |
|---------------|------|--------|---------------|
| **IMPLEMENTED / BRANCH-SPECIFIC** | OrbitBot + KernelBot | `feature/kernel-orbit-v1-hardening` | OrbitBot (Baileys) delega IA via `kernelProvider` → `POST /v1/chat` |
| **CURRENT-de-`main`** | OrbitBot | `main` | **Sem** `kernelProvider.js`; fluxo OpenRouter/WPPConnect legado |
| **CURRENT-de-`main`** | KernelBot | `main` | **Sem** integração Orbit→Kernel consolidada (`engine/` + `frontend/`) |
| **UNKNOWN** | merge / produção | — | E2E WhatsApp+Kernel **NÃO CONFIRMADO** |

**CURRENT WORKSPACE / FEATURE BRANCH (auditado 2026-08-23):** OrbitBot recebe WhatsApp (Baileys), filtra, e delega IA ao Kernel HTTP. SQLite local é operacional (clientes/histórico/admin), **não** é o SSOT de transcript.

POC histórica relacionada: `EchoRoute` (README: "OrbitBot - POC"). Não é o OrbitBot da feature auditada.

## Relação com Kernel

- Orbit (conceito) canaliza; Kernel (conceito) processa.
- Contrato na feature: `KERNEL_API_URL` + `POST /v1/chat` — **só** em `feature/kernel-orbit-v1-hardening`.
- Outbound inverso: Kernel → `ORBIT_INTERNAL_URL` (:8010) — código na feature; produção **NÃO CONFIRMADA**.
