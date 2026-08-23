---
id: gaabwiki-orbit
tipo: conceito
status: atual
projeto: gaabwiki
dominio: architecture
escopo: meta
atualizado: 2026-08-23
confianca: alta
aliases:
  - Orbit layer
  - Camada de transporte
fontes:
  - /home/gaab/Documentos/gitHub/OrbitBot/package.json
  - /home/gaab/Documentos/gitHub/OrbitBot/src/mentionTrigger.js
  - OrbitBot/index.md
relacionados:
  - gaabwiki-orbitbot
  - gaabwiki-kernel
  - gaabwiki-security
tags:
  - gaabwiki-orbit
  - interface
  - transport
---

# Orbit

> Orbit é o **conceito** de canal/transporte. Não existe repo `/home/gaab/Documentos/gitHub/Orbit`.

## Definição

No código, Orbit aparece como:

- `name: "orbit"` em `OrbitBot/package.json`
- trigger de menção `@orbit` / `@~Orbit` (`src/mentionTrigger.js`)
- persona em `prompts/SYSTEM.md`
- `service` name `'orbit'` em traces (`src/traceClient.js`)

A materialização CURRENT é o **OrbitBot**.

## Estado atual

OrbitBot recebe WhatsApp (Baileys), filtra, e delega IA ao Kernel HTTP. SQLite local é operacional (clientes/histórico/admin), **não** é o SSOT de transcript.

POC histórica relacionada: `EchoRoute` (README: "OrbitBot - POC"). Não é o OrbitBot actual.

## Relação com Kernel

- Orbit canaliza; Kernel processa.
- Contrato: `KERNEL_API_URL` + `POST /v1/chat`.
- Outbound inverso: Kernel → `ORBIT_INTERNAL_URL` (:8010) — código existe; produção **NÃO CONFIRMADA**.
