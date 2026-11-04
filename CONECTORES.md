# CONECTORES — 4 MCPs para que Claude haga más que chatear
*Recurso del video sobre conectores de Claude — Brian Anderson / CashFunnel (docs oficiales, 4-nov-2026)*

| Para qué | Herramienta | Cómo se conecta |
|---|---|---|
| Datos (scrapers listos: competencia, Google, redes, mapas) | **Apify** | Claude → Configuración → Conectores → Apify, o `claude mcp add apify "https://mcp.apify.com" -t http` |
| Navegador real (clic, escribir, navegar) | **Playwright MCP** (Microsoft) | `claude mcp add playwright npx @playwright/mcp@latest` |
| Investigar con fuentes | **Perplexity** | `claude mcp add --transport http perplexity https://api.perplexity.ai/mcp` (inicia sesión o usa tu API key) |
| Cola de publicaciones en redes | **Buffer** | Conector personalizado con `https://mcp.buffer.com/mcp` (OAuth) |

Links: https://github.com/apify/apify-mcp-server · https://github.com/microsoft/playwright-mcp · https://github.com/perplexityai/modelcontextprotocol · https://developers.buffer.com/guides/integrations/mcp.html

## Ojo
- Apify y Perplexity cobran por uso según su plan; revisa precios.
- Buffer: la conexión ve **toda** tu cuenta y `create_post` puede publicar al instante. Deja activadas las confirmaciones.
- Configura accesos mínimos y revisa lo que va a salir. Automatizar no es olvidarte del negocio.
