---
id: orbitbot-components
tipo: componentes
status: atual
atualizado: 2026-08-23
---

# Componentes compartilhados e reutilizáveis

## Componentes observados

### 1. Provider HTTP

- Origem: OrbitBot (`src/providers/kernelProvider.js`)
- Uso: comunicação com Kernel API
- Estado: funcional em integração explícita

### 2. Trace/event observability

- Origem: OrbitBot (`src/traceClient.js`)
- Uso: correlacionar eventos e respostas
- Estado: funcional; componente de integração entre projetos

### 3. ContextRouter / context layering

- Origem: KernelBot (`docs/CONTEXT-ARCHITECTURE.md`)
- Uso: decidir FAST / NORMAL / DEEP e carregar camadas específicas
- Estado: documentado e provavelmente reutilizável em outros clientes

### 4. RAG / BM25

- Origem: KernelBot
- Uso: busca e grounding com Fonte e evidência
- Estado: núcleo do conhecimento do ecossistema

### 5. Personificação / prompt único

- Origem: OrbitBot (`prompts/SYSTEM.md`)
- Uso: definir persona e comportamento local
- Estado: componente de adaptação e boa UX do cliente

## Reutilização esperada

- O KernelBot parece ser o maior repositório de componentes reutilizáveis em comunicação/contexto.
- O OrbitBot parece ser o maior repositório de componentes reutilizáveis em transporte de canal, trigger e integração com redes sociais.

## Limite

Não se pode afirmar que todos os módulos de um projeto são compartilhados automaticamente. O que se observa é uma relação de compatibilidade de interfaces, não uma fusão estrutural.
