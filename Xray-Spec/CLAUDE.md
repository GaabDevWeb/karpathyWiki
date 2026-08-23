# Wiki Carpaccio — contrato operacional (Xray-Spec)

Este ficheiro define como agentes devem consultar e manter a wiki deste projecto.
É lido em cada sessão. O que não estiver aqui ou na wiki não é memória persistente.

## Identidade

- **Projecto documentado:** Xray-Spec
- **Localização desta wiki:** `/home/gaab/Documentos/gitHub/GaabWiki/Xray-Spec/`
- **Código de origem:** `/home/gaab/Documentos/gitHub/Xray-Spec` — **não alterar** o código a partir de operações de wiki

## Localização

```text
Xray-Spec/
├── CLAUDE.md    ← este ficheiro
├── index.md     ← mapa; ler primeiro
├── log.md       ← eventos importantes (append-only)
├── raw/         ← fontes originais imutáveis
└── wiki/        ← conhecimento sintetizado
```

## Princípio

A wiki é memória derivada entre agentes e código. Não substitui o código.

Pergunta-guia: *O que um agente novo precisaria saber para trabalhar no Xray sem repetir descobertas?*

## Hierarquia de verdade

```text
Código > Decisões explícitas > Documentação > Wiki derivada > Inferência
```

Código vence sempre. Divergências → registar, não corrigir silenciosamente.

## Regras invioláveis

1. **Não inventar conhecimento** — só registar o observado no código, docs, ou informado pelo utilizador
2. **Não criar estrutura por antecipação** — pastas temáticas só com necessidade real
3. **Não implementar RAG** — Markdown + Git + Obsidian (opcional) são suficientes
4. **Preservar fontes** — ficheiros em `raw/` são imutáveis
5. **Marcar incerteza** — `Status: não confirmado` ou `status: conflito não resolvido` no frontmatter
6. **Não alterar o repositório Xray-Spec** ao manter esta wiki — escrita apenas sob `GaabWiki/Xray-Spec/`

## Distinção obrigatória de estado

Ao documentar funcionalidades, usar rótulos: **IMPLEMENTADO** | **PLANEJADO** | **PARCIAL** | **ABANDONADO** | **EXPERIMENTAL** | **DESCONHECIDO**.

## Crescimento orgânico

- Páginas nascem soltas em `wiki/`
- Frontmatter `tipo:` obrigatório em toda página
- **3+ páginas** do mesmo `tipo:` → criar subpasta, mover, actualizar index e log
- Pasta é cosmética; wikilink resolve por **nome**
- Único tipo inicial garantido: `fonte`

## Frontmatter mínimo

```yaml
---
tipo: ...
status: atual | obsoleto | não confirmado | conflito não resolvido
atualizado: YYYY-MM-DD
---
```

## Workflows

### Consultar (antes de implementar)

1. Ler `index.md`
2. Ler páginas relevantes
3. Confirmar no código do repositório Xray-Spec se necessário
4. Respeitar decisões e convenções registadas

### Ingerir fonte

1. Ler fonte → extrair relevante
2. Preservar em `raw/` se aplicável
3. Actualizar páginas existentes (preferir a criar)
4. Wikilinks + `index.md` + entrada em `log.md`

### Actualizar (após mudança importante)

1. Detectar obsolescência
2. Actualizar páginas + decisões novas
3. `index.md` + `log.md` se relevante

### Lint (periodicamente)

Órfãs, links quebrados, contradições, duplicados, index desactualizado. Marcar problemas; não apagar incertezas às cegas.

## O que não documentar

Trivialidades, tutoriais genéricos, suposições como factos, cópia do código de aulas.

## Vocabulário de tipos

| tipo | Descrição |
|------|-----------|
| fonte | Documento de origem |
| estado | Snapshot verificável |
| arquitetura | Visão estrutural |
| decisao | ADR / decisão |
| convencao | Padrões observados |
| dominio | Regras de negócio / conteúdo |
| problema | Issues conhecidos |
| historia | Evolução do projecto |
| branch | Visão de branches |
| roadmap | Planeamento com evidência |
| integracao | Sistemas externos |

*(Expandir conforme novos tipos forem cunhados.)*
