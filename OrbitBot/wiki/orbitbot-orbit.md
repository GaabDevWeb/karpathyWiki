---
id: orbitbot-orbit
tipo: arquitetura
status: atual
atualizado: 2026-08-23
---

# Orbit

## Papel conceitual

O nome Orbit aparece como identidade do bot e também como conceito arquitetural mais amplo. No contexto do projeto, ele parece corresponder ao nível de interação com o usuário, canal e execução da conversa.

## Funções observadas

- nome do trigger de mensagens (`@orbit`);
- apresentação do assistente em `prompts/SYSTEM.md`;
- camada de canal e transporte entre usuário e sistema;
- nome útil para unificar o cliente/adapter de interface.

## Limite conceitual

Orbit não é confirmado como um repositório independente do projeto principal. Há evidência de que o nome é usado como identidade do bot e também como referência arquitetural de um conjunto maior, mas a implementação real do código está centralizada no OrbitBot.

## Estado

- Confirmado: identidade do produto e trigger de usuário.
- Confirmado: papel de camada de interação.
- Não confirmado: existência de um “Orbit” independente e separado do OrbitBot.

## Relações

- [[orbitbot-identity]]
- [[orbitbot-ecosystem]]
- [[orbitbot-kernel]]
