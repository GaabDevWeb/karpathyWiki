---
id: gaabwiki-terminology
tipo: conceito
status: atual
projeto: gaabwiki
dominio: terminology
escopo: meta
atualizado: 2026-08-23T14:00
confianca: alta
aliases:
  - Terminologia da GaabWiki
  - Canonical terms
fontes:
  - /home/gaab/Documentos/gitHub/KernelBot/README.md
  - /home/gaab/Documentos/gitHub/OrbitBot/package.json
  - /home/gaab/Documentos/gitHub/KernelBot/kernel/
relacionados:
  - gaabwiki-overview
  - gaabwiki-ecosystem
  - gaabwiki-projects
tags:
  - gaabwiki
  - terminology
  - concepts
---

# GaabWiki — Terminologia canônica

Regra: um nome de conceito **não** implica um repositório, um runtime ou uma feature implementada.

## Termos principais

### Kernel

**Conceito** da camada cognitiva (contexto, retrieval, grounding, LLM). **Kernel ≠ KernelBot.**  
**Não é** um repositório separado. Docs por vezes dizem "Kernel (ex-KernelBot)" — tratar como branding, não como split de repo.

| Classificação | Repo | Branch | Implementação |
|---------------|------|--------|---------------|
| **IMPLEMENTED / BRANCH-SPECIFIC** | KernelBot | `feature/kernel-orbit-v1-hardening` | Pacote `kernel/`, `/v1/chat`, BM25 |
| **CURRENT-de-`main`** | KernelBot | `main` | `engine/` + `frontend/`; **sem** `kernel/` |

### KernelBot

**Projecto/repositório** que **implementa** o Kernel (conceito). API HTTP FastAPI em `/home/gaab/Documentos/gitHub/KernelBot`. README actual intitula o produto **"Kernel API"** — branding do produto, não prova de que Kernel = KernelBot como entidades.

### Orbit

**Conceito** de canal/transporte. Também é o `name` npm (`"orbit"`) do OrbitBot e o trigger `@orbit`.  
**Não é** um repositório separado.

### OrbitBot

**Projecto** concreto: cliente WhatsApp (Baileys) em `/home/gaab/Documentos/gitHub/OrbitBot`. Adapter; não contém RAG.

### Agent

Palavra usada em três sítios distintos — **não misturar**:

1. **Tooling de desenvolvimento:** agentes Markdown + orchestrator em `AGENTS/` e `CursorSKILLS/` (MegaBrain).
2. **Provider LLM:** `cursor_sdk.AsyncClient.agents.create()` no KernelBot — um backend de geração, não um sistema multi-agent.
3. **Linguagem genérica** em docs. Sem runtime de "agent framework" no chat WhatsApp.

### Skill

**CURRENT em runtime Kernel/Orbit:** não existe catálogo de skills executável.  
**CURRENT em desenvolvimento:** ficheiros `SKILL.md` em `.cursor/skills/`, `~/.agents/skills/`, `AGENTS/`, `CursorSKILLS/`.  
A skill wiki-carpaccio governa **esta wiki**, não o bot.

### Memory

Família de mecanismos distintos — ver [[gaabwiki-memory]]. Nunca usar "memory" como se fosse um único store.

### RAG

No KernelBot: BM25 léxico **IMPLEMENTED / BRANCH-SPECIFIC** (`feature/kernel-orbit-v1-hardening`); em `main` legado sob `engine/`.  
Na GaabWiki: só preparação documental (corpus/schema).  
No OrbitBot: ausente (delega ao Kernel na feature branch).

### Security

Três planos: (1) ACL/auth no KernelBot, (2) admin/bind no OrbitBot, (3) governação da wiki. Ver [[gaabwiki-security]]. Não afirmar protecção que o código não tem.

## Aliases observados

| Variante | Uso canónico |
|----------|--------------|
| Kernel Bot / kernelbot | KernelBot (repo) |
| Kernel API | nome de produto no README do KernelBot |
| Orbit Bot / orbitbot / orbit (npm) | OrbitBot (repo) / conceito Orbit |
| ACL | nome histórico do KernelBot na wiki GitHub (`KernelBot.wiki`) |
| agent system / orchestrator | Agent (tooling MegaBrain), salvo evidência de runtime |
| memory / kb / transcript store | especificar o tipo |
| retrieval / grounding / search | RAG no KernelBot se for BM25; senão nomear o mecanismo |
