---
id: orbitbot-security
tipo: seguranca
status: atual
atualizado: 2026-08-23
---

# Segurança e guardrails

## Evidências no repositório Orbital

- `KERNEL_API_TOKEN` e `ACL_INTERNAL_BEARER_TOKEN` aparecem no `.env.example` do OrbitBot.
- Há uso de `ACL` no contexto do Kernel e referências a `security`/`ACL` no histórico de desenvolvimento.
- O OrbitBot usa whitelist de admins (`ADMIN_NUMBERS`) e autenticação via sessão WhatsApp.

## Observações

A arquitetura mostra uma segurança em camadas:

1. autenticação do canal (sessão WhatsApp / Baileys);
2. autorização admin local (números permitidos);
3. token de acesso HTTP para Kernel;
4. guardrails e políticas de resposta no backend Kernel;
5. traces para observabilidade e diagnóstico.

## Status

- Confirmado: há elementos de segurança, ACL e token em diferentes camadas.
- Confirmado: a segurança é transversal e não localizada em um único projeto.
- Incerteza: os detalhes exatos do sistema de ACL e release veto não foram totalmente verificados no código analisado.

## Relações

- [[orbitbot-kernel]]
- [[orbitbot-kernelbot]]
- [[orbitbot-identity]]
- [[orbitbot-ecosystem]]
