---
id: kernelbot-domain
tipo: domínio
status: atual
atualizado: 2026-08-23
---

# Domínio do projeto

## Problema que resolve

O KernelBot busca responder dúvidas de alunos com base no material das disciplinas, sem depender de internet aberta ou de um professor em tempo real. Seu objetivo é contextualizar respostas ao conteúdo acadêmico que já foi indexado.

## Conceitos centrais

- aula: unidade didática indexada no MySQL
- chunk: fragmento textual extraído de uma aula
- disciplina: silo ou categoria associada ao conteúdo
- grounding: política que define como a fonte deve ser usada no prompt
- pin: contexto fixado para a conversa atual
- catalog drift: diferença entre o catálogo ISS e o índice do banco
- retrieval reason: classificação do estado da busca (ok, ambiguous, insufficient_context, etc.)

## Linguagem de domínio do produto

O projeto usa termos como:

- ACL (Agente de Contexto Local)
- BM25
- grounding anchored / strict / hybrid
- advisory pós-geração
- disciplina / lesson / slug
- reload e catalog sync

## Papel do professor e do aluno

O projeto não pretende substituir o professor, o regulamento ou a fonte oficial da faculdade. Ele serve como assistente de apoio e como camada de recuperação contextual com evidência primária.

## Limite do sistema

O kernel não é uma plataforma sem limites: ele opera sobre conteúdo já indexado e adiciona responsabilidade de resposta ancorada, quer dizer, responde melhor quando o aluno pergunta sobre temas explícitos no corpus e com contexto suficiente.
