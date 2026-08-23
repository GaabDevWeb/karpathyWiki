---
id: orbitbot-identity
tipo: projeto
status: atual
atualizado: 2026-08-23
---

# OrbitBot

## Identidade

Repositório: /home/gaab/Documentos/gitHub/OrbitBot  
Tipo: bot WhatsApp / client de canal  
Stack: Node.js, Baileys, SQLite, pino, OpenRouter, KernelProvider  

## Papel principal

O OrbitBot recebe mensagens do WhatsApp, filtra triggers, valida comandos, reagrupa contexto local e envia requisições ao Kernel. Ele funciona como uma camada de fronteira, não como o único motor cognitivo do sistema.

## Componentes importantes

- `src/bot.js`: listener principal de mensagens
- `src/providers/kernelProvider.js`: cliente HTTP do Kernel
- `src/kernelContext.js`: reset de contexto e seleção de comandos
- `src/traceClient.js`: observabilidade e traces
- `database/`: persistência local
- `prompts/SYSTEM.md`: identidade do bot

## Relações com o ecossistema

- Depende do Kernel para resposta principal
- Usa Baileys como camada de transporte
- Guarda memória local e backups, mas não é a única fonte de memória
- Mantém compatibilidade com OpenRouter como legado ou fallback

## Status de integração

- Fato: existe integração direta com API do Kernel.
- Fato: e.g. `docs/KERNEL-INTEGRATION.md` é projetado para essa relação.
- Inferência: OrbitBot é o nó de entrada do sistema e o Kernel é o nó de contexto/decisão.
