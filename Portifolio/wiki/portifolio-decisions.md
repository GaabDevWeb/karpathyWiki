---
id: portifolio-decisions
tipo: decisão
status: atual
atualizado: 2026-08-23
fonte:
  - "[[raw-product-decisions]]"
  - "[[raw-ascii-engine-platform]]"
---

# Decisões relevantes

## Decisão 1 — pivô de produto: ROOT OS → ASCII Engine

### Contexto

O repositório histórico começa com a identidade de um portfólio em estilo sistema operativo, mas a documentação de produto e o código do branch atual convergem para um produto focado em conversão de mídia para ASCII.

### Decisão

A experiência do produto passou a ser `Convert · Animate · Library · Docs`, com foco em qualidade de conversão e não em edições de pintura ou laboratório de experimentação.

### Motivo

A documentação afirma que a ferramenta existe para converter mídia em ASCII com a melhor qualidade possível e que qualquer funcionalidade que não contribua para isso deve ser tratada como fora de escopo.

### Evidência

- `PRODUCT_DECISIONS.md`
- `src/app/page.tsx`
- `src/studio/AsciiLab.tsx`
- `docs/architecture/ASCII-ENGINE-PLATFORM.md`

### Status

Atual

---

## Decisão 2 — remover superfícies experimentais do shell principal

### Contexto

O histórico do projeto inclui editor, playground, stats, engine e scene tools. Esses módulos existiam em superfícies que diluíam a compreensão do produto.

### Decisão

Essas superfícies foram removidas do shell principal e preservadas em `src/legacy/` para referência e extração futura.

### Motivo

O produto precisava ter uma narrativa clara e imediata: o usuário deve entender rapidamente que a app é um conversor de mídia para ASCII.

### Evidência

- `src/legacy/README.md`
- `PRODUCT_DECISIONS.md`
- `docs/architecture/ASCII-ENGINE-PLATFORM.md`

### Status

Atual; preservado como legado

---

## Decisão 3 — produzir uma plataforma de produto standalone

### Contexto

A arquitetura documentada mostra uma linha de evolução de `ascii-engine-next` para `ascii-engine-platform`.

### Decisão

A branch `ascii-engine-platform` representa a primeira plataforma standalone do produto, com shell em `/` e `/gallery` e sem a marca ROOT OS como identidade ativa.

### Motivo

A documentação da arquitetura descreve uma separação fundamental entre runtime e fachada de produto, com estágio de extração em monorepo futuro sem reescrever pipelines.

### Evidência

- `docs/architecture/ASCII-ENGINE-PLATFORM.md`
- `git log --all --decorate --oneline`
- `git branch -a`

### Status

Atual para a branch em desenvolvimento; não deve ser tratado como merge definitivo para `main` sem review

---

## Decisão 4 — não tratar o projeto como banco de dados ou app full-stack

### Contexto

A visão do código atual não inclui backend, autenticação, banco de dados ou persistência de servidor.

### Decisão

O produto atual é front-end-driven e foco em cliente-side processing, CLI e exportação.

### Motivo

A organização do repositório e a arquitetura documentada indicam que o domínio principal é renderização e conversão ASCII em navegador.

### Evidência

- `package.json`
- `src/features/ascii-engine/index.ts`
- `src/studio/AsciiLab.tsx`

### Status

Atual
