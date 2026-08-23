---
id: orbitbot-decisions
tipo: decisoes
status: atual
atualizado: 2026-08-23
---

# Decisões arquiteturais relevantes

## Decisão 1: OrbitBot passa a usar Kernel como resposta principal

### Problema

O bot precisaria de um backend de contexto mais robusto do que o OpenRouter isolado.

### Decisão

A arquitetura evolui para `OrbitBot -> KernelProvider -> POST /v1/chat -> Kernel`.

### Motivo

A documentação do projeto e o histórico de desenvolvimento explicitam que o Kernel passa a ser a fonte de verdade de transcript, pin, RAG e contexto.

### Impacto no ecossistema

O canal deixa de ser o centro da cognição e passa a ser a camada de entrada/saída.

### Status

Atual / integrada

---

## Decisão 2: KernelBot concentra RAG, BM25 e contexto em camadas

### Problema

O ecossistema precisava de uma camada de busca e grounding mais robusta, separada do cliente de canal.

### Decisão

KernelBot implementa API de search/chat com BM25, traps de grounding, routing de contexto e integração com infraestrutura de dados.

### Impacto

O conhecimento e o problema de recuperação deixam de ficar no cliente e passam ao backend.

### Status

Atual / confirmado

---

## Decisão 3: manter memória local e memória de kernel separadas

### Problema

Sem separar tipos de memória, o sistema teria risco de misturar histórico operacional, contexto e conhecimento oficial.

### Decisão

O OrbitBot preserva SQLite local e buffer de grupo; o KernelBot centraliza contextos e buscas.

### Impacto

Melhor clareza de responsabilidade e menor acoplamento entre canais e conhecimento.

### Status

Atual / consistente

---

## Decisão 4: integração via branches e contratos HTTP

### Problema

Precisava existir um contrato explícito entre projetos sem acoplamento total.

### Decisão

O sofá de integração foi construído por HTTP, tokens, traces e payloads de chat com `user_id`, `channel_id`, `message` e `reset_context`.

### Impacto

Há um bom nível de interoperabilidade entre cliente e backend e um caminho claro para reutilização.

### Status

Atual / detectado
