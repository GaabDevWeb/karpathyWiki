# CLAUDE.md

## Contrato operacional da Wiki Carpaccio

Este diretório documenta o projeto `Portifolio` em estado derivado a partir do repositório original em `/home/gaab/Documentos/gitHub/Portifolio`.

### Regra absoluta

- Não alterar o código-fonte do projeto original.
- Confirmar factos no código, README e documentação antes de escrever como verdade.
- Preservar história, mas separar claramente estado atual da decisão histórica.
- Quando houver conflito, registrar em `Status: conflito` e não ocultar a divergência.
- Quando houver inferência, marcar explicitamente como `Status: não confirmado`.

### Estado atual considerado

- Branch atual (HEAD): `ascii-engine-platform`
- Baseline relevante: `ascii-engine-next`
- Estado de produto atual: ASCII Engine converter-first, shell em `/` e `/gallery`, seguindo o documento `docs/architecture/ASCII-ENGINE-PLATFORM.md`

### Fontes principais

- `README.md`
- `PRODUCT_DECISIONS.md`
- `docs/architecture/ASCII-ENGINE-PLATFORM.md`
- `docs/architecture/ASCII-ENGINE-NEXT.md`
- `src/app/page.tsx`
- `src/studio/AsciiLab.tsx`
- `src/features/ascii-engine/index.ts`
- `git branch -a`
- `git log --all --decorate --oneline`

### Operação padrão

1. Ler `index.md`.
2. Consultar somente as páginas necessárias.
3. Confirmar no código se a questão depender do estado atual.
4. Atualizar o log em `log.md` quando houver descoberta persistente.
5. Manter a Wiki acima do mínimo necessário, mas sem duplicar documentação oficial.

### Estrutura de páginas

- `index.md`: mapa geral
- `log.md`: eventos importantes e ingest
- `wiki/current-state.md`: visão do estado atual
- `wiki/architecture.md`: visão arquitetural
- `wiki/decisions.md`: decisões relevantes
- `wiki/branches.md`: histórico das branches
- `wiki/history.md`: evolução do projeto
- `wiki/roadmap.md`: plano real observado

---

Este arquivo é o contrato persistente desta Wiki. O código original continua sendo a fonte de verdade operacional.
