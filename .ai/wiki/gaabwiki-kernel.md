---
id: gaabwiki-kernel
tipo: conceito
status: atual
projeto: gaabwiki
dominio: architecture
escopo: meta
atualizado: 2026-08-23
confianca: alta
aliases:
  - Kernel layer
  - Camada cognitiva
  - Kernel API
fontes:
  - /home/gaab/Documentos/gitHub/KernelBot/kernel/
  - /home/gaab/Documentos/gitHub/KernelBot/README.md
  - KernelBot/index.md
relacionados:
  - gaabwiki-kernelbot
  - gaabwiki-orbit
  - gaabwiki-rag
  - gaabwiki-memory
  - gaabwiki-security
tags:
  - gaabwiki-kernel
  - architecture
  - context
---

# Kernel

> O Kernel é o **conceito** da camada cognitiva. A implementação CURRENT vive no repo KernelBot, pasta `kernel/`. Não existe repo `/home/gaab/Documentos/gitHub/Kernel`.

## Definição

No código, `kernel/` agrupa: orchestrator, rag, memory, knowledge, context, providers, policies, trace, comms, users, schemas, disciplines, inspect, tools.

O README do KernelBot chama o produto de **"Kernel API"**: HTTP reutilizável para busca BM25 e conversa RAG sobre aulas indexadas.

## Estado atual (CURRENT)

- Implementado como biblioteca de domínio **dentro** de KernelBot.
- Entrypoint HTTP: FastAPI em `main.py` + `app/factory.py`, porta **8001**.
- Pastas `engine/` e `core/` no repo estão **vazias** (código migrado; leftovers em testes/docs).
- Branding histórico "ACL — Agente de Contexto Local" sobrevive em `KernelBot.wiki` e variáveis `ACL_*`.

## Relação com Orbit

Orbit (conceito / OrbitBot) é o canal. Kernel processa. Comunicação: HTTP `POST /v1/chat`, não import de código partilhado.

## Relação com projectos

- [[gaabwiki-kernelbot]]: o repositório que contém `kernel/`.
- [[gaabwiki-orbitbot]]: o único adapter WhatsApp verificado que consome a API.
