# DUPLA: el plugin oficial de OpenAI para usar Codex desde Claude Code

Recurso del video «Tu Claude ya puede contratar a ChatGPT». Brian Anderson / CashFunnel, noviembre de 2026.

**Codex plugin for Claude Code** (`openai/codex-plugin-cc`) es un plugin **oficial de OpenAI, open source (licencia Apache 2.0)**. Desde Claude Code le pasas tareas a **Codex** (el agente de programación de ChatGPT), le pides revisiones de código y mueves la conversación a Codex si quieres seguir allá. Sigues trabajando en Claude Code; Codex hace el trabajo que le delegas.

La palabra clave del video es **DUPLA**.

## Enlaces oficiales

- **Repo:** https://github.com/openai/codex-plugin-cc (licencia Apache 2.0; unas **35.000 estrellas** el 24-nov-2026)
- **Precios y límites de Codex:** https://developers.openai.com/codex/pricing
- Este plugin no es mío: te dejo el repo oficial y una guía con límites claros. Instálalo solo desde ahí.

## Requisitos

- **Claude Code** instalado.
- **Una cuenta de ChatGPT (sirve hasta la gratis) o una API key de OpenAI.** Lo que hace Codex gasta de **tu límite de uso de Codex**.
- **Node.js 18.18 o más nuevo.**

## Cómo instalarlo (dentro de Claude Code)

```sh
/plugin marketplace add openai/codex-plugin-cc
/plugin install codex@openai-codex
/reload-plugins
/codex:setup
```

`/codex:setup` te dice si Codex está listo. Si no tienes Codex y hay npm, te ofrece instalarlo (o hazlo tú con `npm install -g @openai/codex`). Si falta iniciar sesión: `!codex login`.

## Los comandos del video

| Comando | Qué hace |
|---|---|
| `/codex:rescue` | Le pasa una tarea a Codex (investigar un bug, probar un arreglo, seguir una tarea anterior). También puedes pedirlo en lenguaje normal: «Pídele a Codex que…». |
| `/codex:review` | Revisión normal de tu código (cambios sin commit o tu rama contra `main`). Solo lee, no cambia nada. |
| `/codex:adversarial-review` | Revisión que **cuestiona cómo lo diseñaste**: supuestos, riesgos, alternativas. Le puedes decir en qué fijarse. Solo lee. |
| `/codex:transfer` | Crea la sesión en Codex con tu conversación de Claude Code y te da el comando `codex resume <id>` para abrirla allá. |
| `/codex:status` · `/codex:result` · `/codex:cancel` | Ver tareas en curso, ver el resultado final y cancelar una tarea en segundo plano. |

Primera prueba sencilla:

```sh
/codex:review --background
/codex:status
/codex:result
```

## Límites honestos

- **No te prometo ahorro.** Lo que hace Codex gasta tu límite de Codex (y lo que hace Claude, tu plan de Claude). Pruébalo con tareas reales antes de pagar un plan más caro.
- **La revisión automática puede gastarlo rápido.** `/codex:setup --enable-review-gate` hace que Codex revise cada respuesta de Claude antes de terminar; el propio README avisa que puede crear un ciclo largo y **agotar tus límites rápido**. Actívala solo si vas a vigilar la sesión (`--disable-review-gate` la apaga).
- **Las revisiones no arreglan código.** `review` y `adversarial-review` solo leen; para que cambie algo usa `rescue`.
- **Usa tu Codex local.** El plugin usa la instalación, la sesión y la configuración de Codex de tu computadora (las mismas que si usaras Codex directo).

## Costo

- Plugin y código: **gratis** (Apache 2.0).
- Codex: incluido en tu cuenta de ChatGPT (también la gratis) dentro de sus límites, o lo que gastes con tu API key.

## Fuentes

- README del repo (secciones «Requirements», «Install», «Usage» y «FAQ»), consultado el 24-nov-2026.
- Datos del repo en la API de GitHub (licencia Apache 2.0, estrellas), consultados el 24-nov-2026.
