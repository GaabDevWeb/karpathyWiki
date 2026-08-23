# Fonte: .env.example (snapshot do repositório original)

## Relevância

Define o conjunto de provedores e configurações suportados pelo sistema.

## Factos observados

- Provedores suportados: `openrouter`, `gemini`, `openai`, `anthropic`, `deepseek`, `groq`, `cursor`
- Provider padrão: `openrouter`
- Variáveis relevantes: `XRAY_LLM_PROVIDER`, `XRAY_DEFAULT_MODEL`, `XRAY_CORS_ORIGINS`, `XRAY_RATE_LIMIT`, `XRAY_LLM_TIMEOUT`
- Para `cursor`, há `XRAY_CURSOR_MODE` e `XRAY_CURSOR_CWD`
- `XRAY_FALLBACK_MODEL` reservada para futura rota em OpenRouter

## Observações de rastreabilidade

Fonte observada: `/home/gaab/Documentos/gitHub/Xray-Spec/.env.example`

Data de snapshot: 2026-08-23
