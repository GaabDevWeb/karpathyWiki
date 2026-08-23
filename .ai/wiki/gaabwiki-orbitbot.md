---
id: gaabwiki-orbitbot
tipo: conceito
status: atual
projeto: gaabwiki
dominio: project-definition
escopo: meta
atualizado: 2026-08-23T14:00
confianca: alta
aliases:
  - OrbitBot
  - Orbit Bot
fontes:
  - /home/gaab/Documentos/gitHub/OrbitBot/src/openai.js
  - /home/gaab/Documentos/gitHub/OrbitBot/src/providers/kernelProvider.js
  - /home/gaab/Documentos/gitHub/OrbitBot/src/bot.js
  - /home/gaab/Documentos/gitHub/OrbitBot/README.md
  - OrbitBot/index.md
relacionados:
  - gaabwiki-orbit
  - gaabwiki-kernelbot
  - gaabwiki-security
tags:
  - gaabwiki-orbitbot
  - project
  - channel
---

# OrbitBot

> Cliente WhatsApp (Baileys) que delega IA ao Kernel via HTTP. Repo: `/home/gaab/Documentos/gitHub/OrbitBot`.

## Estado atual (auditado 2026-08-23)

| Aspecto | Evidência |
|---------|-----------|
| Branch auditada | `feature/kernel-orbit-v1-hardening` |
| Stack | Node ≥18, Baileys 6.7.18, SQLite, pino, axios |
| Fluxo IA | `src/openai.js` → `kernelProvider.chat()` → `POST /v1/chat` |
| OpenRouter | ficheiro `src/providers/openrouterProvider.js` **existe**; **não é importado** pelo fluxo actual — código morto, não fallback activo |
| Persistência local | SQLite (`database/`) — admin/backup; Kernel ignora o `historico` enviado |
| Buffer de grupo | RAM, observabilidade; **não** entra no prompt do Kernel |
| HTTP interno | `src/outbound/internalHttp.js` em 127.0.0.1:8010 |
| CI | **ausente** (sem `.github/workflows`) |
| `.cursor/` / `AGENTS.md` | **ausentes** neste repo |

## Relação com KernelBot

```text
WhatsApp → Baileys → OrbitBot
       → POST {KERNEL_API_URL}/v1/chat
KernelBot → answer
OrbitBot → WhatsApp
```

Env: `KERNEL_API_URL` (default `http://127.0.0.1:8001`), `KERNEL_API_TOKEN` / `ACL_API_BEARER_TOKEN`, `ACL_INTERNAL_BEARER_TOKEN`, `ORBIT_INTERNAL_PORT=8010`.

## Divergência README vs código (CONFLITO)

O `README.md` do repo ainda diz: assistente WhatsApp com **OpenRouter/DeepSeek**. O código da branch auditada usa **apenas** Kernel HTTP. Tratar README como **histórico/desatualizado**. Esta wiki não altera o README do repo (regra: só escrever na GaabWiki).

## Bugs / riscos observados no código (não corrigidos)

- `/ai stats` referencia `systemStats.cache.size` mas `getSystemStats()` não devolve `cache` — crash provável no comando admin.
- `core/cache.js` e `core/retry.js` sem `require()` no runtime.
- Produção conjunta com Kernel: **NÃO CONFIRMADA**.

## Proveniência por branch (Git, 2026-08-23)

| Classificação | Branch | Artefactos |
|---------------|--------|------------|
| **IMPLEMENTED / BRANCH-SPECIFIC** | `feature/kernel-orbit-v1-hardening` | `kernelProvider.js`, Baileys, `@orbit`, fluxo `openai.js` → `POST /v1/chat` |
| **CURRENT-de-`main`** | `OrbitBot/main` | **Sem** `src/providers/kernelProvider.js`; OpenRouter legado |
| **HISTORICAL** | ramos antigos | Venom / WPPConnect; OpenRouter como cérebro; dashboard HTTP :3000 |
| **POC** | EchoRoute | experimental |
| **UNKNOWN** | merge / produção | **UNKNOWN** |
