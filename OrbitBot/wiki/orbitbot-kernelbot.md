---
id: orbitbot-kernelbot
tipo: projeto
status: atual
atualizado: 2026-08-23
---

# KernelBot

## Identidade

Repositório: /home/gaab/Documentos/gitHub/KernelBot  
Tipo: backend de busca contextual / RAG / API de chat  
Stack: FastAPI, Uvicorn, PyMySQL, BM25, OpenRouter/Cursor, contexto em camadas  

## Papel principal

O KernelBot é o backend de conhecimento, identificado em README como “Kernel HTTP reutilizável para busca BM25 e conversa RAG sobre aulas indexadas”. Esse projeto representa a camada lógica e semântica do ecossistema muito mais do que um bot de chat simples.

## Componentes importantes

- FastAPI + routes HTTP
- BM25 e RAG
- `ContextRouter` e Context Architecture
- política de grounding e formulários de instrução
- catálogo curricular / contexto institucional
- observabilidade por traces

## Relações com o ecossistema

- Fornece API para o OrbitBot
- Centraliza busca, memória contextual e grounding
- Assegura a fonte oficial do contexto em comparação com memória local do cliente
- Possui suporte para deploy, staging, observabilidade e integração com catálogo

## Status

- Fato confirmado: KernelBot existe e foi identificado como repositório separado.
- Fato confirmado: há integração real com OrbitBot por HTTP.
- Fato confirmado: no projeto KernelBot há intenção de context router e otimização de tokens.
- Inferência útil: ele funciona como o cérebro de um ecossistema de agentes, não apenas como um modelo de resposta isolado.
