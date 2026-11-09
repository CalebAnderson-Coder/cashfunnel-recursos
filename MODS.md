# MODS: 4 mods para Claude Code (Cache Keeper, Goal Meter, Collision Guard y Recording Mode)

Recurso del video sobre mods de Claude Code. Brian Anderson / CashFunnel, noviembre de 2026.

Los **mods** son plugins que corren **dentro** de Claude Code. Pueden dibujar en pantalla (una línea sobre el prompt, una etiqueta en el pie o un panel lateral), añadir comandos con `/` e intervenir antes de que Claude use una herramienta.

- Repo oficial (licencia MIT): https://github.com/nateherkai/claude-code-mods
- Autor: Nate Herk. Estos mods no son míos; aquí te explico qué hacen y cómo instalarlos.

## Los mods del video (y uno extra del repo)
| Mod | Comandos | Para qué sirve |
|---|---|---|
| **Cache Keeper** | `/cache`, `/keepwarm`, `/board`, `/handoff` | Te muestra si el prompt cache de un chat está caliente o frío y cuánto costaría reescribirlo. Puede mantener calientes los chats grandes y te pregunta antes de mandar un mensaje caro a un chat grande con el cache frío. |
| **Goal Meter** | `/goals` | Una barra de progreso para `/goal`, armada con el plan de tareas del propio Claude, con tiempo transcurrido y ETA. |
| **Collision Guard** | `/guard` | Antes de que Claude edite un archivo que otro chat abierto cambió en los últimos 30 minutos, te pregunta: Proceed, Move to a worktree o Cancel. |
| **Recording Mode** (extra del repo) | `/rec`, `/rec strict`, `/rec off`, `/rec config` | Oculta en pantalla claves, datos personales y cifras de negocio mientras grabas. |

## Requisitos
- **Claude Code 2.1.287 o posterior.** Revísalo con `claude --version`. Funciona en la terminal y en la pestaña Code de la app de escritorio.
- **Mods activados en tu cuenta.** Anthropic los está activando de forma gradual. Ejecuta `claude plugin test` en cualquier carpeta:
  - Si dice "no hooks module to load", los mods ya pueden cargar.
  - Si dice "served off", todavía no están disponibles para ti. Cuando los activen no tienes que reinstalar nada.

## Instalación
Agrega el repo como marketplace de plugins:
```bash
claude plugin marketplace add nateherkai/claude-code-mods
```
Después instala los mods que quieras, un comando por mod:
```bash
claude plugin install cache-keeper@nateherk-mods
claude plugin install goal-meter@nateherk-mods
claude plugin install collision-guard@nateherk-mods
claude plugin install recording-mode@nateherk-mods
```
Abre un chat nuevo. Los mods cargan cuando empieza un chat, y `/reload-plugins` no los recarga.

- **Actualizar:** `claude plugin marketplace update nateherk-mods`, luego `claude plugin update <mod>@nateherk-mods` y abre un chat nuevo.
- **Quitar:** `claude plugin uninstall <mod>@nateherk-mods`.

## Límites honestos
- Necesitas Claude Code con un plan o una API de pago. Los mods son gratis; el uso del modelo no.
- En un plan de suscripción, los "costos" del cache se ven como uso contra tus límites, no como una factura aparte.
- Cache Keeper no garantiza un ahorro fijo. Depende del tamaño del chat, del tiempo que pase inactivo y de si el cache sigue caliente. Mantenerlo caliente usa pings pequeños al modelo, solo mientras `/keepwarm` está encendido.
- Recording Mode cambia lo que se ve en pantalla y lo que Claude puede abrir, no lo que se guarda. No atrapa todo, así que revisa tu grabación antes de publicarla.
- Los datos de los mods quedan en tu máquina, en `~/.claude/mods-data/`. Los mods no hacen llamadas de red propias, aparte de los pings de keep-warm.

## Costo
- Repo y mods: gratis (MIT).
- Claude Code: según tu plan.

Fuente: README, `marketplace.json` y `plugin.json` del repo oficial (commit `33a936f`, revisado el 9-nov-2026).
