## [2026-08-23] init | wiki-carpaccio

Wiki inicializada para o projeto `KernelBot`.

Ações realizadas:
- Estrutura mínima criada (`CLAUDE.md`, `index.md`, `log.md`, `raw/`, `wiki/`).
- Capturada lista de branches e commit history resumido.
- Copiado `README.md` para `raw/README.md` como fonte imutável.

## [2026-08-23] update | current-state

Refinamento da wiki com base no código actual do repositório `KernelBot` e no histórico de branches.

Ajustes principais:
- confirmação de `main` como branch de estado atual
- registro de stack e runtime em `current-state.md`
- consolidação de decisões e ramos relevantes em `branches.md` e `decisions.md`
- separação entre estado atual, histórico e execução em staging/produção
- preservação da documentação oficial em `raw/docs-wiki/`

## [2026-08-23] update | wiki-ecosystem

Criadas páginas de síntese sobre ecossistema e componentes externos:

- `wiki/kernel.md` — definição do Kernel e módulos centrais
- `wiki/orbit.md` — análise do conceito Orbit (adapter, Baileys)
- `wiki/kernelbot.md` — identidade e responsabilidades do projecto
- `wiki/orbitbot.md` — notas sobre o OrbitBot (auditado)
- `wiki/components.md` — inventário de componentes reutilizáveis
- `wiki/memory.md` — síntese de mecanismos de memória e KB
- `wiki/rag.md` — resumo do pipeline RAG (BM25)
- `wiki/security.md` — medidas de segurança observadas
- `wiki/ecosystem.md` — mapa do ecossistema e relações
- `wiki/ecosystem-history.md` — histórico do ecossistema (PRD/branches)

Fontes preservadas em `raw/` e referências a `docs/prd/` e `memory/`.

## [2026-08-23] ingest | related-repos

- Preservados `OrbitBot` README em `raw/related/OrbitBot-README.md`.
- Preservado PRD do `OrbitBot` em `raw/related/OrbitBot-docs/2026-07-26-refactor-baileys.md` (resumo).
- Preservado resumo de `KernelBot-Deploy` README em `raw/related/KernelBot-Deploy-README.md`.
- Preservado snapshot de `KernelBot.wiki` em `raw/related/KernelBot.wiki/Visao-geral.md`.

## [2026-08-23] ingest | OrbitBot docs

- Preservado `docs/ARCHITECTURE.md` → `raw/related/OrbitBot-docs/ARCHITECTURE.md` (Resumo topologia, mutex, SQLite, Baileys).
- Preservado `docs/KERNEL-INTEGRATION.md` → `raw/related/OrbitBot-docs/KERNEL-INTEGRATION.md` (ChannelContext mapping, envs, reset behavior).
- Preservado `docs/RELATORIO-GERAL.md` → `raw/related/OrbitBot-docs/RELATORIO-GERAL.md` (inventário técnico e fluxos).
- Preservado `docs/WHATSAPP-MARKDOWN-MAPPING.md` → `raw/related/OrbitBot-docs/WHATSAPP-MARKDOWN-MAPPING.md` (contratos de formatação).
- Preservado `docs/API_SPEC.md` → `raw/related/OrbitBot-docs/API_SPEC.md` (contrato KernelProvider / exemplos).

## [2026-08-23] lint

Resumo do lint da wiki

- Verificações executadas: frontmatter (presença), links internos (`[[...]]`), index vs páginas, páginas órfãs, campos `fonte` em frontmatter.

Resultados principais:

- Frontmatter: OK — todas as páginas em `wiki/` têm frontmatter mínimo (`tipo`, `status`, `atualizado`).
- Links internos: OK — o `index.md` referencia as páginas listadas; não foram encontrados wikilinks quebrados em `wiki/`.
- Páginas órfãs: nenhuma — todas as páginas em `wiki/` são referenciadas pelo `index.md`.
- `fonte` (frontmatter): nenhuma página contém o campo `fonte`. Recomenda-se adicionar `fonte:` nas páginas de síntese (ex.: `current-state.md`, `architecture.md`, `kernel.md`, `orbit.md`, `orbitbot.md`, `components.md`, `memory.md`, `rag.md`, `security.md`, `ecosystem.md`, `ecosystem-history.md`) apontando para os arquivos preservados em `raw/` ou para paths de origem no repositório (ex.: `raw/README.md`, `raw/docs-wiki/02-arquitetura.md`, `raw/related/OrbitBot-docs/*`).

Observações:

- Não foram feitas correções automáticas: problemas detectados foram apenas marcados no log (conforme política da skill).
- Conflito operativo detectado (não resolvido): estratégia de unificação OrbitBot (Baileys Node.js) → Kernel (Python) permanece como `não confirmado` / `conflito não resolvido` na wiki; requer decisão arquitetural fora do alcance do lint.

Próximo(s) passo(s) recomendado(s):

- Adicionar campo `fonte:` nas páginas de síntese citadas acima (apontar para `raw/related/` e `raw/docs-wiki/`).
- Rodar lint novamente após adicionar `fonte` e após quaisquer mudanças no `index.md`.

Entradas de log e fontes preservadas continuam em `raw/`.

## [2026-08-23] update | add fontes

Campos `fonte:` adicionados nas páginas de síntese: `current-state.md`, `architecture.md`, `kernel.md`, `kernelbot.md`, `orbit.md`, `orbitbot.md`, `components.md`, `memory.md`, `rag.md`, `security.md`, `ecosystem.md`, `ecosystem-history.md`, `decisions.md`.

Re-lint recomendado; mudanças não comitadas.

## [2026-08-23] update | forensic-pass-3

Reconciliado com código em `/home/gaab/Documentos/gitHub/KernelBot`:
- current-state/architecture: Ops/Traces, Discord stub, bug `bootstrap_catalog_state`
- known-issues: itens 7–10
- index: UI operacional vs frontend público


