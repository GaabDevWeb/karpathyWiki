---
id: kernelbot-roadmap
tipo: planejamento
status: atual
atualizado: 2026-08-23
---

# Roadmap e planejamento evidenciado

## Planejamento explícito

Há evidência de trabalho orientado a:

- deploy e produção pública (`chore/railway-first-deploy`)
- melhorias de UI (`main`, commits recentes de refactor)
- suporte a diferentes providers (`feat/cursor-provider`)
- gestão de histórico de conversa (`feature/chat-history-api`)
- catalog sync / integração ISS (`ACL_CATALOG_ENABLED`, `/health/catalog`, docs de integração)

## Planejamento inferido a partir do código

Os módulos e variáveis sugerem linhas de evolução que o projeto já considera:

- reforço do catálogo curricular e drift detection
- refinamento de BM25 e políticas de retrieval
- suporte a mais provedores de LLM
- melhoria da experiência de diálogo e da interface
- operações mais robustas de staging e produção

## Planejado e não necessariamente integrado

Ramos experimentais como `webscraping_feature`, `internalPromptFeature` e `feat/continuous-generation` mostram workstreams de valor, mas não são, por si só, evidência de que todas as ideias estão ativas no estado principal.

## Regra da Wiki

Este documento não transforma inferência em fato; ele registra o que está documentado ou sugerido no histórico e no código. Quando não houver suporte direto, a página usa marcação de incerteza e não anuncia uma “estratégia oficial”.
