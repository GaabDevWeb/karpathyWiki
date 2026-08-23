---
id: orbitbot-branches
tipo: historia
status: atual
atualizado: 2026-08-23
---

# Branches e ramos relevantes

## OrbitBot

A branch principal atual do repositório é `feature/kernel-orbit-v1-hardening`.

Branches observadas em `git branch -a`:
- `feature/kernel-orbit-v1-hardening`
- `main`
- `feature/orbit-kernel-provider`
- `feature/orbit-kernel-tracing`
- `refactor/test-trigger-mode`
- `refactor/wppconnect-to-baileys`

## KernelBot

O KernelBot também possui `feature/kernel-orbit-v1-hardening` e várias branches de arquitetura e deploy, incluindo:
- `feature/kernel-orbit-integration`
- `feature/kernel-ops-center`
- `security-audit`
- `security-hardening`
- `mysql-refactor`
- `feat/cursor-provider`
- `feat/continuous-generation`

## Interpretação

A sobreposição explícita de nomes de branches entre os projetos fornece evidência forte de que os dois repositórios evoluíram em paralelo e em integração. Esse padrão é maior do que uma coincidência de nomenclatura.

## Status

- Fato: há nítida correspondência entre branches de integração.
- Inferência: estes repositórios fazem parte de um mesmo esforço de arquitetura em camadas, com desenvolvimento paralelo e sincronizado.
