---
id: orbitbot-memory
tipo: memoria
status: atual
atualizado: 2026-08-23
---

# Memória e contexto

## Tipos de memória observados

### Memória local do cliente

- SQLite no OrbitBot
- histórico, config, clientes e backups
- útil para dados do usuário e de operação

### Memória de sessão / canal

- grupos usam buffer em memória
- 1:1 usa mutex + histórico local
- mais voltado para fluxo operacional do bot do que para domínio

### Memória do Kernel

- transcript
- pin
- contexto institucional
- grounding / indexação RAG
- busca BM25

## Diferença importante

A arquitetura não trata toda a memória como um único mecanismo. O que o cliente salva localmente não é necessariamente a mesma coisa que o Kernel considera fonte oficial de contexto.

## Conclusão

O ecossistema separa claramente:
- memória operacional local (OrbitBot)
- memória de conhecimento e contexto (KernelBot)
- memória de sessão e estado transitório (grupos, mutex, triggers)

## Relações

- [[orbitbot-identity]]
- [[orbitbot-kernelbot]]
- [[orbitbot-rag]]
- [[orbitbot-ecosystem]]
