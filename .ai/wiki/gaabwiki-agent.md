---
id: gaabwiki-agent
tipo: conceito
status: atual
projeto: gaabwiki
dominio: agentology
escopo: meta
atualizado: 2026-08-23
confianca: media
aliases:
  - Agent system
  - Agente
fontes:
  - /home/gaab/Documentos/gitHub/KernelBot/kernel/providers/chat_provider.py
  - /home/gaab/Documentos/gitHub/AGENTS/Cursor/GLOBAL-SETUP.md
  - /home/gaab/Documentos/gitHub/CursorSKILLS/README.md
relacionados:
  - gaabwiki-skill
  - gaabwiki-memory
  - gaabwiki-rag
  - gaabwiki-security
tags:
  - gaabwiki-agent
  - orchestration
  - context
---

# Agent

> "Agent" **não** é um projecto nem um runtime único no ecossistema de chat.

## O que existe (CURRENT)

### 1. Tooling de desenvolvimento (MegaBrain)

Repos `AGENTS/` (local, sem remote) e `CursorSKILLS/` (publicado). Contêm agentes Markdown, commands, hooks e um orchestrator TypeScript para o Cursor. **Não** são carregados pelo OrbitBot nem pelo KernelBot em runtime de WhatsApp.

### 2. Provider LLM no KernelBot

`kernel/providers/chat_provider.py` pode chamar `cursor_sdk.AsyncClient.agents.create()`. Isto é um **backend de geração**, equivalente funcional a OpenRouter — não um sistema multi-agent com tools/skills no produto.

### 3. Palavra em documentação

Aparece em wikis e planos. Sem evidência de framework de agentes no path WhatsApp → Kernel.

## O que não existe (confirmado por ausência)

- Runtime multi-agent no OrbitBot (`src/` sem agent framework).
- `AGENTS.md` / `CLAUDE.md` na raiz do KernelBot ou do OrbitBot.
- Catálogo de agentes executável exposto pela API `/v1`.

## Relação com Skills

[[gaabwiki-skill]] no sentido Cursor = ficheiro de instruções para o agente de desenvolvimento.  
Não há skills runtime no bot.

**Confiança:** média — AGENTS/CursorSKILLS não foram auditados módulo a módulo; só estrutura e ausência de ligação no código de chat.
