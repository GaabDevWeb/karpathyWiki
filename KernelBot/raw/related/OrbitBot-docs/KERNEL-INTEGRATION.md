(Preservado) KERNEL-INTEGRATION.md — Orbit → Kernel mapping

Fonte: /home/gaab/Documentos/gitHub/OrbitBot/docs/KERNEL-INTEGRATION.md

Resumo:
- Fluxo: WhatsApp → Baileys → Orbit → KernelProvider → POST /v1/chat → Kernel → answer → formatter → WhatsApp
- Mapeamento Baileys→ChannelContext: `platform=whatsapp`, `user_id=JID`, `channel_id` = chat JID (preserve JID format)
- Reset: `/reset` → `reset_context: true` (strip @orbit before forwarding)
- Config envs: `KERNEL_API_URL`, `KERNEL_API_TOKEN`, `KERNEL_API_TIMEOUT_MS`
- Cache de respostas IA desativado no caminho Kernel; Kernel é SSOT para transcripts/pin.
