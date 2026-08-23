# Fonte: README.md (snapshot do repositório original)

## Relevância

Documento principal de identidade do projecto e dos fluxos de uso.

## Conteúdo resumido

- Nome: Xray
- Objetivo: raio-X de especificações; inspeciona prompts, requisitos e briefings antes do envio para IA ou times de desenvolvimento.
- Stack: Python 3.11+, FastAPI, Vanilla JS, LLM adapters via OpenRouter/Gemini/OpenAI/Anthropic/DeepSeek/Groq/Cursor.
- Fluxo principal: frontend valida entrada localmente, backend orquestra a chamada LLM, valida JSON, recalcula score no servidor.
- Score: 0 a 100 em seis dimensões ponderadas.
- Estados: `context`, `objective`, `constraints`, `specificity`, `clarity`, `success_criteria`.
- Persistência do histórico: LocalStorage no browser; texto da especificação não persiste no backend.
- Variáveis de ambiente: `XRAY_LLM_PROVIDER`, `XRAY_DEFAULT_MODEL`, `XRAY_CORS_ORIGINS`, `XRAY_RATE_LIMIT`, `XRAY_LLM_TIMEOUT`, etc.

## Observações de rastreabilidade

Fonte observada: `/home/gaab/Documentos/gitHub/Xray-Spec/README.md`

Data de snapshot: 2026-08-23
