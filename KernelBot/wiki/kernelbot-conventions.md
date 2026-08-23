---
id: kernelbot-conventions
tipo: convenções
status: atual
atualizado: 2026-08-23
---

# Convenções observadas no projeto

## Convenções de código

- estrutura modular por camadas: `api/`, `app/`, `kernel/`, `adapters/`
- pacote legado `engine/` migrado para `kernel/` na branch auditada; `raw/docs-wiki/` preserva nomenclatura antiga como fonte histórica
- configuração via ambiente e `.env`
- validação explícita de env vars em `core/config.py`
- uso de `Settings` como fonte central para comportamento do sistema

## Convenções de runtime

- FastAPI como entrypoint principal
- Uvicorn em `127.0.0.1:8001` para execução local
- streaming SSE para respostas do assistente
- MySQL como fonte de dados e BM25 como mecanismo de busca

## Convenções operacionais

- scripts em `bin/` para staging e ingest
- uso de `KERNELBOT_ENV=staging` para ambiente específico
- endpoint `/reload` para reconstruir o índice
- `/health/catalog` para comparação catálogo vs índice

## Convenções de conteúdo

- respostas devem ser anotadas com evidência no estilo `[Fonte: ...]`
- projeto evita respostas que coloquem o sistema como fonte oficial de conteúdo curricular
- política de grounding prioriza ancoragem e indicação de lacuna em vez de inventar resposta

## Importante

Essas convenções são observadas no código e na documentação. Não são “boas práticas genéricas”; são convenções do KernelBot tal como ele está implementado.