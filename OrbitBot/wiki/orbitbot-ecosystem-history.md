---
id: orbitbot-ecosystem-history
tipo: historia
status: atual
atualizado: 2026-08-23
---

# História do ecossistema

## Linha do tempo observada

### Fase 1 — OrbitBot como bot standalone

O README inicial descreve OrbitBot como assistente WhatsApp com IA via OpenRouter e SQLite local. Nessa fase, o projeto é autônomo e o mesmo repositório contém bot, canal, histórico e prompt.

### Fase 2 — migração para Kernel

A documentação e o histórico de desenvolvimento mostram que o projeto passou a delegar a resposta ao Kernel por HTTP (`feature/orbit-kernel-provider`, `feature/orbit-kernel-tracing`). O evento crucial é a introdução de `KernelProvider` e `traceClient`.

### Fase 3 — Kernel como provedor de contexto e busca

O repositório KernelBot confirma uma camada de RAG/BM25, contexto em camadas e observabilidade. Esse estágio reforça a separação entre canal e inteligência.

### Fase 4 — hardening e integração em conjunto

A branch atual `feature/kernel-orbit-v1-hardening` sugere uma fase de integração/estabilização, especialmente entre Kernel e Orbit. Isso é compatível com a leitura de “ecossistema em camadas”, em que o projeto se estabiliza sem que o mesmo repositório seja fusionado.

## Evolução de nomenclatura

- OrbitBot: nome do cliente canal.
- Orbit: nome de identidade/artefato arquitetural no produto.
- Kernel: nome do backend de contexto e conhecimento.
- KernelBot: repositório concreto do backend.

## Resultado histórico

A evidência indica que não houve um fork simples de “um projeto para outro”; houve uma evolução arquitetural em que o bot de WhatsApp passou a ser um adapter do Kernel e o Kernel passou a se tornar a fonte principal de contexto e conhecimento.

## Status do histórico

- Fato: há branches de integração com nomes repetidos em ambos os repositórios.
- Fato: o histórico de desenvolvimento menciona `KernelProvider` e `ACL` explicitamente.
- Hipótese útil: a arquitetura foi pensada como um ecossistema de múltiplos agentes/repositórios, e não como um único monólito.
