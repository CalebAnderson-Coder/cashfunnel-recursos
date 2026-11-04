# LLAMADA — Dale a Claude Code un número de teléfono (con Bland AI)
*Recurso del video "Le di a Claude un número de teléfono" — Brian Anderson / CashFunnel (docs de Bland verificadas 4-nov-2026)*

Claude Code se conecta al servidor MCP de Bland AI y puede llamarte, hablar con alguien y dejarte el resumen.

## Lo que necesitas
1. **Claude Code** (plan de pago de Claude). El video menciona que también funciona con otros agentes que soporten MCP, como Codex.
2. **Cuenta de Bland AI** y su **API key** (en el panel: Settings → API key). Para tener un número propio que llame, Bland ofrece su plan de número (*Agent Phone Plan*), que agrega un número local de EE. UU. Revisa sus precios: las llamadas tienen costo.

## Conectar (2 opciones)
**Con API key:**
```bash
export BLAND_API_KEY="tu_api_key"
claude mcp add --transport http bland https://api.bland.ai/v1/mcp --header "Authorization: Bearer $BLAND_API_KEY"
claude mcp list
```
**Con inicio de sesión (OAuth):** agrega el servidor sin la cabecera y luego `claude mcp login bland`.

## Pruébalo
Dile a Claude: *"Quiero que me puedas llamar a mí y a otros. Mi número es +58… Llámame ahora para probar."* Aprueba la llamada cuando te lo pida.
Luego pídele que cree un **skill** para llamar a quien le digas.

## La idea pro del video
Una rutina cada mañana a las 9:00 que revise tu email, Slack y herramientas, y **te llame solo si algo sale mal**.

## Ojo
- Guarda la API key como contraseña; nunca la pegues en un repositorio.
- Llamar a terceros: avísales que es una IA y respeta las leyes de tu país.

Fuentes: https://docs.bland.ai/integrations/mcp/clients/claude-code · https://www.bland.ai/ai-phone-number/claude-phone-calls
