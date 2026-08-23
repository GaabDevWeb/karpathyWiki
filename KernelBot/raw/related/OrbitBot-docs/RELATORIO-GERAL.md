(Preservado) RELATORIO-GERAL.md — resumo do inventário técnico

Fonte: /home/gaab/Documentos/gitHub/OrbitBot/docs/RELATORIO-GERAL.md

Resumo:
- Inventário técnico completo: topologia, fluxos 1:1 e grupo, bootstrap, padrões (command bus, provider, mutex), backup, testes.
- Regras 1:1: só responde em 1:1 quando mensagem começa com `@orbit` (modo teste) — prefixo removido antes do processamento.
- Grupos: buffer RAM, ativação por menção, sem escrita em SQLite.
- Comandos admin: `/ai`, `/backup`, `/historico`, `/reset` com whitelist `ADMIN_NUMBERS`.
- Formatação: `markdownToWhatsapp` com contratos em `docs/WHATSAPP-MARKDOWN-MAPPING.md`.
