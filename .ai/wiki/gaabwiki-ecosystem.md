---
id: gaabwiki-ecosystem
tipo: ecossistema
status: atual
projeto: gaabwiki
dominio: ecosystem
escopo: meta
atualizado: 2026-08-23
confianca: alta
aliases:
  - Ecossistema da GaabWiki
  - Wiki ecosystem
fontes:
  - /home/gaab/Documentos/gitHub/OrbitBot/src/providers/kernelProvider.js
  - /home/gaab/Documentos/gitHub/OrbitBot/src/openai.js
  - /home/gaab/Documentos/gitHub/KernelBot/api/routes_v1.py
  - /home/gaab/Documentos/gitHub/KernelBot/adapters/whatsapp/outbound.py
relacionados:
  - gaabwiki-overview
  - gaabwiki-projects
  - gaabwiki-terminology
  - gaabwiki-kernelbot
  - gaabwiki-orbitbot
tags:
  - gaabwiki
  - ecosystem
  - gaabwiki-kernel
  - gaabwiki-orbit
---

# GaabWiki — Ecossistema e relações transversais

## Relação confirmada no código (CURRENT)

```text
WhatsApp
  → OrbitBot (Baileys, `src/bot.js`)
  → filtros (@orbit / menção / mutex / dedupe)
  → `src/openai.js` → `kernelProvider.chat()`
  → POST {KERNEL_API_URL}/v1/chat   default http://127.0.0.1:8001
  → KernelBot FastAPI (`api/routes_v1.py`)
  → BM25 + grounding + LLM
  → JSON { answer }
  → OrbitBot formata e envia no WhatsApp
```

Canal inverso (IMPLEMENTADO no código; uso em produção NÃO CONFIRMADO):

```text
KernelBot adapters/whatsapp/outbound.py
  → ORBIT_INTERNAL_URL  default http://127.0.0.1:8010
  → OrbitBot `src/outbound/internalHttp.js`
  → envio proactivo WhatsApp
```

Traces: OrbitBot `src/traceClient.js` → KernelBot `POST /internal/traces/events` (no-op se token vazio).

**Não existe** repositório `Kernel` nem `Orbit`. São conceitos + namespace/package name.

## O que cada peça é (e não é)

| Entidade | CURRENT | NÃO é |
|----------|---------|-------|
| KernelBot | API FastAPI Python, RAG BM25, LLM, Ops/Traces UI interna | repo chamado Kernel; frontend público de chat |
| OrbitBot | Cliente WhatsApp Node/Baileys; adapter HTTP | o cérebro; implementação de RAG |
| Kernel | Pacote `kernel/` dentro de KernelBot + conceito | projecto separado |
| Orbit | `package.json` name `orbit` + conceito de canal | projecto separado |
| GaabWiki | Memória Markdown | runtime, RAG, código de app |
| AGENTS / CursorSKILLS | Tooling Cursor/MegaBrain para desenvolvimento | runtime de chat |
| ISS | Site estático + pipeline VTT→lições; catálogo usado pelo Kernel | parte do KernelBot |
| EchoRoute | POC antiga de chatbot WhatsApp (README ainda diz "OrbitBot - POC") | OrbitBot actual |

## Conceitos transversais — onde existem de facto

- **Agents / Skills:** existem como skills Cursor e docs MegaBrain (`AGENTS/`, `CursorSKILLS/`, `~/.agents/skills`). **Não** há framework multi-agent no runtime KernelBot/OrbitBot. O `ChatProvider` do KernelBot pode usar `cursor_sdk.AsyncClient.agents.create()` como **provider LLM**, não como orquestrador de agentes.
- **Memory:** vários tipos distintos — ver [[gaabwiki-memory]].
- **RAG:** implementado só no KernelBot (BM25). Ausente no OrbitBot e na GaabWiki.
- **Security:** ACL Bearer + rate limit + headers no KernelBot; whitelist admin + bind 127.0.0.1 no OrbitBot; governação documental na GaabWiki. Ver [[gaabwiki-security]].

## Relações satélite (evidência parcial)

- ISS fornece conteúdo/catálogo que o KernelBot pode ingerir (`ACL_CATALOG_ENABLED`, `LessonCatalog`). Integração completa em `main` do ISS: ver wiki ISS ([[integrations]] lá).
- KernelBot-Deploy / z-KernelDeploy / KernelPlanner / KernelBot.wiki: artefactos de deploy, prompts e wiki GitHub — **não** são o SSOT do código API.
- Xray-Spec e Portifolio: projectos com identidade própria; **sem** dependência de runtime confirmada com Kernel/Orbit.

## Status

- relação Kernel↔Orbit no código: confirmada
- operação conjunta em produção: **NÃO CONFIRMADO**
- merge das feature branches em `main`: **NÃO CONFIRMADO**
