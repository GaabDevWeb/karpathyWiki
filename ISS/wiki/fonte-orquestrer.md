---
tipo: fonte
status: atual
atualizado: 2026-08-22
origem: raw/requirements/orquestrer-2026-08-22.md
---

# Fonte: agents/orquestrer.md

Prompt do orquestrador agentic do pipeline ISS (não é o workflow GHA).

## Pontos-chave

- SSOT: `documentation.md` na raiz
- Exige `agents/discipline-map.yaml` — **diverge** do código GHA actual ([[iss-known-issues]] C3)
- Protocolo de fan-out por disciplina; integração serial dos JSON
- Gates: JSON válido, unicidade `(discipline, slug)`, smoke URLs
- Registo em `.agent_history.md` (ficheiro tipicamente da branch `features`)

## Páginas derivadas

- [[iss-decisions]]
- [[iss-known-issues]]
- [[iss-conventions]]
