# OrbitBot

Assistente pessoal via WhatsApp (1:1) com IA (OpenRouter/DeepSeek) e SQLite.

Stack actual: Node.js · @whiskeysockets/baileys · SQLite · pino · OpenRouter

## Sumário do README

- Projeto principal: OrbitBot
- Entrada principal: WhatsApp via Baileys
- Persistência: SQLite
- IA: OpenRouter + fallback; mais tarde KernelProvider HTTP
- Prompt: `prompts/SYSTEM.md`
- Comandos admin: `/ai`, `/backup`, `/historico`, `/reset`

## Arquitetura resumida

```text
WhatsApp → Baileys → grupos (@orbit/menção) | 1:1 (@orbit)
                         ↓                        ↓
                   buffer RAM 40            mutex → SQLite
                         ↓                        ↓
                    OpenRouter ←────────────── openai.js
                         ↓
              markdownToWhatsapp → sendMessage
```

## Conformidade com o ecossistema

O README documenta o OrbitBot como um cliente de canal, não como o núcleo do sistema. O projeto possui evolução explícita para delegar a IA a um Kernel: `Orbit → KernelProvider → POST /v1/chat`.

Fontes de origem: /home/gaab/Documentos/gitHub/OrbitBot/README.md
