---
id: orbitbot-architecture
tipo: arquitetura
status: atual
atualizado: 2026-08-23
---

# Arquitetura

```text
WhatsApp
  → Baileys (`src/bot.js`)
  → trigger / dedupe / mutex / admin
  → kernelProvider (`POST /v1/chat`)
  → KernelBot BM25 + LLM
  → answer
  → whatsappFormatter → sock.sendMessage
```

Inbound proactivo (código existe; produção NÃO CONFIRMADA):

```text
KernelBot outbound → ORBIT_INTERNAL_URL :8010 → internalHttp.js → WhatsApp
```

## Camadas

| Camada | Papel | Path |
|--------|-------|------|
| Canal | WhatsApp | `src/bot.js` |
| 1:1 / grupos | handlers | `src/core/messageHandler.js`, `src/groups/groupHandler.js` |
| Transporte IA | HTTP Kernel | `src/providers/kernelProvider.js` |
| Observabilidade | traces | `src/traceClient.js` |
| Persistência local | SQLite | `database/` |
| Outbound | HTTP interno | `src/outbound/` |

## Split

OrbitBot = transporte / filtros / admin.  
KernelBot = resposta, transcript, RAG.  
Não partilham código; só HTTP.

## Legado

OpenRouter **fora do fluxo**. Humanizer (`src/humanizer.js`) exigido em planos antigos — **ficheiro ausente**; envio é directo.
