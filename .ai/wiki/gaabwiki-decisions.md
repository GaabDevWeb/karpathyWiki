---
id: gaabwiki-decisions
tipo: decisao
status: atual
projeto: gaabwiki
dominio: knowledge-governance
escopo: meta
atualizado: 2026-08-23
confianca: alta
aliases:
  - Decisões da GaabWiki
  - Governance da wiki
fontes:
  - .ai/CLAUDE.md
  - .ai/log.md
  - README.md
relacionados:
  - gaabwiki-overview
  - gaabwiki-architecture
  - gaabwiki-auditoria
tags:
  - gaabwiki
  - decisions
  - governance
---

# Decisões da GaabWiki

## Decisão central

A GaabWiki deve continuar sendo uma memória documental em Markdown + Git + wikilinks, sem uma infraestrutura de retrieval dentro do repositório.

## Contexto

O objetivo principal da meta-wiki é reduzir a redescoberta de contexto em um ecossistema de múltiplos projetos e agentes. Isso exige coerência sem sobrecarregar o corpus com infraestrutura que ainda não é necessária.

## Motivo

- favorece manutenção humana;
- funciona bem em Obsidian e Git;
- preserva rastreabilidade e transparência;
- prepara o corpus para futuras camadas de indexação sem reescrever a base.

## Alternativas consideradas

- RAG incorporado imediatamente: descartado porque cria infraestrutura antes da base documental estar madura.
- Wiki sem schema ou ids: descartado porque prejudica futura recuperação e consistência.
- Estrutura rígida com centenas de subpastas: descartado porque vai contra o princípio de crescimento orgânico.

## Consequências

- a meta-wiki é mais fácil de manter;
- cada página precisa ter identidade, status e fontes;
- o corpus futuro pode evoluir para BM25, embeddings e graph retrieval sem reconstrução radical.

## Decisão forense V1 (2026-08-23)

A wiki canónica documenta o estado verificado nas branches `feature/kernel-orbit-v1-hardening`, não `main`, até haver merge confirmado.

Motivo: o código local de KernelBot e OrbitBot está nessas branches; README/`main` divergem.

Consequência: qualquer agente que leia só README ou só `main` remota recebe um mapa errado.

## Decisão: não corrigir código a partir da wiki

Bugs encontrados (`bootstrap_catalog_state` sem import; `/ai stats` cache; testes `engine.*`) ficam em [[known-unknowns]] / known-issues. A wiki não é o sítio de patch.

## Status

- atual

## Fontes

- [.ai/CLAUDE.md](../CLAUDE.md)
- [.ai/log.md](../log.md)
- [README.md](../../README.md)