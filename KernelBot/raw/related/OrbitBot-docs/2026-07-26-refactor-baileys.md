(Preservado) PRD — Refatoração OrbitBot (WPPConnect → Baileys)
(Preservado) PRD — Refatoração OrbitBot (WPPConnect → Baileys)

Fonte: /home/gaab/Documentos/gitHub/OrbitBot/docs/prd/2026-07-26-refactor-baileys.md

Conteúdo resumido (primeiras secções):

— Objetivo: migrar engine WhatsApp para `@whiskeysockets/baileys` e simplificar arquitetura (sem PluginSystem, sem Dashboard, sem MessageQueue).
— Persistência: SQLite com tabela `config` para parâmetros e histórico.
— Admin por `ADMIN_NUMBERS` (env); comandos `/ai`, `/backup`, `/historico`, `/reset` previstos.
— Métricas de sucesso e riscos listados no PRD.

Para o conteúdo completo, consulte a fonte preservada no repositório original.

