---
id: gaabwiki-readme
tipo: projeto
status: atual
projeto: gaabwiki
dominio: overview
escopo: meta
atualizado: 2026-08-23
confianca: alta
aliases:
  - README da GaabWiki
  - GaabWiki overview
fontes:
  - README.md
relacionados:
  - gaabwiki-overview
  - gaabwiki-index
tags:
  - gaabwiki
  - readme
---

# GaabWiki

## Visão geral

A GaabWiki é a camada de memória persistente do ecossistema documental do repositório. Ela reúne o conhecimento derivado dos projetos locais em um único mapa navegável, com foco em arquitetura, histórico, decisões, fontes, relações e preparação para futura indexação sem implementação de RAG.

## Objetivo

A Wiki funciona como um sistema de conhecimento para agentes e humanos, evitando redescoberta de contexto e preservando a coerência entre:

- arquitetura
- histórico
- decisões
- issues e riscos
- fontes e evidências
- relações entre projetos
- metadata canônica e proveniência

## Estrutura principal

- `.ai/`: contrato operacional e índice global da wiki
  - `CLAUDE.md`: regras operacionais da wiki
  - `index.md`: índice global da GaabWiki
  - `log.md`: registro histórico das alterações relevantes
  - `raw/`: fontes imutáveis e materiais de evidência
  - `wiki/`: páginas sintetizadas do conhecimento global
- `schema.md`: vocabulário e invariantes do conhecimento (**raiz**)
- `schema-example.md`: exemplo canônico de frontmatter
- `corpus.yaml`: especificação do corpus e exclusões futuras
- `.agent_history.md`: decisões de auditoria / MegaBrain
- `ISS/`: wiki do projeto ISS
- `KernelBot/`: wiki do projeto KernelBot
- `OrbitBot/`: wiki do projeto OrbitBot
- `Portifolio/`: wiki do projeto Portifolio / ASCII Engine
- `Xray-Spec/`: wiki do projeto Xray-Spec

## Mapa de navegação

- [Índice global](.ai/index.md)
- [Visão geral](.ai/wiki/gaabwiki-overview.md)
- [Ecossistema](.ai/wiki/gaabwiki-ecosystem.md)
- [Projetos](.ai/wiki/gaabwiki-projects.md)
- [Terminologia](.ai/wiki/gaabwiki-terminology.md)
- [Auditoria global](.ai/wiki/gaabwiki-auditoria.md)
- [Health da wiki](.ai/wiki/health.md)
- [Known unknowns](.ai/wiki/known-unknowns.md)
- [Schema](schema.md)
- [Corpus](corpus.yaml)

## Estado do corpus (2026-08-23)

A meta-wiki foi reconciliada com o código de KernelBot e OrbitBot nas branches `feature/kernel-orbit-v1-hardening`. Lacunas em `.ai/wiki/known-unknowns.md`. Retrieval sobre a GaabWiki **não** está implementado. RAG BM25 **está** implementado no KernelBot (branch-specific) — são coisas diferentes.

**Freeze V1:** pendente de gate externo. Esta wiki documenta sistemas; não declara a própria validação como facto.

Path real dos repos: `/home/gaab/Documentos/gitHub` (não `GitHub`). As pastas de projecto **dentro desta wiki** são documentação derivada, não o código.

## Relações canônicas

```text
WhatsApp → OrbitBot (Baileys) → POST /v1/chat → KernelBot (FastAPI + BM25)
Kernel = conceito + pasta kernel/ dentro do KernelBot (não é repo)
Orbit = conceito + package name "orbit" (não é repo)
GaabWiki = memória documental (não é runtime)
```

## Observação

A GaabWiki não substitui o código-fonte nem os repositórios específicos. Ela organiza a leitura e a relação entre os projetos para que um agente novo possa navegar com contexto, reduzir ruído e preservar rastreabilidade sem implementar infraestrutura de retrieval neste momento.