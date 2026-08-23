---
id: orbitbot-kernel
tipo: arquitetura
status: atual
projeto: orbitbot
dominio: architecture
escopo: projeto
atualizado: 2026-08-23
confianca: alta
fontes:
  - /home/gaab/Documentos/gitHub/OrbitBot/src/openai.js
  - /home/gaab/Documentos/gitHub/OrbitBot/src/providers/kernelProvider.js
relacionados:
  - orbitbot-branches
  - orbitbot-kernelbot
  - orbitbot-architecture
tags:
  - kernel
  - orbit
  - branch-provenance
---

# Kernel (conceito) — vista OrbitBot

> **Kernel** = camada cognitiva (no repo **KernelBot**, pacote `kernel/`). **OrbitBot não implementa Kernel** — delega via HTTP.

## Kernel ≠ KernelBot ≠ OrbitBot

| Entidade | O que é |
|----------|---------|
| Kernel | Conceito / processamento (RAG, LLM, transcript SSOT na feature) |
| KernelBot | Repositório Python que hospeda `kernel/` |
| OrbitBot | Adapter WhatsApp Node; **canal**, não cognição |

## Contrato Orbit → Kernel (feature branch)

**Classificação:** IMPLEMENTED / BRANCH-SPECIFIC  
**Branch OrbitBot + KernelBot:** `feature/kernel-orbit-v1-hardening`

```text
OrbitBot
  → src/openai.js
  → kernelProvider.chat()
  → POST {KERNEL_API_URL}/v1/chat
  → KernelBot (api/routes_v1.py)
  → resposta JSON { answer }
```

Evidência: `src/openai.js` require `kernelProvider`; comentário confirma cache OpenRouter **não** usado no caminho Kernel.

## Endpoints KernelBot

| Endpoint | Classificação | Uso OrbitBot |
|----------|---------------|--------------|
| **`POST /v1/chat`** | **Contrato Orbit (feature)** | **Principal** — `kernelProvider.js` |
| `POST /chat` | LEGACY | API legada; **não** é o fluxo Orbit na feature auditada |
| `POST /search` | LEGACY / direct | Busca BM25; OrbitBot **não** usa como contrato de chat |

## Em `OrbitBot/main` (HISTORICAL)

- **Sem** `src/providers/kernelProvider.js`
- Fluxo via OpenRouter + cache local (`src/openai.js` legado)
- Ver [[orbitbot-branches]]

## Estado

- Backend Kernel separado (repo KernelBot): **confirmado**
- Integração HTTP na feature: **confirmada**
- Merge para `main`: **UNKNOWN**
- Kernel como "produto" vs "convenção": conceito arquitectural — ver [[gaabwiki-kernel]]

## Relações

- [[orbitbot-kernelbot]] — repo do backend
- [[orbitbot-identity]] — este projecto (OrbitBot)
- [[orbitbot-rag]] — OrbitBot **não** faz RAG
- [[orbitbot-memory]] — SQLite local; transcript SSOT no Kernel (feature)
