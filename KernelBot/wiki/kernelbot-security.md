---
id: kernelbot-security
tipo: security
status: atual
atualizado: 2026-08-23
fonte:
  - "raw/docs-wiki/14-seguranca-observabilidade.md"
  - "raw/README.md"
---

# Segurança — medidas observadas

Principais controles observados no repositório e documentação:

- Autenticação e ACL
  - Bearer token para operações sensíveis (ex.: `/reload`, `/health/catalog`, `ACL_RELOAD_BEARER_TOKEN`).
  - `ACL_CATALOG_ENABLED` controla exposição do catálogo em staging vs produção.

- Rate limiting
  - `POST /chat` limitado a 30 requisições por IP a cada 60 segundos (implementado em `api/routes.py`).

- Operações administrativas
  - Reload do índice protegido por token; operações internas em `/internal/*` com Bearer.

- Observabilidade/trace
  - `traces.sqlite3` e painel `/traces` para auditoria operacional.

- Recomendações (observadas como práticas na documentação)
  - Não reenviar `ACL_RELOAD_BEARER_TOKEN` em logs; rota protegida.
  - Emitir traces com níveis e IDs correlacionáveis para investigações forenses.

Fonte e evidências

- `README.md` (deploy e variáveis obrigatórias)
- `docs/ARCHITECTURE.md` (seção segurança)
- `api/security.py` e `api/routes.py` (código do projeto)
