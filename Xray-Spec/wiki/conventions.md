---
tipo: convencao
status: atual
atualizado: 2026-08-23
---

# Convenções observadas

## Convenções de configuração

- As variáveis de ambiente do sistema usam prefixo `XRAY_`.
- Há aliases compatíveis como `LLM_PROVIDER` e `LLM_MODEL`.
- Cada provider exige a sua própria chave, por exemplo `OPENROUTER_API_KEY` ou `ANTHROPIC_API_KEY`.
- Provedores são nomeados em minúsculas e sem espaços: `openrouter`, `gemini`, `openai`, `anthropic`, `deepseek`, `groq`, `cursor`.

## Convenções de API

- Endpoint de análise: `POST /api/analyze`
- Health check: `GET /api/health`
- Cliente e backend usam JSON; a resposta do LLM é validada como JSON.
- Sessões de erro são convertidas em status HTTP amigáveis ao cliente (400, 422, 429, 502, 504).

## Convenções de resposta

- O schema de resposta é estritamente validado por Pydantic.
- O servidor recalcula o valor do total do score a partir das dimensões.
- O campo `improved_spec` exige resumo de mudanças explícito.
- O texto de entrada é validado para 10 a 10.000 caracteres.

## Convenções de frontend

- Sem build system; HTML e JS puro em `frontend/`.
- Estado de UI controlado por `STATE` e render flow em `app.js`.
- Histórico salvo em `localStorage` com chave `xray_history`.
- Análises por invocação não persistem no backend.

## Convenções de desenvolvimento

- Repositório não inclui evidência de testes automatizados em diretórios dedicados.
- O README recomenda `python3 -m venv .venv` e setup manual local.
- O código usa Logging em vez de stacktraces expostos ao cliente.

## Status

Estas são convenções observadas no código e na documentação e não boas práticas genéricas inventadas por inferência.
