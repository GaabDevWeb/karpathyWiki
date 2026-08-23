---
id: gaabwiki-schema
tipo: conceito
status: atual
projeto: gaabwiki
dominio: metadata
escopo: meta
atualizado: 2026-08-23
confianca: alta
aliases:
  - Schema do conhecimento
  - knowledge schema
fontes:
  - schema.md
relacionados:
  - gaabwiki-index
  - gaabwiki-schema-example
tags:
  - schema
  - metadata
---

# Schema do conhecimento da GaabWiki

Este documento define o vocabulário mínimo e as invariantes que permitem a GaabWiki funcionar como corpus humano, memória de agente e base para futura indexação sem criar infraestrutura de RAG.

## 1. Campos canônicos

### Campos essenciais

- `id`: identidade estável e única da página.
- `tipo`: categoria semântica canônica da página.
- `status`: estado atual do conhecimento.
- `projeto`: nome do projeto ou domínio de origem.
- `dominio`: conceito ou subdomínio semântico.
- `escopo`: `meta`, `projeto`, `ecossistema`, `documentacao`, `historico`.
- `atualizado`: data no formato `YYYY-MM-DD`.
- `confianca`: `alta`, `media`, `baixa` ou `nao-confirmada`.
- `aliases`: lista de nomes alternativos relevantes.
- `fontes`: lista de evidências ou documentos primários.
- `relacionados`: links internos e IDs de páginas relacionadas.
- `tags`: palavras-chave curtas e úteis para busca humana e futura indexação.

### Campos opcionais

- `relacoes`: lista estruturada de relações semânticas.
- `valido_desde`: data de início de validade.
- `valido_ate`: data de término de validade, quando aplicável.

## 2. Tipos canônicos

Use apenas estes valores quando possível:

```text
conceito
arquitetura
projeto
decisao
fonte
historico
problema
roadmap
integracao
ecossistema
```

Não usar variações como `arch`, `architectural`, `estado`, `seguranca`, `componentes` sem padronização.

## 3. Status canônicos

```text
atual
planejado
proposto
experimental
abandonado
historico
nao-confirmado
```

## 4. Níveis de confiança

### alta

Há evidência direta em código, configuração, documentação primária ou Git com clareza.

### media

Há múltiplas evidências ou documentação consistente, mas ainda depende de contexto.

### baixa

Há alguma base, mas a informação é incompleta ou depende de inferência.

### nao-confirmada

É hipótese, observação não validada ou informação que precisa ser confirmada.

## 5. Proveniência

Toda página importante deve permitir responder:

> De onde veio essa afirmação?

Para isso, use:

```yaml
fontes:
  - README.md
  - KernelBot/raw/README.md
  - ISS/index.md
```

E quando precisar de maior granularidade:

```yaml
relacoes:
  - tipo: documenta
    alvo: kernelbot-project
```

## 6. Precedência da verdade

A ordem de evidência do corpus deve ser:

```text
código atual
>
configuração/testes
>
documentação atual
>
decisões registradas
>
histórico
>
propostas
>
inferências
```

Quando a documentação divergir do estado real, o estado real deve prevalecer. A Wiki não deve criar afirmações apenas para parecer coerente.

## 7. Estado vs evento

Cada página deve distinguir, quando relevante:

```text
Estado: o que é verdadeiro agora.
Evento: o que aconteceu para chegar ao estado atual.
```

O histórico deve ser documentado como histórico, não como estado atual.

## 8. Relações canônicas

Tipos pequenos e coerentes:

```text
utiliza
fornece
depende-de
integra
substitui
substituido-por
deriva-de
influencia
implementa
documenta
relaciona-se-com
```

A presença de uma relação em um lado do grafo deve ser coerente com o outro quando apropriado.

## 9. Modelo conceitual

```text
Project
  ├── contains → Component
  ├── has → Decision
  ├── uses → Skill
  ├── uses → Agent
  ├── integrates → Project
  └── depends-on → Component

Concept
  ├── defined-by → Source
  ├── related-to → Concept
  └── documented-by → Project
```

## 10. Invariantes do corpus

1. Todo documento importante possui `id`.
2. Nenhum `id` pode se repetir.
3. Todo `tipo` deve ser canônico.
4. Todo `status` deve ser canônico.
5. Uma página importante deve possuir contexto suficiente para leitura isolada.
6. Fontes devem ser rastreáveis quando possível.
7. Relações devem ser explícitas.
8. Histórico e atual devem permanecer distintos.
9. `raw/` não é conhecimento sintetizado.
10. A wiki não deve incluir infraestrutura de retrieval, embeddings ou banco vetorial.
11. A precedência da verdade deve seguir a ordem de evidência canônica.
12. Estado atual e evento histórico devem ser separados explicitamente quando houver mudança.

## 11. Exemplo mínimo

```yaml
---
id: kernelbot-project
tipo: projeto
status: atual
projeto: kernelbot
dominio: ai
escopo: projeto
atualizado: 2026-08-23
confianca: alta
aliases:
  - KernelBot
fontes:
  - README.md
relacionados:
  - kernelbot-current-state
  - kernelbot-architecture
tags:
  - kernelbot
  - retrieval
---
```

## 12. Identidade de wikilinks (obrigatório no corpus GaabWiki)

Obsidian e a skill wiki-carpaccio resolvem `[[stem]]` pelo **nome do ficheiro** (stem), não pelo campo `id`. Num vault com sub-wikis, stems genéricos colidem.

### Regra

```text
[[{escopo}-{conceito}]]
```

- **Meta-wiki** (`.ai/wiki/`): prefixo `gaabwiki-` — ex.: `[[gaabwiki-kernel]]`, `[[gaabwiki-rag]]`.
- **Sub-wiki KernelBot** (`KernelBot/wiki/`): prefixo `kernelbot-` — ex.: `[[kernelbot-kernel]]`.
- **Sub-wiki OrbitBot** (`OrbitBot/wiki/`): prefixo `orbitbot-` — ex.: `[[orbitbot-kernel]]`.
- **Outros projectos** (ISS, Portifolio, Xray-Spec): prefixo `{projeto}-` — ex.: `[[iss-architecture]]`.

O campo `id` no frontmatter **deve coincidir** com o stem do ficheiro (sem `.md`).

### Proibido

- `[[gaabwiki-kernel]]`, `[[gaabwiki-rag]]`, `[[gaabwiki-memory]]` num vault multi-projecto — ambíguos.
- Referenciar entidade de outro escopo sem prefixo.

### Excepção estreita

Páginas únicas no vault (ex.: `[[known-unknowns]]`, `[[gaabwiki-index]]`) podem usar stem global se não existir homónimo noutra pasta.
