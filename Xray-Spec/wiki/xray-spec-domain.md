---
id: xray-spec-domain
tipo: dominio
status: atual
atualizado: 2026-08-23
---

# Domínio do sistema

## O que o Xray analisa

O Xray é um "spec inspector": examina textos de especificação antes de estes serem apresentados a uma IA ou a um time técnico. A ideia central não é "gerar requisitos", mas detectar se a especificação está pronta para ser executada ou desenvolvida sem ruído, ambiguidade e lacunas.

## Tipos de input suportados

Os tipos declarados no schema são:

- `prompt`
- `requirement`
- `briefing`

Essas categorias orientam a calibração do modelo.

## Dimensões de análise

As seis dimensões observadas no projecto são:

- `context` — problema, contexto, dor, utilizador/cenário
- `objective` — objetivo e entregável esperado
- `constraints` — restrições, stack, prazo, plataforma, limites
- `specificity` — nível de detalhe e adequação
- `clarity` — linguagem clara, sem múltiplas interpretações
- `success_criteria` — critérios mensuráveis e de aceitação

## O que é considerado problema

A lógica do sistema identifica:

- `gaps`: elementos ausentes ou faltantes
- `ambiguities`: termos com múltiplas interpretações plausíveis
- `assumptions`: premissas implícitas e arriscadas
- `suggestions`: ações para melhorar a especificação
- `improved_spec`: proposta de revisão sem inventar requisitos fora do contexto

## Regra importante

O projecto afirma explicitamente que **não inventa requisitos**. A proposta de revisão deve preservar a intenção original e sinalizar pontos ainda indefinidos com o marcador `[A DEFINIR: ...]`.

Isso está documentado em `prompt_builder.py` e no README do repositório.

## Estado de domínio

**IMPLEMENTADO**: classificação da qualidade de especificações usando critérios estruturados e ponderados.

**PLANEJADO / NÃO EVIDENCIADO**: integração com outro tipo de conteúdo além de texto livre (tickets, PRDs estruturados, documentos anexados, multimodal inputs).
