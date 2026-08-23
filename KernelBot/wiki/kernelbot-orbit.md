---
id: kernelbot-orbit
tipo: orbit
status: não confirmado
atualizado: 2026-08-23
fonte:
	- "raw/docs-wiki/02-arquitetura.md"
	- "raw/related/OrbitBot-docs/KERNEL-INTEGRATION.md"
---

# Orbit — Adapter e fronteira de transporte

Síntese

Pelo conjunto de documentos (PRD, auditoria) e pela arquitetura apresentada, `Orbit` refere-se ao conjunto de adapters e fluxos de transporte que integram canais (especialmente WhatsApp via Baileys) com o `Kernel`.

O que sabemos por evidência:

- `docs/prd/2026-07-28-kernel-orbit-integration.md` descreve explicitamente: **Orbit (OrbitBot) = Adapter WhatsApp (Baileys)** — responsável por transporte, sessão e formatação.
- `memory/orbit-kernel-unification/AUDIT.md` documenta auditoria de unificação e discute trade-offs (Baileys é Node.js; Kernel é Python).
- `docs/ARCHITECTURE.md` menciona "Fronteira Orbit" e lista responsabilidades (Baileys, sessão WhatsApp, comandos admin locais).

O que NÃO foi encontrado no repositório:

- Implementação funcional de Orbit dentro deste repositório. A pasta `adapters/` contém README e placeholders, mas não o código Baileys.

Categoria de relação com Kernel

- Relação confirmada: Orbit é um consumidor/adapter externo que fala HTTP para o Kernel (objetivo: `/v1/chat`).
- Possível evolução (hipótese documentada): unificação parcial via sidecar Node.js ou IPC (ver `memory/orbit-kernel-unification/AUDIT.md`).

Status e recomendações

- Status atual: `não confirmado` para código no repo (implementação de Orbit não está aqui).
- Se for necessário trabalhar em Orbit: procurar repositório irmão ou histórico de commits/branches que referenciem Orbit (`feature/kernel-orbit-integration`, `feature/orbit-kernel-tracing`).

Fontes primárias:

- `raw/docs-wiki/02-arquitetura.md`
- `docs/prd/2026-07-28-kernel-orbit-integration.md` (PRD)
- `memory/orbit-kernel-unification/AUDIT.md` (auditoria)