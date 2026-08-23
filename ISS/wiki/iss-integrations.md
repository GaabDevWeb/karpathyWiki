---
id: iss-integrations
tipo: integracao
status: atual
atualizado: 2026-08-22
relacionado:
  - "[[iss-architecture]]"
  - "[[iss-branches]]"
  - "[[iss-decisions]]"
---

# Integrações

Sistemas externos e repositórios relacionados.

## StripperScrapper (IMPLEMENTADO — repo separado)

- URL: https://github.com/GaabDevWeb/STRIPPERscrapper
- Papel: extracção local autenticada Infnet → `.vtt` e documentos
- Saída consumida pelo ISS em `downloads/`
- Stack referida no README ISS: Node.js + Puppeteer
- **Não** faz parte do código deste repositório ISS

## Cursor SDK / Agent (IMPLEMENTADO no GHA)

- Pacote `@cursor/sdk` instalado no job Actions
- Secret `CURSOR_API_KEY`; variável opcional `CURSOR_MODEL_ID`
- Gera Markdown de lição a partir de VTT + contexto de documentos + prompts `agents/`

## Discord (PARCIAL / opcional)

- Secret `DISCORD_WEBHOOK_URL`
- Script `.github/scripts/discord-notify.sh`
- Embeds com detalhes de lição nova; sem secret o passo é ignorado

## GitHub Pages (IMPLEMENTADO)

- Site público: https://gaabdevweb.github.io/ISS/
- Repo público: https://github.com/GaabDevWeb/ISS
- `.nojekyll` presente

## KernelBot + MySQL (EXPERIMENTAL — branch `features`)

- Repo referido: https://github.com/GaabDevWeb/KernelBot
- Fluxo: ingest `knowledge` via pymysql; `POST /reload`; `GET /health/catalog`
- Secrets: `KB_DB_*`, `KERNELBOT_CHAT_URL`, `KERNELBOT_RELOAD_TOKEN`, etc.
- **Não** está no workflow de `main`

## ActionTests (DESCONHECIDO / legado)

- README: “legado / espelho”; desenvolvimento do pipeline; integração canónica é no ISS
- Repositório não analisado nesta passagem da wiki

## LibreOffice / poppler (IMPLEMENTADO no runner)

- Conversão `.ppt`/`.pptx` → PDF e `pdftotext` no job de sumarização
