(Preservado) API_SPEC.md — contrato parcial/consultivo

Fonte: /home/gaab/Documentos/gitHub/OrbitBot/docs/API_SPEC.md

Resumo:
- Especifica endpoints locais do Orbit (quando aplicável) e contrato do KernelProvider (POST /v1/chat) esperado.
- Inclui exemplos de body `ChannelContext` e `ChatRequest` (fields: `platform`, `user_id`, `channel_id`, `message`, `stream`, `reset_context`).
- Recomenda-se `extra=forbid` no schema Pydantic para evitar campos vendor.
