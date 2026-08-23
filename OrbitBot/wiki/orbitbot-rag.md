---
id: orbitbot-rag
tipo: arquitetura
status: atual
atualizado: 2026-08-23
---

# RAG e recuperação de conhecimento

## Evidência no ecossistema

O projeto KernelBot documenta explicitamente:
- BM25
- search
- retrieval
- grounding
- ContextRouter
- contexto institucional e temporal

## Como isso se encaixa

O OrbitBot envia a pergunta para o Kernel. O Kernel faz o trabalho de recuperar contexto relevante, montar o prompt e decidir qual parte do conhecimento usar antes de responder. Isso coloca o RAG fora do bot de WhatsApp e dentro do backend principal.

## Estado do ecossistema

- Confirmado: há RAG no KernelBot.
- Confirmado: o OrbitBot referencia e usa a API do Kernel como fonte de resposta.
- Inferência útil: a busca e o grounding são centrais para a arquitetura do ecossistema, enquanto o bot local mantém função de transporte e composição do canal.

## Relações

- [[orbitbot-kernelbot]]
- [[orbitbot-kernel]]
- [[orbitbot-memory]]
- [[orbitbot-ecosystem]]
