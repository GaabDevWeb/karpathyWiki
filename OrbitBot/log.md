## [2026-08-23] init | wiki-carpaccio

Wiki inicializada no diretório externo `/home/gaab/Documentos/gitHub/GaabWiki/OrbitBot`.

Evidências principais capturadas:
- OrbitBot = cliente WhatsApp / adapter de canal em Node.js
- KernelBot = backend de conhecimento e RAG com FastAPI, BM25, MySQL e context router
- Relação confirmada: OrbitBot envia `POST /v1/chat` para o Kernel em `KERNEL_API_URL`
- Sinais de ecossistema: branches `feature/kernel-orbit-*` compartilhadas e referência explícita a `KernelBot` em `.agent_history.md`

## [2026-08-23] ingest | orbitbot-readme

Preservado resumo do README de OrbitBot e do KernelBot em `raw/`.

## [2026-08-23] ingest | branches

Registadas branches relevantes do OrbitBot e do KernelBot para reconstrução histórica e da relação entre os projetos.

## [2026-08-23] update | ecosystem

Mapeadas as relações do ecossistema e diferenciadas as camadas: canal (OrbitBot), backend de contexto (KernelBot), infraestrutura compartilhada (memory, ACL, RAG, traces, prompts).

## [2026-08-23] update | forensic-pass-3

Código vs wiki: OpenRouter fora do fluxo; paths `src/groups/groupHandler.js`; agents/skills sem runtime; `/ai stats` cache; README stale. current-state, architecture, known-issues, agents, skills actualizados. Código do repo OrbitBot **não** alterado.
