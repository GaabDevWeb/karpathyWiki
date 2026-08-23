---
id: xray-spec-decisions
tipo: decisao
status: atual
atualizado: 2026-08-23
---

# Decisões relevantes

## Decisão 1: score recalculado no backend

### Contexto

O sistema analisa uma especificação e produz um score. O projecto quer evitar que a resposta do LLM e o frontend controlem diretamente a métrica final.

### Decisão

O backend recalcula o valor total do score a partir das dimensões, aplicando pesos fixos e depois atualiza `score.label`.

### Motivo

Isso cria uma fonte de verdade consistente e reduz risco de `score` divergente ou manipulado pelo modelo.

### Evidência

- `backend/app/services/score.py`
- `README.md` seção "Arquitetura Deep Dive"

### Status

Atual.

---

## Decisão 2: contrato JSON-only com retry único

### Contexto

O LLM pode devolver texto livre, markdown, JSON incompleto ou schema ausente.

### Decisão

O backend remove fences de markdown, tenta `json.loads` e valida contra o schema Pydantic. Em caso de erro, executa um retry único usando um prompt de correção.

### Motivo

O sistema depende de uma estrutura estável para renderização e para evitar que o frontend interprete payloads inválidos.

### Evidência

- `backend/app/services/analyzer.py`
- `backend/app/services/prompt_builder.py`

### Status

Atual.

---

## Decisão 3: arquitetura orientada a providers

### Contexto

Há necessidade de suportar múltiplos providers de LLM sem acoplamento forte.

### Decisão

Cria-se um registry de providers e uma interface comum `chat_completion()` com `probe()` em módulos isolados.

### Motivo

Facilita a troca de provedor por variável de ambiente e a expansão sem reescrever a orquestração.

### Evidência

- `backend/app/services/llm_registry.py`
- `backend/app/services/providers/`
- `.env.example`

### Status

Atual.

---

## Decisão 4: histórico no navegador

### Contexto

O sistema precisa de um histórico de análise sem criar persistência no backend.

### Decisão

Usa-se `localStorage` no navegador para guardar até 50 entradas.

### Motivo

Simplifica a primeira versão e reduz requisitos de infraestrutura.

### Evidência

- `frontend/js/history.js`
- `README.md` ("Histórico: até 50 análises em localStorage")

### Status

Atual.

---

## Decisão 5: sem criação de requisitos inventados

### Contexto

A análise deve ser útil e não "adivinhar" requisitos adicionais.

### Decisão

A resposta do modelo deve preservar intenção original e sinalizar indeterminações com `[A DEFINIR: ...]`.

### Motivo

A ferramenta prioriza melhoria da clareza sem inventar escopo sem evidência.

### Evidência

- `backend/app/services/prompt_builder.py`
- `README.md`

### Status

Atual.
