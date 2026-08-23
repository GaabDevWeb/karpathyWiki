---
id: kernelbot-branches
tipo: historico
status: atual
projeto: kernelbot
dominio: git
escopo: projeto
atualizado: 2026-08-23
confianca: alta
fontes:
  - /home/gaab/Documentos/gitHub/KernelBot
relacionados:
  - kernelbot-current-state
  - kernelbot-architecture
  - kernelbot-history
tags:
  - branches
  - provenance
---

# Branches relevantes do KernelBot

> Repositório de origem: `/home/gaab/Documentos/gitHub/KernelBot`  
> Evidência Git recolhida em 2026-08-23 (`git branch`, `git ls-tree`, `git cat-file`).

## Como ler este documento

| Classificação | Significado |
|---------------|-------------|
| **CURRENT (workspace)** | Branch verificada no checkout local durante a auditoria |
| **IMPLEMENTED** | Estrutura ou endpoint confirmado no código dessa branch |
| **BRANCH-SPECIFIC** | Existe numa branch; **não** assumir em `main` |
| **TARGET / PLANNED** | Objetivo de merge ou evolução; ainda não confirmado |
| **HISTORICAL** | Estado legado ou ramo abandonado; não é runtime actual |

---

## Perguntas rápidas

### O que existe actualmente em `main`?

**Classificação:** CURRENT-de-`main` / HISTORICAL relativamente à arquitectura True Kernel.

| Artefacto | Em `main`? | Evidência |
|-----------|------------|-----------|
| Pacote `kernel/` | **Não** | `git cat-file -e main:kernel/rag/search.py` → ausente |
| `api/routes_v1.py`, `POST /v1/chat` | **Não** | `git ls-tree main -- api/` → só `routes.py`, `rate_limit.py` |
| Pacote `engine/` | **Sim** | 13 paths sob `engine/` |
| `frontend/` (UI web pública) | **Sim** | ~68 ficheiros |
| BM25 via `kernel/rag/` | **Não** | RAG legado sob `engine/` |
| `adapters/whatsapp/outbound.py` | **Não** | Ausente em `main` |
| `api/security.py` (ACL v1) | **Não** | Ausente em `main` |

`main` representa a linha **monólito educacional** (FastAPI + `engine/` + frontend web). Não é a arquitectura True Kernel documentada na wiki meta.

### O que existe na branch `feature/kernel-orbit-v1-hardening`?

**Classificação:** CURRENT (workspace) / IMPLEMENTED / BRANCH-SPECIFIC.

| Artefacto | Na feature? | Evidência |
|-----------|-------------|-----------|
| Pacote `kernel/` | **Sim** | HEAD contém `kernel/rag/search.py` |
| `api/routes_v1.py`, `POST /v1/chat` | **Sim** | `git ls-tree HEAD -- api/routes_v1.py` |
| `engine/` | **Não** | Substituído por `kernel/` |
| `frontend/` | **Não** | Diretório ausente no HEAD |
| Integração Orbit (`ChannelContext`) | **Sim** | `routes_v1.py`, ADR-0002 |
| Outbound WhatsApp | **Sim** | `adapters/whatsapp/outbound.py` |
| ACL / rate limit v1 | **Sim** | `api/security.py`, `api/rate_limit.py` |

Checkout local verificado: `feature/kernel-orbit-v1-hardening` (commit `8b0b2ef` no momento da auditoria).

---

## Mapa de branches

| Branch | Classificação | Observação |
|--------|---------------|------------|
| `main` | HISTORICAL (relativamente à wiki canónica True Kernel) | `engine/` + `frontend/`; sem `/v1/chat` |
| `feature/kernel-orbit-v1-hardening` | **CURRENT (workspace)** / BRANCH-SPECIFIC | True Kernel HTTP + contrato Orbit; **não mergeada** em `main` (NÃO CONFIRMADO) |
| `origin/main` | TARGET / UNKNOWN | Pode divergir de `main` local (`e436295` remoto vs `e70b66c` local reportados) |
| `chore/railway-first-deploy` | HISTORICAL / infra | Deploy e staging |
| `chore/repo-cleanup-deploy` | HISTORICAL / infra | Limpeza e Docker |
| `feat/cursor-provider` | HISTORICAL / funcional | Provider Cursor |
| `feature/chat-history-api` | HISTORICAL / funcional | Histórico de chat |
| `feat/continuous-generation` | EXPERIMENTAL | Políticas de retrieval |
| `internalPromptFeature` | EXPERIMENTAL | Desambiguação |
| `webscraping_feature` | EXPERIMENTAL | Scraping |
| `origin/mysql-refactor`, `origin/mysql_integration` | HISTORICAL | Evolução MySQL |
| `origin/develop`, `origin/doc`, `origin/testes` | HISTORICAL | Ramos remotos não activos localmente |

---

## TARGET / PLANNED

- **Merge** `feature/kernel-orbit-v1-hardening` → `main`: **NÃO CONFIRMADO**. Até lá, tratar True Kernel como **branch-specific**, não como estado universal do repositório.
- **Branch `trueKernel`:** referenciada em ADR; relação exacta com a feature actual — **UNKNOWN**.

---

## Implicação para agentes

1. Antes de editar código, correr `git branch --show-current` no repo `/home/gaab/Documentos/gitHub/KernelBot`.
2. Não assumir que `kernel/` ou `/v1/chat` existem em `main`.
3. Documentação em `raw/docs-wiki/` que cita `engine/` descreve **HISTORICAL** — preservada imutável.
4. Páginas sintetizadas desta sub-wiki (`kernelbot-*`) descrevem a feature branch salvo indicação contrária.

## Fontes

- `git branch --show-current` → `feature/kernel-orbit-v1-hardening`
- `git ls-tree main` vs `git ls-tree HEAD`
- `docs/adr/0001-true-kernel-monolith.md` (repo KernelBot)
