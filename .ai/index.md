---
id: gaabwiki-index
tipo: conceito
status: atual
projeto: gaabwiki
dominio: knowledge-map
escopo: meta
atualizado: 2026-08-23T14:00
confianca: alta
aliases:
  - Índice global da GaabWiki
  - GaabWiki index
fontes:
  - README.md
  - .ai/wiki/gaabwiki-overview.md
  - .ai/wiki/gaabwiki-ecosystem.md
relacionados:
  - gaabwiki-overview
  - gaabwiki-ecosystem
  - gaabwiki-projects
  - gaabwiki-terminology
  - gaabwiki-auditoria
  - kernelbot-project
  - orbitbot-project
  - iss-project
  - portifolio-project
  - xray-spec-project
tags:
  - gaabwiki
  - index
  - knowledge
---

# Índice global da GaabWiki

Este é o índice principal da Wiki Carpaccio do repositório GaabWiki. Ele organiza a memória do ecossistema, conecta a meta-documentação aos projetos locais e estabelece a base para futura indexação sem construir infraestrutura de retrieval.

## Visão do ecossistema

- [[gaabwiki-overview]]: visão geral da meta-wiki, propósito e regras de coerência.
- [[gaabwiki-ecosystem]]: mapa das relações entre projetos, conceitos e dependências.
- [[gaabwiki-projects]]: inventário dos projetos documentados no repositório.
- [[gaabwiki-terminology]]: termos e nomes canônicos para Kernel, Orbit, Agents, Skills, Memory, RAG e Security.
- [[gaabwiki-auditoria]]: relatório da auditoria estrutural, semântica e histórica.
- [[gaabwiki-source-index]]: índice de fontes relevantes preservadas.
- [[gaabwiki-architecture]]: arquitetura da camada de conhecimento da GaabWiki.

## Projetos locais

- [ISS](../ISS/index.md): projeto de conteúdo, educação e publicação.
- [KernelBot](../KernelBot/index.md): núcleo cognitivo, memória e recuperação contextual.
- [OrbitBot](../OrbitBot/index.md): canal de entrada/saída e transporte de mensagens.
- [Portifolio](../Portifolio/index.md): portfólio, experiência visual e plataforma ASCII.
- [Xray-Spec](../Xray-Spec/index.md): validação de requisitos, prompts e qualidade.

## Schema e corpus

- [schema.md](../schema.md): vocabulário e invariantes do conhecimento.
- [schema-example.md](../schema-example.md): exemplo de frontmatter canônico.
- [corpus.yaml](../corpus.yaml): especificação do corpus e exclusões para futura indexação.

## Entidades canônicas

- [[gaabwiki-kernel]]: camada cognitiva e de contexto.
- [[gaabwiki-orbit]]: camada de transporte e interface.
- [[gaabwiki-kernelbot]]: projeto central do núcleo cognitivo.
- [[gaabwiki-orbitbot]]: projeto de canal e interface.
- [[gaabwiki-agent]]: execução orientada por contexto e ferramentas.
- [[gaabwiki-skill]]: capacidade funcional do agente.
- [[gaabwiki-memory]]: persistência de contexto e conhecimento.
- [[gaabwiki-rag]]: recuperação contextualizada para geração.
- [[gaabwiki-security]]: guardrails e confiabilidade da base.
- [[known-unknowns]]: lacunas conhecidas e não resolvidas.
- [[gaabwiki-health]]: checagem da saúde da wiki.

## Relações canônicas (código, 2026-08-23)

> **Proveniência:** IMPLEMENTED — `feature/kernel-orbit-v1-hardening` (KernelBot + OrbitBot).  
> **NOT MERGED INTO MAIN** — merge feature → `main`: **UNKNOWN**.  
> **PRODUCTION E2E:** **UNKNOWN** — integração HTTP no código da feature; operação conjunta WhatsApp+Kernel não confirmada.  
> Em `main`, OrbitBot **não** tem `kernelProvider.js`; KernelBot **não** tem `kernel/` nem `/v1/chat`.

```text
[IMPLEMENTED — feature/kernel-orbit-v1-hardening; NOT in main]
WhatsApp → OrbitBot (Baileys, Node) → POST /v1/chat → KernelBot (FastAPI :8001)
KernelBot → BM25 (MySQL) + grounding + LLM → JSON answer → OrbitBot → WhatsApp
Kernel    → namespace `kernel/` + conceito; NÃO é repositório separado
Orbit     → nome npm `orbit` + conceito de canal; NÃO é repositório separado
GaabWiki  → memória documental; NÃO contém código de aplicação
```

Path real dos repos: `/home/gaab/Documentos/gitHub` (o path `GitHub` com G maiúsculo **não existe**).

As pastas `ISS/`, `KernelBot/`, `OrbitBot/`, `Portifolio/`, `Xray-Spec/` **dentro da GaabWiki** são wikis derivadas, não os repositórios de código.

## Regra operacional

A meta-wiki deve orientar a navegação e preservar o contexto, sem substituir a documentação específica dos subprojetos. Sempre que houver conflito, o **código actual** do repositório de origem prevalece. README e wiki perdem.

## Estado da preparação

- IDs estáveis: meta-wiki + sub-wikis KernelBot/OrbitBot com prefixo `{projeto}-` (ver [schema.md](../schema.md) §12).
- Metadata canônica: padronizada na meta-wiki; sub-wikis KernelBot/OrbitBot com `id` = stem após remediação de blockers.
- Proveniência: documentada nas páginas canónicas; fontes primárias são os repos em `/home/gaab/Documentos/gitHub/<project>`.
- Corpus: definido em `corpus.yaml` (raiz da GaabWiki, não em `.ai/`).
- Schema: `schema.md` na **raiz** da GaabWiki (não em `.ai/`).
- Health check: registrado em [[gaabwiki-health]].
- Conhecimento não resolvido: registrado em [[known-unknowns]].
- Futuro RAG sobre a GaabWiki: preparado sem implementar infraestrutura.
- RAG no KernelBot: **implementado** (BM25) na branch `feature/kernel-orbit-v1-hardening`. Ver [[gaabwiki-rag]].

## Eventos de auditoria (histórico)

- **2026-08-23:** auditoria forense concluída; gate independente reportou blockers (branch provenance, wikilinks, auto-freeze, git).
- **2026-08-23:** remediação de blockers; **freeze V1 pendente** de novo gate externo.
