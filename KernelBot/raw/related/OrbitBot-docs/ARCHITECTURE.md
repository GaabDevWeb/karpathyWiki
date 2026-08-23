(Preservado) ARCHITECTURE.md — OrbitBot

Fonte: /home/gaab/Documentos/gitHub/OrbitBot/docs/ARCHITECTURE.md

Resumo:
- Bot WhatsApp 1:1 usando `@whiskeysockets/baileys`.
- Persistência SQLite para 1:1 (`clientes`, `historico`, `config`).
- Mutex por JID para serializar chamadas IA; buffer RAM para grupos (max 40 msgs).
- Removidos: MessageQueue, PluginSystem, Dashboard.
- Stack: Node.js ≥18, Baileys, OpenRouter, pino, sqlite3.
