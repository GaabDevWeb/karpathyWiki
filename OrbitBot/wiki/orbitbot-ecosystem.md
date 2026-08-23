---
id: orbitbot-ecosystem
tipo: ecossistema
status: atual
atualizado: 2026-08-23
---

# Ecossistema Orbit / Kernel

## Visão geral

O ecossistema identificado é composto por um conjunto de projetos e componentes em torno de inteligência contextual, agentes e recuperação de conhecimento.

### Relações confirmadas

```text
OrbitBot
 ├── utiliza → Kernel API
 ├── compartilha → trace/event observability
 ├── depende → Baileys / WhatsApp
 ├── preserva → SQLite local
 └── integra → prompts e workflow de admin

KernelBot
 ├── fornece → API de chat / search / grounding
 ├── implementa → BM25 + RAG
 ├── expõe → contexto em camadas
 ├── recebe → integrações por contratualização de HTTP
 └── relaciona-se → OrbitBot como cliente principal
```

## Categoria funcional

### Orbit

O conceito de Orbit parece corresponder a um nome de camada/identidade/cliente que encapsula o bot de conversa e a interface com o usuário. No projeto OrbitBot, o próprio bot se apresenta como `@orbit` e o nome “Orbit” é usado como identidade de produto. Há evidência de que o nome evoluiu de uma identidade de bot para um referencial arquitetural maior.

### Kernel

O Kernel representa a camada de processamento, contexto, busca e grounding. O repositório KernelBot documenta explicitamente FastAPI, BM25, RAG, API, contexto em camadas e observabilidade. Isso o coloca como a camada cognitiva, não como um canal de comunicação.

### Relação entre Orbit e Kernel

A relação mais bem sustentada é: OrbitBot é a interface + transporte; KernelBot é o cérebro + contexto.

## Estado da relação

- Direta: confirmada.
- Indireta: a forma como os demais projetos e skills se encaixam ainda depende de mais evidência.
- Compartilhado: prompts, memory, contracts, observability e arquitetura de trace.
- Inferida: alguns conceitos de “Orbit” podem estar sendo usados como nome de produto, arquitetura ou identidade sem necessariamente ser um repositório distincto.

## Componentes observados no conjunto

- Agentes: OrbitBot, KernelBot, possíveis orquestradores e workflows avançados
- Skills: catálogo/skills/documentação no ambiente local
- Memory: sessão, projeto, persistente, cache, knowledge base
- RAG: BM25, retrieval, grounding, transcript, index
- Segurança: ACL, tokens, guardrails e políticas de segurança
- Infra: MySQL, SQLite, Docker, scripts de staging, deploy e API HTTP

## Conclusão

O ecossistema mais plausível é um conjunto em camadas e em evolução constante, em que o envio ao usuário e o canal de comunicação ficam no Orbit, enquanto a inteligência contextual e o conhecimento ficam no Kernel.
