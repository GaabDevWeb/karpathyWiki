---
id: gaabwiki-skill
tipo: conceito
status: atual
projeto: gaabwiki
dominio: agentology
escopo: meta
atualizado: 2026-08-23
confianca: alta
aliases:
  - Capability
  - Habilidade
  - SKILL.md
fontes:
  - /home/gaab/.agents/skills/wiki-carpaccio/SKILL.md
  - /home/gaab/Documentos/gitHub/KernelBot/.cursor/skills/
  - /home/gaab/Documentos/gitHub/CursorSKILLS/README.md
relacionados:
  - gaabwiki-agent
  - gaabwiki-memory
  - gaabwiki-rag
  - gaabwiki-security
tags:
  - gaabwiki-skill
  - capability
  - tooling
---

# Skill

> Skill, neste ecossistema, é quase sempre um **ficheiro de instruções para o agente de desenvolvimento** (`SKILL.md`), não uma capability runtime do bot.

## CURRENT

| Onde | O quê | Consumido por Orbit/Kernel em runtime? |
|------|-------|----------------------------------------|
| `~/.agents/skills/` (ex.: wiki-carpaccio) | Skills globais do utilizador | Não |
| `KernelBot/.cursor/skills/` | `production-deploy-readiness`, `pre-publish-cleanup` | Não |
| `AGENTS/`, `CursorSKILLS/` | catálogo MegaBrain | Não |
| OrbitBot | nenhum `.cursor/skills` | — |

## NÃO implementado

- Skill registry na API Kernel.
- Tools/skills invocáveis pelo utilizador WhatsApp (além de comandos admin do OrbitBot: `/ai`, `/backup`, `/historico`, `/reset` — isto são **comandos**, não skills Cursor).

## Política desta wiki

Documentar skills de desenvolvimento só quando afectarem o conhecimento do projecto. Não inventar um "skill system" de produto.
