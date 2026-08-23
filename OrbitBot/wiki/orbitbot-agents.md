---
id: orbitbot-agents
tipo: arquitetura
status: atual
atualizado: 2026-08-23
---

# Agentes

OrbitBot **não** implementa um framework de agentes. É um processo Node que encaminha mensagens WhatsApp para uma API HTTP.

Chamar OrbitBot e KernelBot de "agentes em camadas" é metáfora. No código:

- OrbitBot = bot Baileys + HTTP client
- KernelBot = FastAPI + BM25 + LLM provider
- MegaBrain (`AGENTS/`, `CursorSKILLS/`) = tooling de desenvolvimento, **não** carregado neste repo

`ChatProvider` do Kernel pode usar Cursor SDK `agents.create()` como backend LLM. Isso não torna o OrbitBot um orquestrador multi-agent.
