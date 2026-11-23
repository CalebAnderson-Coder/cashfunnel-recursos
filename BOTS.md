# BOTS: OpenMausBot, tu equipo de bots de IA gratis y open source

Recurso del video sobre OpenMausBot. Brian Anderson / CashFunnel, noviembre de 2026.

**OpenMausBot** es una app **gratis y open source (Apache 2.0)** con la idea de Grok Bot: una lista de bots con los que chateas como si fueran contactos. Cada bot tiene su personalidad, su modelo, su memoria de la conversación, su propia computadora y sus apps conectadas. El propio proyecto se presenta como alternativa open source a Grok Bot, Meta Muse, OpenAI dots y Cue de Manus.

No es un modelo de IA nuevo ni un servicio en la nube al que te suscribes. Los bots corren sobre los agentes que ya tienes instalados (Claude Code, Codex o Grok CLI), con tu login y tu plan de siempre.

La palabra clave del video es **BOTS**.

## Enlaces oficiales

- **Repo:** https://github.com/milind-soni/OpenMausBot (licencia Apache 2.0, unas **27.100 estrellas** el 23-nov-2026)
- **Descargas (Releases):** https://github.com/milind-soni/OpenMausBot/releases/latest (versión v0.1.177 del 22-nov-2026)
- **Sitio:** https://www.openmausbot.com
- **Autor:** [Milind Soni](https://github.com/milind-soni) y colaboradores. Este software no es mío: te dejo el repo oficial y una guía con límites claros.

## Qué hace (y qué no)

- **Un bot por trabajo.** Creas varios bots y cada uno usa el modelo que elijas (Claude o Codex, por ejemplo). Puedes cambiarle el modelo a mitad de la conversación.
- **Cada bot tiene una computadora.** En el panel «Computer» el bot abre un escritorio Linux en la nube, una VM local aislada o, si lo activas tú, tu propia computadora (macOS y Ubuntu Xorg). Ves la pantalla en vivo mientras trabaja.
- **Pide permiso antes de actuar.** Los comandos, los cambios de archivos y las preguntas aparecen como tarjetas en el chat: Permitir, Denegar o responder.
- **Apps conectadas.** Gmail, Slack, GitHub, Notion, Linear y cientos más a través de Composio (el repo habla de **más de 500 apps**). Conectas una vez por OAuth y todos los bots las pueden usar.
- **Rutinas.** Tareas programadas una vez, en días de semana elegidos o cada 5 a 1.440 minutos.
- **Canales.** Trabajo, Personal y cada proyecto por separado, cada uno con sus instrucciones y su equipo de bots.
- **No es** un sustituto de tu plan de IA ni un agente que trabaje gratis: el modelo lo pagas tú con el plan que ya tienes.

## Requisitos

- **macOS** (Apple silicon o Intel), **Windows x64** o **Ubuntu 24.04 x64** (Fedora con soporte de la comunidad).
- Al menos un agente instalado y con sesión iniciada: [`claude`](https://claude.com/claude-code), [`codex`](https://github.com/openai/codex) o [`grok`](https://x.ai/cli). Aparecen solos en el selector de modelos.
- Opcional, según lo que quieras activar:
  - Una key de proyecto de **Composio** para las apps (Gmail, Slack, Notion…).
  - Una key de **Boat** (boat.dev) para la computadora en la nube de cada bot.
  - Una key de ElevenLabs o Fish Audio si quieres que los bots hablen.

## Instalación (5 pasos)

1. Instala y abre sesión en al menos un agente: Claude Code, Codex o Grok CLI.
2. Descarga el instalador de tu sistema desde la [última versión](https://github.com/milind-soni/OpenMausBot/releases/latest):
   - Mac Apple silicon: `OpenMausBot.dmg` · Mac Intel: `OpenMausBot-intel.dmg` (firmados y notarizados; los arrastras a Aplicaciones).
   - Windows: `OpenMausBot-setup.exe`. Todavía no está firmado, así que SmartScreen dice «editor desconocido»: **Más información → Ejecutar de todas formas**. Déjalo en la carpeta donde lo instala.
   - Ubuntu 24.04: `OpenMausBot-amd64.deb` (con APT) o el AppImage (beta).
3. Abre la app y crea tu primer bot con **＋**. Ponle nombre, personalidad y modelo.
4. Opcional: en **App Settings** (el engranaje de abajo en la barra lateral) pega la key de Composio para conectar tus apps, y la de Boat si quieres la computadora en la nube.
5. Dale una tarea en el chat y aprueba las tarjetas que te muestre.

Si prefieres la terminal o un servidor (Node 24 o más nuevo):

```sh
npm install -g openmausbot
openmausbot
```

O sin instalar nada global: `npx openmausbot`. La primera vez te guía para elegir el acceso a la IA, iniciar sesión y elegir el modelo.

## Ejemplos reales (del README oficial)

- **Rutina programada:** una tarea que corre una vez, en los días de semana que elijas o cada 5 a 1.440 minutos, con el modelo y la computadora del bot. Si la corrida anterior sigue activa, se salta la siguiente para no acumular trabajo.
- **Evento de una app:** «cada vez que me llegue un correo de Acme, redacta una respuesta». El bot crea el disparador y tú lo apruebas. Gmail se revisa cada 15 minutos; Slack y GitHub llegan al instante.
- **Un equipo completo desde un archivo Markdown:** en [BotMRR](https://botmrr.io) eliges un equipo armado (bots, canales, rutinas) y lo importas con **Add to OpenMausBot**. Las conexiones quedan apagadas hasta que las apruebes y las rutinas llegan en pausa.
- **Compartir un bot:** le pides «publish yourself to GitHub» y te da una tarjeta con sus instrucciones y skills, sin chats, memoria ni keys.

Ideas para empezar, como en el video: un bot que ordena tu correo y redacta respuestas, uno que investiga guiones («búscame las herramientas de IA en tendencia de esta semana») y otro que resume un guion en escenas para editar.

## Límites honestos

- **El modelo no es gratis.** La app no cobra, pero cada bot usa tu plan de Claude, ChatGPT/Codex o Grok, con sus límites de uso.
- **La computadora en la nube es de un tercero.** Boat (boat.dev) es de pago después de la prueba, y usar una computadora en la nube puede generar cargos. Composio también tiene su propia cuenta y sus propios términos.
- **Proyecto joven.** El repo se creó en agosto de 2026 y saca versiones casi a diario. No es un producto con soporte comercial.
- **Windows sin firma.** El instalador de Windows todavía no está firmado por código.
- **Control de tu propia computadora:** solo en macOS y Ubuntu Xorg, y solo si lo activas. En Ubuntu Wayland está desactivado.
- **Keys en texto plano en algunos casos:** las keys que guardas con `openmausbot setup` o en el servidor quedan sin cifrar en un `config.json` privado. La app de escritorio cifra las del proveedor de IA con el sistema operativo.
- **Permisos:** dale a cada bot solo las apps y permisos que necesita, y revisa lo que hace antes de dejar que envíe correos o publique por ti. Mira también las guías [PERMISOS](PERMISOS.md) y [SEGURO](SEGURO.md).
- **Sin criptomoneda:** el proyecto no tiene token. Cualquier moneda con el nombre OpenMausBot, Maus o SupaMaus no es del proyecto.

## Costo

- App y código: gratis (Apache 2.0). La carpeta `enterprise/` del repo tiene su propia licencia de código disponible; si la borras, lo que queda es la edición open source.
- Modelo de IA: el plan que ya pagas (Claude, ChatGPT/Codex o Grok).
- Opcionales de terceros: Composio (apps conectadas), Boat (computadora en la nube, de pago después de la prueba) y voces de ElevenLabs o Fish Audio.

## Créditos y fuentes

Consultadas el 23-nov-2026, America/Caracas:

- README, licencia y Releases del repo oficial: https://github.com/milind-soni/OpenMausBot
- Sitio del proyecto: https://www.openmausbot.com

OpenMausBot es un proyecto independiente de Milind Soni y sus colaboradores, inspirado en Grok Bot. No está afiliado a xAI, Meta, OpenAI ni Manus. Guía educativa de Brian Anderson / CashFunnel.
