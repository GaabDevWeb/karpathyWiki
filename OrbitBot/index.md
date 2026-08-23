---
id: orbitbot-project
tipo: projeto
status: atual
projeto: orbitbot
dominio: channel-interface
escopo: projeto
atualizado: 2026-08-23
confianca: alta
aliases:
  - OrbitBot
  - Orbit Bot
fontes:
  - OrbitBot/raw/orbitbot-readme.md
  - OrbitBot/index.md
relacionados:
  - kernelbot-project
  - gaabwiki-ecosystem
  - gaabwiki-terminology
tags:
  - orbitbot
  - whatsapp
  - transport
---

# OrbitBot — Wiki do ecossistema Orbit / Kernel

## Identidade do projeto

Projeto: OrbitBot  
Tipo: cliente WhatsApp / adapter de canal para um Kernel de IA  
Repositório de origem: /home/gaab/Documentos/gitHub/OrbitBot  
Repositório relacionado principal: /home/gaab/Documentos/gitHub/KernelBot  
Estado atual analisado: branch `feature/kernel-orbit-v1-hardening`  
Data da análise: 2026-08-23

## Visão resumida

O OrbitBot é um assistente pessoal via WhatsApp baseado em Baileys, com fluxo principal de IA delegando para um backend Kernel HTTP em `POST /v1/chat`. O projeto não é o Kernel por si só; ele é uma camada de entrada/saída, canal, trigger, filtros de segurança e transporte de mensagens entre WhatsApp e o sistema de conhecimento/LLM do Kernel.

A relação mais forte evidencia é:

```text
WhatsApp → Baileys → OrbitBot → Kernel HTTP API → KernelBot/RAG/contexto → resposta
```

## Estado atual

- Stack verificada: Node.js, Baileys, SQLite local, KernelProvider HTTP, pino, QR login.
- OpenRouter: ficheiro legado **fora do fluxo** (não é fallback activo). README do repo ainda o descreve como cérebro — stale.
- Relação com o ecossistema: OrbitBot é um cliente/adapter; KernelBot é o backend do cérebro e do contexto.
- Limitação principal: o estado real depende de um Kernel em execução e de variáveis de ambiente compatíveis.

## Mapa da wiki

- [[orbitbot-project]] — identidade e escopo
- [[orbitbot-current-state]] — o que existe hoje
- [[orbitbot-architecture]] — fluxos e camadas do sistema
- [[orbitbot-ecosystem]] — mapa das relações no ecossistema
- [[orbitbot-ecosystem-history]] — evolução do conjunto
- [[orbitbot-orbit]] — definição e papel do Orbit
- [[orbitbot-kernel]] — definição e papel do Kernel
- [[orbitbot-identity]] — projeto OrbitBot
- [[orbitbot-kernelbot]] — projeto KernelBot
- [[orbitbot-components]] — componentes compartilhados e reutilizáveis
- [[orbitbot-memory]] — memória, sessão e persistência
- [[orbitbot-rag]] — recuperação e grounding
- [[orbitbot-security]] — ACL, guardrails e segurança
- [[orbitbot-branches]] — análise de branches e ramos históricos
- [[orbitbot-decisions]] — decisões importantes
- [[orbitbot-known-issues]] — riscos e incertezas

## Fontes principais preservadas

- `raw/orbitbot-readme.md`
- `raw/kernelbot-readme.md`
- `raw/orbitbot-branches.txt`
- `raw/kernelbot-branches.txt`
- histórico Git dos repositórios

## Leitura recomendada

1. [[orbitbot-ecosystem]]
2. [[orbitbot-kernel]]
3. [[orbitbot-orbit]]
4. [[orbitbot-architecture]]
5. [[orbitbot-decisions]]

> A documentação do código continua sendo a fonte de verdade para o estado atual. A wiki preserva contexto, decisões, relações e histórico, sem substituir a implementação.
