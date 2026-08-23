---
id: kernelbot-orbitbot
tipo: component
status: não confirmado
atualizado: 2026-08-23
fonte:
	- "raw/related/OrbitBot-README.md"
	- "raw/related/OrbitBot-docs/ARCHITECTURE.md"
---

# OrbitBot — notas rápidas

Evidência encontrada:

- `docs/prd/2026-07-28-kernel-orbit-integration.md` nomeia explicitamente `Orbit` como `OrbitBot` (Adapter WhatsApp via Baileys).
- `memory/orbit-kernel-unification/AUDIT.md` contém uma auditoria detalhada sobre opções de unificação e migração.

O que é (síntese baseada em documentos):

- OrbitBot = conjunto de componentes Node.js que implementam Baileys, formatos WhatsApp, deduplicação de mensagens, comandos admin locais e sessão QR.
- Não há implementação de OrbitBot neste repositório; o plano é tratar Orbit como adapter externo que consome a API do Kernel.

Detalhes verificados (ingest de docs):

- Implementação: `@whiskeysockets/baileys` (versão 6.7.18), Node.js ≥18, persistência SQLite (`database/data/orbitbot.db`). Fonte: `docs/ARCHITECTURE.md`, `RELATORIO-GERAL.md`.
- Concurrency: mutex por JID (`src/concurrency.js`) para serializar chamadas IA por utilizador; dedupe por `messageKey` impede reprocessamento duplicado.
- Fluxo 1:1: mensagens privadas processadas apenas quando ativadas (prefixo `@orbit` em modo teste) ou por design de admin; prefixo é removido antes de encaminhar ao KernelProvider.
- Grupos: buffer em RAM (max 40 msgs), ativação por menção `@orbit`, sem escrita em SQLite.
- Comandos admin suportados: `/ai` (persona/stats/cache), `/backup`, `/historico`, `/reset` (whitelist `ADMIN_NUMBERS` no env).
- Formatação: `markdownToWhatsapp` em `src/utils/whatsappFormatter.js` com matriz de contratos definida em `docs/WHATSAPP-MARKDOWN-MAPPING.md`.
- Integração com Kernel: `KERNEL_API_URL`, `KERNEL_API_TOKEN`, `KERNEL_API_TIMEOUT_MS` para `POST /v1/chat` — mapeamento de `ChannelContext` preserva JIDs completos (não normalizar para dígitos).

Riscos/observações operacionais:

- Baileys é Node.js; migração para Python exigiria sidecar ou reescrita (auditoria lista opções A–D e recomenda A/D para deploy unit).
- Cache de respostas local existe, mas a arquitetura Kernel→Orbit desativa cache no caminho Kernel (Kernel é SSOT para transcript/pin).

Fontes preservadas em `raw/related/OrbitBot-docs/`.

Relação com Kernel

- Dependência: OrbitBot depende do Kernel para RAG, grounding e geração de texto (LLM).
- Integração planeada: troca do provider LLM directo por `KernelProvider` HTTP (Kernel expõe `/v1/chat`).

Estado e recomendações

- Estado: `não confirmado` como código aqui; existem branches de integração e auditorias que tratam da unificação.
- Recomendação operacional: manter Orbit como um deploy sidecar Node.js até decisão arquitetural; preferir testes de paridade antes da migração.

Fontes:

- `docs/prd/2026-07-28-kernel-orbit-integration.md`
- `memory/orbit-kernel-unification/AUDIT.md`