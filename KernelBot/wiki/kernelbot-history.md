---
id: kernelbot-history
tipo: historico
status: atual
projeto: kernelbot
dominio: evolution
escopo: projeto
atualizado: 2026-08-23
confianca: alta
relacionados:
  - kernelbot-branches
  - kernelbot-current-state
tags:
  - history
---

# Histórico do projeto em alto nível

## Fase 1 — base funcional e protótipo

A base do projeto foi estruturada em torno de um chatbot web simples com FastAPI, frontend JS e modelo de inteligência artificial orientado ao conteúdo curricular. Os primeiros commits indicam a criação da aplicação e a consolidação do fluxo de chat.

## Fase 2 — adoção de BM25 e MySQL

Os commits e a documentação mostram que a camada de RAG foi evoluindo em direção ao uso de MySQL como fonte principal de conhecimento. Essa etapa é central no projeto: o corpus de aulas é carregado e indexado por chunks para busca léxica.

## Fase 3 — refinamento de retrieval e grounding

O projeto passou a incorporar políticas de gating e regras de grounding, com decisões como `insufficient_context`, `underspecified_query`, `ambiguous_retrieval` e pós-geração advisory. Isso reforça a orientação do sistema para respostas fundamentadas, e não para geração livre de contexto.

## Fase 4 — deploy, staging e operações

Os ramos `chore/railway-first-deploy` e `chore/repo-cleanup-deploy` mostram a preocupação com deploy público, scripts de staging, Docker e preparação para produção. Há uma clara diferenciação entre ambiente de desenvolvimento, staging e produção.

## Fase 5 — UX, sessão e provider

As branches `feat/cursor-provider`, `feature/chat-history-api`, `feat/continuous-generation` e `internalPromptFeature` sugerem refinamentos de UX, gestão de histórico, provider de LLM e comportamento de pergunta e pin. Esses ramos mostram que a aplicação passou por várias melhorias sem necessariamente substituir `main`.

## Fase 6 — branches experimentais

Ramos como `webscraping_feature` e `internalPromptFeature` parecem estar ligados a experimentação específica e não ao núcleo estável da aplicação. O projeto preserva essas linhas como histórico.

## Fase 7 — True Kernel e integração Orbit (2026)

**Classificação:** BRANCH-SPECIFIC (`feature/kernel-orbit-v1-hardening`).

- Migração `engine/` → `kernel/`
- API v1 (`POST /v1/chat`) para adapters de canal
- Remoção do frontend web público no HEAD da feature
- Outbound WhatsApp via HTTP interno

**Não confundir com `main`:** em `main`, a linha de entrega ainda é `engine/` + `frontend/` sem contrato v1. Ver [[kernelbot-branches]].

## Conclusão histórica

O KernelBot não é um projeto “monolítico” de uma única vibração; ele evoluiu por ciclos de:

1. protótipo base
2. reforço do BM25/MySQL
3. hardening do grounding e retrieval
4. deploy e staging
5. refinamentos de UX e provider
6. experimentação em ramos paralelos
7. True Kernel + integração Orbit (branch-specific; ver [[kernelbot-branches]])

Esse histórico distingue estado **documentado na feature branch** de legado em `main` e de esforços experimentais.
