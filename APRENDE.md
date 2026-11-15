# APRENDE: LearnHarness, la IA que sí te enseña

Recurso del video «Este repo está explotando en GitHub». Brian Anderson / CashFunnel, 15 de noviembre de 2026.

LearnHarness es una app de escritorio **gratis y open source** (licencia [AGPL-3.0](https://github.com/amosblomqvist/learnharness/blob/main/LICENSE)) que usa agentes de IA para enseñarte: primero averigua lo que ya sabes, luego te explica un paso a la vez y guarda lo aprendido en un grafo de conocimiento para la siguiente sesión.

- Sitio y descargas: [learnharness.ai](https://learnharness.ai)
- Código: [github.com/amosblomqvist/learnharness](https://github.com/amosblomqvist/learnharness) (unas 9,5 mil estrellas al 15-nov-2026)
- Documentación oficial: [docs/getting-started.md](https://github.com/amosblomqvist/learnharness/blob/main/docs/getting-started.md)
- Discord del proyecto: https://discord.gg/5tCHHQEB2e

**No es AULAIA.** AULAIA es otra herramienta (un aula/espacio de estudio con IA). LearnHarness es un proyecto distinto, de [amosblomqvist](https://github.com/amosblomqvist), pensado para medir lo que ya entiendes y enseñarte desde ahí. Si comentaste AULA o AULAIA en otro video, esa guía es otra.

Los datos de esta guía salen del README, de *Getting started* y de *Desktop builds and releases* del repo oficial, consultados el 15-nov-2026. Si algo cambia en una versión nueva, manda el sitio y el GitHub.

## Qué es (y qué no es)

LearnHarness no es un chat genérico ni un curso grabado. El flujo oficial es este:

1. **Medir.** Antes de enseñar, el agente busca dónde se te acaba la comprensión en lo que la lección necesita. Usa tus respuestas, tu confianza y tu razonamiento para saber por dónde empezar.
2. **Planear.** Arma un mapa de dependencias desde ese punto hasta tu meta. Tú ves el plan, y la lección se adapta si tu nivel resulta distinto.
3. **Enseñar.** Cada paso se apoya en algo que ya entiendes. Predices, recibes una explicación y compruebas si lo entendiste. Las confusiones se corrigen antes de construir encima.
4. **Practicar.** Sesiones aparte, con problemas variados, para que el conocimiento te salga sin que te lo nombren primero.

Lo que te enseñan se acumula en un **grafo de conocimiento** (proposiciones y cadenas de razonamiento, con enlace a las sesiones de origen). Las sesiones siguientes pueden retomar el grafo en lugar de empezar de cero. El grafo guarda ideas y conexiones, no una “nota” de tu habilidad.

También puedes importar notas, adjuntar archivos locales en la app de escritorio (PDF, fotos, etc.: el archivo se queda en tu máquina; el mensaje lleva la ruta) y, si lo configuras, usar dictado y búsqueda web.

## Costo

- **La app es gratis.** Open source bajo AGPL-3.0. El README oficial lo dice así: la app es gratis y abierta para siempre; si algún día cobran algo, será por conveniencia (claves gestionadas, hosting), nunca por funciones que puedas correr en local.
- **Tú pagas el modelo**, no una suscripción de LearnHarness ni un recargo suyo. La facturación depende de tu proveedor, de la CLI, de tu suscripción o de tu setup local.
- El **medidor de costo en vivo** estima solo costos de API conocidos. **No** incluye cargos de suscripción, de la CLI ni de un endpoint personalizado.

## Cómo se descarga, por sistema

Descarga desde [learnharness.ai](https://learnharness.ai) o desde [GitHub Releases](https://github.com/amosblomqvist/learnharness/releases). Las tres plataformas tienen actualizaciones dentro de la app.

- **macOS (Apple Silicon):** DMG firmado y notarizado. Arrastra la app a Aplicaciones. La tabla oficial de releases lista Apple Silicon, no Intel.
- **Windows (x64):** corre el instalador NSIS. Hoy va **sin firma**; Windows puede mostrar el aviso de “editor desconocido” o SmartScreen. Eso lo advierte el propio README.
- **Linux (x64):** el descargo principal es el **AppImage** (lo haces ejecutable y lo abres). También hay un `.deb` para Debian/Ubuntu; una actualización por `.deb` puede pedir contraseña de administrador.

Si prefieres correrlo desde el código: `npm ci`, `npm run plugins:setup` y `npm run dev` (http://localhost:3000). Ver [docs/development.md](https://github.com/amosblomqvist/learnharness/blob/main/docs/development.md).

## Cómo empezar

1. Instala la app (o ábrela en local).
2. Ve a **Settings → Providers** y conecta al menos un modelo (abajo está el detalle).
3. En Ajustes elige los modelos **Strong**, **Cheap** y **Vision**. No hay una selección de fábrica: las sesiones nuevas empiezan con Strong.
4. Entra a **Teach** y describe lo que quieres entender. El agente sondea tu punto de partida, te propone un plan y enseña con explicaciones y comprobaciones. Puedes aceptar o corregir el plan con naturalidad.
5. Usa los campos de **pensamiento** para explicar tu razonamiento, tus dudas o tu reacción, no solo la respuesta marcada. La confianza que indicas es **auto-reportada**, no una evaluación independiente. Puedes escribir o dictar.
6. Elige **Practice** cuando quieras problemas en lugar de una lección. Puedes partir del grafo o describir el material. Envíes tu razonamiento mientras trabajas; la solución comprometida del modelo se revela al terminar el problema.

Las sesiones se guardan en local, incluso cuando se compacta el contexto.

## Conexiones (proveedores de IA)

En **Settings → Providers** puedes configurar:

- **Claves de API de un proveedor:** usas tu propia cuenta y pagas las tarifas de ese proveedor (por ejemplo Anthropic, OpenAI o Google, u otros que la app soporte en esa versión).
- **Conexiones de suscripción:** ChatGPT, GitHub Copilot y Grok usan su propio inicio de sesión y los límites de esa cuenta. **No** caen en silencio a facturación por API.
- **[Claude Code](https://github.com/amosblomqvist/learnharness/blob/main/docs/claude-code.md):** un CLI instalado y autenticado por separado. Su propia configuración controla el ruteo y la facturación; no es una garantía de “solo suscripción”.
- **[Endpoint personalizado](https://github.com/amosblomqvist/learnharness/blob/main/docs/custom-providers.md):** un servidor compatible con OpenAI, incluido un servidor de modelo local. LearnHarness **no instala ni descarga modelos**.

La búsqueda web opcional (Tavily, Brave, Exa, Firecrawl u Ollama alojado) y el dictado (Deepgram) llevan claves aparte, también en Settings → Providers. La investigación puede visitar URLs conocidas sin clave de búsqueda.

## Límites honestos (léelos antes de instarla)

- **Almacenamiento local no es trabajo offline.** Chats, grafo, ajustes y claves viven en tu máquina (archivos que puedes inspeccionar). Pero los modelos corren a través de los proveedores que configuraste: las peticiones envían el contexto necesario. La investigación web y el dictado también contactan servicios externos.
- **El medidor de costo es solo de API.** No te va a mostrar lo que gasta una suscripción, la CLI o un endpoint propio.
- **macOS oficial: Apple Silicon.** Si tienes un Mac Intel, no asumas que hay un build firmado en la tabla actual de releases; confirma en el sitio el día que descargues.
- **Windows sin firma.** El aviso de SmartScreen es esperado, no un virus “oficialmente certificado”. Instálala solo desde [learnharness.ai](https://learnharness.ai) o desde las releases del repo oficial.
- **No instala modelos locales.** Si quieres un modelo en tu máquina, lo montas tú (por ejemplo un servidor compatible con OpenAI) y lo conectas como endpoint personalizado.
- **Adjuntar un archivo no es un upload.** En la app de escritorio se envía la ruta local; el original se queda donde está. En un navegador común no puedes exponer esas rutas igual: puedes pegar la ruta completa.
- **La confianza es auto-reportada.** El agente la usa como señal, no como una nota objetiva de lo que sabes.

## Créditos

- LearnHarness — [amosblomqvist](https://github.com/amosblomqvist) y contribuidores, licencia AGPL-3.0.
- Sitio oficial: https://learnharness.ai
- Música del video: «Digital Lemonade» — Kevin MacLeod (incompetech.com). Licensed under Creative Commons: By Attribution 4.0 License. http://creativecommons.org/licenses/by/4.0/
