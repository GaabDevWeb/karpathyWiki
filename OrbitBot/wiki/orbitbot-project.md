---
id: orbitbot-project
tipo: projeto
status: atual
atualizado: 2026-08-23
---

# Projeto OrbitBot

## Definição

O OrbitBot é um projeto de agente WhatsApp com foco em interações 1:1 e grupos, usando Baileys como canal de transporte e SQLite para persistência local. O código do projeto mostra uma arquitetura de produto em que a IA não é responsabilidade do bot em si, mas de um provedor externo que evoluiu para um Kernel HTTP.

## Papel no ecossistema

O papel principal do projeto é atuar como:
- canal de entrada/saída para usuários de WhatsApp;
- adaptador para mensagens e eventos do WhatsApp;
- camada de trigger, deduplicação, segurança e envio de respostas;
- cliente HTTP do Kernel.

O código e a documentação indicam que o bot foi refeito para depender do Kernel como autoridade de contexto, memória e resposta. Em outras palavras, o OrbitBot não substitui o Kernel; ele o usa.

## Limites observados

- Não é um framework genérico de agentes;
- Não é o backend de RAG/BM25 do ecossistema;
- Não é a fonte de verdade para conhecimento institucional, calendário, transcript e grounding;
- Não possui autorização de segurança centralizada comparável ao Kernel.

## Relacionamentos

- [[orbitbot-orbit]] — identidade mais ampla do conceito Orbit
- [[orbitbot-kernel]] — camada de inteligência e contexto
- [[orbitbot-identity]] — implementação específica do projeto
- [[orbitbot-kernelbot]] — backend de serviços e memória
- [[orbitbot-ecosystem]] — mapa completo do conjunto
