# Kernel API

Kernel HTTP reutilizável para busca BM25 e conversa RAG sobre aulas indexadas. Não inclui interface web: adapters de Discord, Moodle, CLI ou outros consumidores usam exclusivamente JSON/SSE.

## Arquitetura

- Backend: FastAPI, Uvicorn, PyMySQL, rank-bm25
- LLM: OpenRouter ou Cursor
- RAG: BM25 + política de grounding
- Contexto: camadas + ContextRouter

Fluxo principal:

```text
main.py → app/factory.py → api/routes.py
                         → kernel/ (domínio, RAG, providers e contratos)
```

## API

- GET /health
- POST /chat
- POST /search

## Relação com o ecossistema

O KernelBot é o backend do conhecimento e do contexto. O OrbitBot o utiliza como fornecedor de respostas em HTTP. A integração é documentada no repositório OrbitBot em `docs/KERNEL-INTEGRATION.md` e em `.agent_history.md`.

Fontes de origem: /home/gaab/Documentos/gitHub/KernelBot/README.md
