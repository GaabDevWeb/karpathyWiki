---
id: orbitbot-kernel
tipo: arquitetura
status: atual
atualizado: 2026-08-23
---

# Kernel

## Papel conceitual

O Kernel é a camada de processamento de contexto, recolha, decisão e grounding. O projeto KernelBot confirma esta leitura: FastAPI, BM25, MySQL, RAG, context router e observabilidade estão concentrados no backend.

## Funções observadas

- API HTTP de chat: `POST /chat`
- API de busca: `POST /search`
- contexto institucional, temporal e calendário
- grounding / RAG / BM25
- integração com memória e transcript
- observabilidade por traces

## Como se relaciona com Orbit

O contrato documentado define que OrbitBot envia a pergunta para o Kernel e recebe uma resposta estruturada. A documentação do repositório OrbitBot chama a este fluxo de “Orbit → Kernel (ChannelContext)”.

## Estado atual

- Confirmado: existe um backend Kernel separado em outro repositório.
- Confirmado: há integração explícita e branches compartilhadas (`feature/kernel-orbit-*`).
- Confirmado: Kernel está associado a context routing e conhecimento recuperável.
- Não confirmado: se o termo “Kernel” representa um produto único, um framework ou uma convenção de arquitetura mais ampla.

## Relações

- [[orbitbot-kernelbot]]
- [[orbitbot-identity]]
- [[orbitbot-rag]]
- [[orbitbot-memory]]
- [[orbitbot-ecosystem]]
