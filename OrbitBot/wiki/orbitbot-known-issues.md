---
id: orbitbot-known-issues
tipo: risco
status: atual
atualizado: 2026-08-23
---

# Problemas conhecidos

## 1. README vs código

README descreve OpenRouter. Código usa Kernel. Conflito aberto no repo de origem.

## 2. OpenRouter não é fallback

Wikis anteriores diziam "coexistência / fallback". Evidência: `openrouterProvider.js` sem import no path actual. Código morto.

## 3. `/ai stats` e cache

Comando admin referencia `systemStats.cache.size`; `getSystemStats()` em `openai.js` não devolve `cache`. Crash provável.

## 4. Dependência do Kernel

Sem `KERNEL_API_URL` acessível, o bot não gera resposta útil.

## 5. Memória dupla

SQLite local + transcript Kernel. Risco de operadores tratarem o SQLite como SSOT. Não é.

## 6. Produção conjunta

NÃO CONFIRMADA.

## 7. Sem CI

Não há `.github/workflows` neste repo.
