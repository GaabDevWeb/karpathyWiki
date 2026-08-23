---
id: orbitbot-current-state
tipo: estado
status: atual
atualizado: 2026-08-23
---

# Estado atual

Repo: `/home/gaab/Documentos/gitHub/OrbitBot`.  
Branch: `feature/kernel-orbit-v1-hardening`.

## O que existe (CURRENT)

- Assistente WhatsApp Node + Baileys (`app.js` → `src/bot.js`).
- Trigger `@orbit` / menção (`src/mentionTrigger.js`).
- 1:1: `src/core/messageHandler.js`. Grupos: `src/groups/groupHandler.js` (não `src/groupHandler.js`).
- IA: `src/openai.js` → `src/providers/kernelProvider.js` → `POST /v1/chat`.
- `historico` **ignorado** no caminho Kernel (SSOT = Kernel).
- SQLite local para clientes/histórico/config (`database/`) — operacional/admin.
- Buffer de grupo em RAM — **não** enviado ao Kernel.
- HTTP interno `src/outbound/internalHttp.js` (`127.0.0.1:8010`).
- Traces fire-and-forget `src/traceClient.js`.
- Reset `/reset` `/nova` via `src/kernelContext.js`.

## OpenRouter

`src/providers/openrouterProvider.js` existe. **Nenhum** `require` no fluxo actual (`src/openai.js` só importa `kernelProvider`). Isto é **código morto**, não fallback activo.

## README

Desactualizado (OpenRouter/DeepSeek como cérebro). Não foi alterado (escrita só na GaabWiki).

## NÃO CONFIRMADO

- WhatsApp E2E (pasta `auth/` ausente no checkout auditado).
- Kernel+Orbit em produção.
- `npm test` verde com `node_modules` instalado (execução sem deps falhou).
