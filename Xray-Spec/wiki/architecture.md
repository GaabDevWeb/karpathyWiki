---
tipo: arquitetura
status: atual
atualizado: 2026-08-23
---

# Arquitetura

## Visão geral

O Xray-Spec separa a experiência do utilizador do motor de análise em duas camadas principais:

- `frontend/`: interface web em HTML + JavaScript vanilla
- `backend/`: API FastAPI responsável pela orquestração do LLM e pela validação do resultado

## Camadas reais

### 1) Frontend

Local: `frontend/`

Responsabilidades:

- validar input localmente (`frontend/js/validator.js`)
- controlar estados da UI (`frontend/js/app.js`)
- chamar a API backend (`frontend/js/api.js`)
- renderizar a análise e o diff (`frontend/js/renderer.js`)
- salvar histórico em `localStorage` (`frontend/js/history.js`)

Observações:

- não usa bundler nem framework;
- serve-se de `python3 -m http.server` em `127.0.0.1:5500`;
- comunica apenas com o backend em `127.0.0.1:8000`.

### 2) Backend FastAPI

Local: `backend/app/`

Responsabilidades:

- expor as rotas HTTP;
- selecionar provider activo;
- montar prompts;
- chamar o provider;
- validar formato JSON;
- recalcular score a partir dos pesos fixos;
- devolver diagnóstico estruturado em JSON.

## Fluxo principal

```text
Frontend -> POST /api/analyze -> FastAPI route -> analyzer -> LLM adapter -> JSON validation -> score recomputation -> response JSON -> renderer
```

## Provider layer

A arquitetura usa um registry em `backend/app/services/llm_registry.py` para mapear nomes de provider a módulos concretos.

Provedores observados:

- OpenRouter
- Gemini
- OpenAI
- Anthropic
- DeepSeek
- Groq
- Cursor

Cada módulo implementa `chat_completion()` e, quando relevante, `probe()` para health checks.

## Lógica de score

O servidor recalcula a pontuação a partir das dimensões, em vez de confiar na resposta do LLM.

Pesos fixos:

- `context` — 0.20
- `objective` — 0.20
- `constraints` — 0.15
- `specificity` — 0.15
- `clarity` — 0.15
- `success_criteria` — 0.15

O cálculo está em `backend/app/services/score.py`.

## Validação e robustez

A lógica de validação reforça a integridade do output:

- `AnalyzeRequest` exige texto com 10 a 10.000 caracteres;
- `analyzer.py` retira fences de markdown ` ```json `;
- tenta um retry único em caso de JSON inválido;
- falha de schema após retry resulta em `AnalysisValidationError`.

## Dependências de runtime

- Python 3.11+
- FastAPI
- Pydantic + pydantic-settings
- httpx
- Python SDK do provider quando aplicável (ex.: cursor-sdk)

## Riscos e observações

- O servidor necessita de API key ativa do provider escolhido.
- Se a chave não estiver configurada, `health` devolve `status: degraded` e o backend não liga ao provider.
- O frontend não persiste o histórico no backend, apenas em browser local.

## Decisão arquitetural observada

**Decisão:** centralizar a lógica de validação e score no backend para evitar que o frontend ou o LLM determine o score final.

**Evidência:** `backend/app/services/score.py`, `backend/app/services/analyzer.py`, `README.md`.
