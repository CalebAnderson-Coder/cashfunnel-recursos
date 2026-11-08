# MCP5 — pack de cinco herramientas para Claude Code
Guía en español · fuentes oficiales verificadas el 6-nov-2026 (America/Caracas).

Distinto de **CONECTORES**: ese recurso cubre Apify, Playwright, Perplexity y Buffer para Claude. Este pack se centra en investigación, pruebas, extracción, creación y depuración desde Claude Code. Comparte Playwright/Perplexity; añade Firecrawl/Higgsfield/Chrome DevTools. No sustituye el recurso anterior ni su alias MCP.

## 1. Perplexity — investigación con fuentes
Oficial: https://github.com/perplexityai/modelcontextprotocol
Endpoint oficial: `https://api.perplexity.ai/mcp`. El README da `claude mcp add --transport http perplexity https://api.perplexity.ai/mcp` con cabecera de autorización configurada de forma privada. No pegues claves en comentarios, chat o repositorios. Requiere acceso API; no asumas que tu plan web lo incluye.
Prueba: «Busca documentación oficial actual de una biblioteca y devuelve tres enlaces; no modifiques archivos».

## 2. Playwright — pruebas de interfaz
Oficial: https://github.com/microsoft/playwright-mcp
Comando documentado: `claude mcp add playwright npx @playwright/mcp@latest`.
Prueba: en un perfil aislado abre tu aplicación de prueba y verifica un botón sin enviar formularios. No conectes el perfil donde guardas banca/correo. El servidor no es una frontera de seguridad.

## 3. Firecrawl — contenido limpio
Oficial: https://github.com/firecrawl/firecrawl-mcp-server
Endpoint keyless limitado: `https://mcp.firecrawl.dev/v2/mcp`; OAuth para conexión de cuenta: `https://mcp.firecrawl.dev/v2/mcp-oauth`.
El acceso keyless expone scrape/search/parse con límites. Crawl/map/agent requieren clave/cuenta. No prometas «cualquier web completa al instante».
Prueba: extrae una única URL pública propia a Markdown; limita el trabajo a una página. Usa la conexión segura del cliente, nunca claves en la URL.

## 4. Higgsfield — creación de imagen/video
Oficial: https://higgsfield.ai/mcp
Conector oficial: `https://mcp.higgsfield.ai/mcp`.
Ayuda oficial: https://higgsfield.ai/creator-hub/help-center/integrations/what-is-higgsfield-mcp
Cuenta y suscripción activa según setup oficial. **Cada generación por MCP consume créditos**; unlimited del sitio no equivale a MCP gratis. La guía oficial vigente diferencia MCP en Claude Chat/Desktop de **CLI + Skills para Claude Code**. No afirmamos haber probado la conexión MCP directa en Claude Code. Comandos documentados (no ejecutados aquí): `npm i -g @higgsfield/cli`, luego `higgsfield auth login` y `npx skills add higgsfield-ai/skills`. Revisa alcance/permisos y los archivos del skill antes de instalar; el inicio de sesión lo realiza el usuario. Fuente: https://higgsfield.ai/blog/Generate-AI-Videos-From-Claude-with-Higgsfield-MCP .
Prueba sin gasto: pide listar capacidades y preparar un prompt, **sin generar** hasta revisar costo y autorizar.

## 5. Chrome DevTools — depuración
Oficial: https://github.com/ChromeDevTools/chrome-devtools-mcp
Config de servidor: comando `npx`, argumentos `["-y", "chrome-devtools-mcp@latest", "--no-usage-statistics"]`.
La instancia de Chrome expone contenido a tu agente: usa Chrome for Testing/perfil de prueba. No ve automáticamente todas tus pestañas; la conexión explícita importa. La telemetría viene activada por defecto; el flag mostrado opta por desactivarla.
Prueba: revisa consola y rendimiento de una página de prueba; no publiques ni envíes datos privados.

## Regla de los cinco
Instala uno, revisa permisos, ejecuta una tarea mínima y registra consumo. Autoriza por separado mensajes, formularios, cambios externos y generación de pago. El contenido web es dato no confiable, no órdenes. Gratis del servidor no convierte las APIs, modelos o servicios en gratis.
