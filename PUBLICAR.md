# PUBLICAR — Claude maneja tu canal de YouTube (vía Uplika MCP)
*Recurso del video "Claude ya puede manejar tu canal de YouTube" — Brian Anderson / CashFunnel (5-nov-2026)*

Conectas **Uplika** a Claude como conector MCP. Claude lee tus views, propone Shorts, escribe títulos/hooks/descripciones, agenda la semana (con tu OK) y puede responder comentarios. Sin pegar API key: OAuth en el navegador.

- MCP: `https://api.uplika.com/mcp`
- Docs: https://uplika.com/en/docs
- Claude (web): https://uplika.com/en/integrations/claude
- Claude Code: https://uplika.com/en/integrations/claude-code

## Montarlo en Claude (web / desktop)
1. Abre Claude → **Customize** → **Connectors** → **Add custom connector**.
2. Nombre: `Uplika`. URL: `https://api.uplika.com/mcp`.
3. **Connect** → inicia sesión en Uplika → elige **YouTube** → tu canal → **Allow**.
4. Abre un chat nuevo y confirma que Uplika aparece en las tools.

## Prompt de channel manager (cópialo)
```
You are my YouTube channel manager.
1. Find the Shorts that beat their channel size.
2. Write titles and first-3-second hooks.
3. Upload and schedule them, after my yes.
4. Read my numbers every week.
5. Answer comments, fix weak titles.

Empieza listando mis cuentas conectadas (list_accounts) y confirma que estás conectado a Uplika. Luego resume mis últimos Shorts y propón el plan de la semana. No publiques nada sin mi OK explícito.
```

## Qué puede hacer (YouTube vía Uplika)
- Subir video con título y `privacyStatus` (public / unlisted / private).
- Agendar posts.
- Leer replies / métricas básicas y responder comentarios.
- Límite práctico YouTube: ~5 posts / 24 h (según docs Uplika).

## Ojo
- Uplika MCP usa **OAuth** (no pegas API key en Claude). Las API keys son solo para REST directo.
- Publicar gasta cuota de YouTube/Uplika; **tú** apruebas cada upload.
- No es “piloto automático”: el agente propone; tú dices que sí.

---
¿Quieres que te lo dejemos conectado en tu Claude? Escríbeme por DM **@briananderson.ai**.
