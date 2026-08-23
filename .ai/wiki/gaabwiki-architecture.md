---
id: gaabwiki-architecture
tipo: arquitetura
status: atual
projeto: gaabwiki
dominio: knowledge-architecture
escopo: meta
atualizado: 2026-08-23
confianca: alta
aliases:
  - Arquitetura da GaabWiki
  - Meta-arquitetura da Wiki
fontes:
  - README.md
  - .ai/index.md
  - schema.md
  - corpus.yaml
relacionados:
  - gaabwiki-overview
  - gaabwiki-ecosystem
  - gaabwiki-projects
  - gaabwiki-kernelbot
  - gaabwiki-orbitbot
tags:
  - gaabwiki
  - architecture
  - knowledge
---

# Arquitetura da GaabWiki

> A GaabWiki é memória documental. A arquitectura de **runtime** Kernel↔Orbit vive nos repos de código, não aqui.

## Camadas desta wiki

```text
/home/gaab/Documentos/gitHub/GaabWiki
├── schema.md, schema-example.md, corpus.yaml   # metamodelo (raiz, NÃO .ai/)
├── README.md
├── .agent_history.md                           # log MegaBrain desta auditoria
├── .ai/
│   ├── CLAUDE.md     # contrato
│   ├── index.md      # mapa
│   ├── log.md        # append-only
│   ├── raw/          # fontes imutáveis (quase vazio na meta)
│   └── wiki/         # síntese canónica
└── ISS/ KernelBot/ OrbitBot/ Portifolio/ Xray-Spec/
    # wikis derivadas — NÃO são os repos de código
```

Código de aplicação: `/home/gaab/Documentos/gitHub/<Project>` (siblings).

## O que a arquitectura NÃO inclui

- Embeddings, vector DB, BM25 sobre a wiki, MCP de retrieval.
- Execução de Kernel ou Orbit.
- Subpastas temáticas prematuras em `.ai/wiki/`.

## Preparação para futuro retrieval (não implementar agora)

O corpus e o schema permitem, **mais tarde**, BM25/embeddings/graph sobre páginas com `id`, `status`, `confianca`, `fontes`. Isso é intenção. **Não existe** essa camada.

## Relação com a arquitectura de produto

A arquitectura de runtime está em [[gaabwiki-kernelbot]] e [[gaabwiki-orbitbot]], não nesta página.
