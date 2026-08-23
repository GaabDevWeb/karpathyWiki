---
id: gaabwiki-projects
tipo: conceito
status: atual
projeto: gaabwiki
dominio: portfolio-ecosystem
escopo: meta
atualizado: 2026-08-23
confianca: alta
aliases:
  - Projetos da GaabWiki
  - Inventory of projects
fontes:
  - listagem /home/gaab/Documentos/gitHub
  - /home/gaab/Documentos/gitHub/KernelBot/README.md
  - /home/gaab/Documentos/gitHub/OrbitBot/package.json
  - ISS/index.md
  - Portifolio/index.md
  - Xray-Spec/index.md
relacionados:
  - gaabwiki-ecosystem
  - gaabwiki-overview
  - gaabwiki-terminology
  - known-unknowns
tags:
  - gaabwiki
  - projects
  - inventory
---

# GaabWiki — Projetos

## Path

Workspace real: `/home/gaab/Documentos/gitHub`.  
`/home/gaab/Documentos/GitHub` **não existe** (Linux é case-sensitive).

O `.git` do directório pai aponta para `gaabFaculty/KernelBot.git`. Vários filhos têm `.git` próprio (clones aninhados). Relação exacta pai↔`GaabDevWeb/KernelBot`: **NÃO CONFIRMADA**.

## Projectos com sub-wiki na GaabWiki

| Projeto | Repo de código | Função verificada | Estado auditado |
|---------|----------------|-------------------|-----------------|
| GaabWiki | este repo (wiki-only) | memória documental | V1 com ressalvas |
| KernelBot | `/home/gaab/Documentos/gitHub/KernelBot` | API FastAPI + BM25 + LLM | branch `feature/kernel-orbit-v1-hardening` |
| OrbitBot | `/home/gaab/Documentos/gitHub/OrbitBot` | cliente WhatsApp → Kernel HTTP | mesma feature branch |
| ISS | `/home/gaab/Documentos/gitHub/ISS` | site estático + pipeline VTT | wiki local (não re-auditaram código nesta passagem) |
| Portifolio | `/home/gaab/Documentos/gitHub/Portifolio` | app Next.js; README ROOT OS vs código ASCII Engine | conflito README↔código já na wiki local |
| Xray-Spec | `/home/gaab/Documentos/gitHub/Xray-Spec` | análise de specs (FastAPI + JS) | wiki local |

As pastas homónimas **dentro da GaabWiki** são wikis, não checkouts do código.

## Satélites da família Kernel/Orbit (sem sub-wiki V1)

| Pasta | Evidência | Papel aparente |
|-------|-----------|----------------|
| KernelBot-Deploy | repo `GaabDevWeb/KernelBot-Deploy` | stack de deploy (UI + Docker); README "Em obras" |
| z-KernelDeploy | sem `.git` próprio | cópia local divergente do Deploy |
| KernelPlanner | sem `.git` próprio | prompts/corpus antes de ingestão |
| KernelBot.wiki | repo wiki GitHub | docs de utilizador (ACL / KernelBot) |
| EchoRoute | README: "OrbitBot - POC" | POC antiga WhatsApp |
| AGENTS | sem remote; `Cursor/GLOBAL-SETUP.md` | MegaBrain local (skills/orchestrator) |
| CursorSKILLS | `GaabDevWeb/CursorSKILLS` | setup Cursor portátil |

## Outros dirs de 1º nível (inventário, sem pretensão de cobertura V1)

ActionTests, ASCII-LAB-readme, CL4R1T4S, devops, GAAB-sRICE, GitCourse, gitTrain, GitTreino, index, ISS-Eletivas, Jsons, linkedim, mods, nixos-configuration, Noctis-rice, polybar-themes, ProjetoLucas, RepoTools, RiceProject, rofi, STRIPPERscrapper, Tps, whisperTest, Zappy.

**Não existem** dirs `Kernel`, `Orbit`, `Memory`, `RAG` ou `Security` no 1º nível.

## Navegação das wikis derivadas

- [ISS](../../ISS/index.md)
- [KernelBot](../../KernelBot/index.md)
- [OrbitBot](../../OrbitBot/index.md)
- [Portifolio](../../Portifolio/index.md)
- [Xray-Spec](../../Xray-Spec/index.md)
