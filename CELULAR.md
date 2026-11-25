# CELULAR: mirroir, para que Claude Code use tu iPhone de verdad

Recurso del video sobre mirroir-mcp. Brian Anderson / CashFunnel, noviembre de 2026.

**mirroir-mcp** es una herramienta **gratis y open source (licencia Apache-2.0)** que deja a tu agente de IA (Claude Code, Codex, Cursor y otros clientes MCP) usar **tu iPhone real**: lee la pantalla, toca, desliza, escribe y abre apps, a través de la **Duplicación del iPhone** (iPhone Mirroring) de tu Mac. No se instala nada en el teléfono, no hace falta Modo Desarrollador ni Xcode, y las apps siguen con tu sesión ya iniciada: no le das tu contraseña a nadie.

La palabra clave del video es **CELULAR**.

## Enlaces oficiales

- **Repo:** https://github.com/jfarcand/mirroir-mcp (licencia Apache-2.0)
- **Sitio y demos:** https://mirroir.dev
- **Guía para que tu agente lo instale paso a paso:** https://github.com/jfarcand/mirroir-mcp/blob/main/docs/onboarding.md
- **Permisos y apps bloqueadas:** https://github.com/jfarcand/mirroir-mcp/blob/main/docs/permissions.md
- Este software no es mío: te dejo el repo oficial y una guía con límites claros. Instálalo solo desde el repo, desde npm (`mirroir-mcp`) o desde el tap oficial de Homebrew.

## Requisitos

- Una **Mac con macOS 15 o más nuevo**.
- Un **iPhone con iOS 18 o más nuevo**, con la **misma cuenta de Apple** que la Mac.
- **Duplicación del iPhone disponible en tu país**: Apple no la ofrece en todas partes (por ejemplo, no está en la Unión Europea).
- Un agente compatible con MCP: Claude Code, Codex, Cursor, Claude Desktop, VS Code u otro.
- No funciona en Windows ni con Android: depende de la Duplicación del iPhone de macOS.

## Cómo instalarlo (2 caminos)

### A. Que tu agente lo haga por ti

Pega esto en Claude Code o Codex:

```text
Set up mirroir-mcp so you can drive my iPhone: follow https://github.com/jfarcand/mirroir-mcp/blob/main/docs/onboarding.md step by step, and finish by reading back what my iPhone screen shows.
```

### B. Con un comando

```bash
npx -y mirroir-mcp install    # o: brew tap jfarcand/tap && brew install mirroir-mcp
npx -y mirroir-mcp doctor     # te dice qué falta arreglar
```

Para conectarlo a mano a tu agente:

```bash
claude mcp add --transport stdio mirroir -- npx -y mirroir-mcp   # Claude Code
codex mcp add mirroir -- npx -y mirroir-mcp                      # Codex
```

La primera vez, macOS te pide permisos de **Grabación de pantalla** y **Accesibilidad**: dáselos a la app que indique `doctor`.

## Qué le puedes pedir

- **Flujos enteros entre apps:** por ejemplo, leer el tiempo de viaje en Waze y mandarlo a un canal de Slack, o armar una playlist en Spotify (son demos oficiales del proyecto).
- **Probar tus apps en un iPhone real:** que pruebe una pantalla de login en Expo Go, toque los botones y te diga qué falla.
- **Tareas aburridas del celular:** lo que hoy haces a mano, paso a paso.
- Lo que aprende una vez lo puede guardar como *skill* y repetirlo después sin gastar tokens (`mirroir test`).

## Tú mandas: seguridad

- **Solo lectura por defecto.** Las herramientas que cambian algo (tocar, abrir enlaces…) quedan ocultas hasta que tú las permites en `~/.mirroir-mcp/permissions.json`.
- **Bloquea apps.** Con `blockedApps` el agente no puede abrir las apps que tú digas:

```json
{
  "allow": ["tap", "open_url"],
  "blockedApps": ["Wallet", "PayPal", "Tu banco"]
}
```

  Usa el nombre exacto que muestra el iPhone debajo del ícono.
- **Nunca escribe tus contraseñas** ni aprueba Touch ID/Face ID por ti.
- **Botón de apagado:** cierra la Duplicación del iPhone, bloquea la Mac o cierra tu agente y se detiene al instante.

## Límites (léelos antes)

- `blockedApps` revisa las apps por su nombre: los íconos sin nombre (el Dock, carpetas, la Biblioteca de apps, el selector de apps) **no** se revisan. No dependas solo de eso para tu banco: no le des permisos de toque si no lo vas a vigilar.
- Mientras el agente usa el teléfono, en macOS posteriores a 26 la ventana de la Duplicación pasa al frente.
- Lee la pantalla con OCR local (gratis, en tu Mac) por defecto; el modo de visión por IA lee mejor los íconos, pero gasta unos 25.000 tokens por lectura.
- Es un proyecto de un desarrollador independiente y se mueve rápido: actualiza con `npx -y mirroir-mcp update` y revisa su CHANGELOG.
- Úsalo solo en **tu** iPhone y con **tus** cuentas.

---

¿Te sirvió? Comenta en el video qué tarea del celular le darías primero.
