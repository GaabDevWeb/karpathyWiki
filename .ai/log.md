## [2026-08-23] init | wiki-carpaccio

Wiki inicializada. Estrutura mínima criada em `.ai/`.

## [2026-08-23] audit | gaabwiki-global

Auditoria estrutural global concluída sobre a GaabWiki: inventário dos projetos ISS, KernelBot, OrbitBot, Portifolio e Xray-Spec; consolidação do índice da meta-wiki; criação de páginas de ecossismo, terminologia e relatório final; e reforço das relações canônicas entre Kernel, Orbit, KernelBot e OrbitBot.

## [2026-08-23] standardize | gaabwiki-rag-ready

Padronização da meta-wiki para preparação futura de retrieval: IDs estáveis introduzidos em páginas centrais, metamodelo canônico documentado em `schema.md`, regras de confiabilidade e proveniência reforçadas em `CLAUDE.md`, e especificação do corpus definida em `corpus.yaml` sem criar infraestrutura de vector DB ou embeddings.

## [2026-08-23] hardening | gaabwiki-v1

Hardening final da GaabWiki V1: reforço da precedência da verdade, separação entre estado e evento, políticas de manutenção e entrada, criação de páginas de entidades canônicas, health check e known unknowns; base documental estabilizada para futuro retrieval sem implementar qualquer camada técnica de indexação.

## [2026-08-23] adversarial-remediation | gaabwiki-v1

Correcção H1–H5 + M1–M4 do gate adversarial: branch provenance em gaabwiki-kernel/ecosystem; Kernel≠KernelBot; path outbound; orbitbot-kernel/branches; links kernelbot-rag; prefixos iss/portifolio/xray-spec; Portifolio/.ai/wiki excluído do corpus current. Freeze **não** declarado.

## [2026-08-23] lint+update | forensic-pass-3

Segunda reconciliação contra código (worker executor). Corrigido o que a passagem anterior ainda deixava mentir ou vago:

- Agent/Skill: sem runtime inventado (MegaBrain ≠ chat)
- Security: três planos (wiki / KernelBot ACL / OrbitBot ACL) + ausências
- Memory: 12 mecanismos distintos
- KernelBot: Ops/Traces documentados; `bootstrap_catalog_state` sem import; Discord stub
- OrbitBot: OpenRouter = código morto (não fallback); paths `src/groups/`; `/ai stats` cache
- Inventário: path `gitHub` vs `GitHub`; satélites; schema/corpus na raiz
- `tipo: documento` → `problema` em health/known-unknowns
- Fontes: source-index deixa de ser circular
- CLAUDE.md/README: paths do schema corrigidos

**Evento histórico (pré-gate):** passagem anterior registou veredito preliminar de freeze — **substituído** pelo gate independente (READY WITH BLOCKERS). Código dos projectos **não** foi alterado.