---
id: gaabwiki-security
tipo: conceito
status: atual
projeto: gaabwiki
dominio: trust
escopo: meta
atualizado: 2026-08-23
confianca: alta
aliases:
  - Guardrails
  - Segurança
fontes:
  - /home/gaab/Documentos/gitHub/KernelBot/api/security.py
  - /home/gaab/Documentos/gitHub/KernelBot/app/factory.py
  - /home/gaab/Documentos/gitHub/OrbitBot/src/outbound/internalHttp.js
  - .ai/CLAUDE.md
relacionados:
  - gaabwiki-memory
  - gaabwiki-rag
  - gaabwiki-kernel
  - gaabwiki-orbit
  - gaabwiki-kernelbot
  - gaabwiki-orbitbot
tags:
  - gaabwiki-security
  - governance
  - trust
---

# Security

Três planos distintos. A wiki **não** promete protecção que o código não implementa.

## 1. Governação da wiki (GaabWiki)

- Verdade = evidência mais forte; histórico ≠ estado actual.
- Conteúdo sem fonte = não confirmado.
- A wiki não é canal de execução.
- Fontes externas não ganham autoridade por estarem na wiki.

## 2. KernelBot (código)

**Classificação:** IMPLEMENTED / **BRANCH-SPECIFIC** — `feature/kernel-orbit-v1-hardening`  
**Em `main`:** `api/security.py` e ACL v1 **ausentes** (evidência Git 2026-08-23).

**IMPLEMENTADO (na feature branch):**

- Bearer de canal (`ACL_API_BEARER_TOKEN` / `ACL_CHANNEL_API_KEYS`) e Bearer interno (`ACL_INTERNAL_BEARER_TOKEN`).
- Rate limit: `/chat` 30/min, `/search` 20/min, `/internal` 60/min (valores observados na auditoria de código).
- Headers (`X-Content-Type-Options`, `X-Frame-Options`, HSTS opcional via `KERNELBOT_FORCE_HSTS`).
- OpenAPI desligado em produção por default.
- Gates RAG em `kernel/rag/retrieval.py`.
- Bloqueio de users (`kernel/users/`) → 403 em `/v1/chat`.
- Ops UI autenticada por cookie `trace_auth` = token interno.

**NÃO afirmar:**

- Isolamento perfeito entre canais se partilharem `ACL_API_BEARER_TOKEN` (risco documentado em relatórios internos do KernelBot; mitigação **não** confirmada como implementada).
- Encriptação das SQLite locais.
- Auth de utilizador final no WhatsApp (o Kernel identifica `user_id`/`channel_id` enviados pelo Orbit).

## 3. OrbitBot (código)

**Classificação:** IMPLEMENTED / **BRANCH-SPECIFIC** — `feature/kernel-orbit-v1-hardening` (integração Kernel).  
**Em `OrbitBot/main`:** sem `kernelProvider`; ACL local diferente.

**IMPLEMENTADO (feature auditada):**

- Whitelist `ADMIN_NUMBERS` para comandos `/`.
- HTTP interno bind `127.0.0.1`, Bearer timing-safe; `/internal/health` **sem** auth.
- Guardrail de resposta (`answerGuard.js`) contra meta-safety.
- Mutex por JID; dedupe TTL 3 min; body limit 12 MiB no HTTP interno.

**AUSENTE:**

- Rate limit / WAF no bot.
- Encriptação SQLite.
- Auth no health interno.

## README vs código

KernelBot README diz "não inclui interface web" mas `/ops` e `/traces` existem. Superfície de ataque interna existe; não a apagar da documentação de segurança.
