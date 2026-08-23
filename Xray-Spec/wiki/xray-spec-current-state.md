---
id: xray-spec-current-state
tipo: estado
status: atual
atualizado: 2026-08-23
---

# Estado atual do projecto

## Resumo executivo

O projecto Xray-Spec funciona como uma aplicação de inspeção estrutural de especificações. O fluxo principal é:

1. o frontend coleta uma especificação em texto;
2. valida a entrada localmente;
3. envia `POST /api/analyze` para o backend;
4. o backend escolhe um provedor LLM configurado;
5. valida a resposta JSON do modelo;
6. recalcula o score no servidor e devolve um diagnóstico.

O backend é a fonte de verdade do score; o frontend apenas renderiza os resultados.

## Estado implementado

### Backend

- FastAPI app com rotas `GET /api/health` e `POST /api/analyze`
- Validadores Pydantic para texto de entrada e schema de resposta
- `score.py` recalcula total e label usando pesos fixos
- `analyzer.py` faz prompt do sistema + prompt do utilizador, tentativas de retry em JSON inválido
- adaptadores por provedores LLM: OpenRouter, Gemini, OpenAI, Anthropic, DeepSeek, Groq e Cursor
- middleware de rate limiting em `/api/*`
- CORS configurável por variável de ambiente

### Frontend

- UI estática em `frontend/index.html`
- JavaScript vanilla sem bundler
- `localStorage` para histórico de até 50 análises
- renderização do score, gaps, ambiguities, assumptions, suggestions e improved spec
- estados de loading, erro, offline e drawer de histórico/ajuda

### Domínio e lógica de negócio

- análise focada em prompts, requisitos e briefings
- medidas em 6 dimensões:
  - `context`
  - `objective`
  - `constraints`
  - `specificity`
  - `clarity`
  - `success_criteria`
- output estruturado em JSON com `gaps`, `ambiguities`, `assumptions`, `suggestions` e `improved_spec`

## Estado real do projecto

**IMPLEMENTADO**: análise funcional de especificações via LLM, backend FastAPI, frontend Web, múltiplos providers, validation, scoring e histórico local.

**PLANEJADO / NÃO EVIDENCIADO**: benchmarking de provider, comparação de custo/latência, leaderboard de modelos, persistência do backend, autenticação, integrações com banco de dados ou trabalho em fila.

## Evidência principal

- README do projecto (`README.md`)
- `backend/app/main.py`
- `backend/app/services/analyzer.py`
- `backend/app/services/score.py`
- `backend/app/config.py`
- `frontend/js/app.js`

## Limitações observadas

- Não existe evidência de testes automatizados ou CI configurados no repositório.
- O sistema depende de API key válida do provedor escolhido.
- O histórico é client-side; não há persistência de análises no backend.
- O markdown `README.md` expõe evoluções futuras como não implementadas, não como roadmap oficial.

## Status

O projecto está em estado funcional de protótipo/serviço de análise de especificações, mas não em uma plataforma de produção com observabilidade, persistência e testes completos.
