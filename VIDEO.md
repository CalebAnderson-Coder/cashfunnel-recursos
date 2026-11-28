# VIDEO: Gemini API CLI, para que tu agente analice videos y Shorts de YouTube

Recurso del video sobre Gemini API CLI. Brian Anderson / CashFunnel, 28 de noviembre de 2026.

**Gemini API CLI** (el comando se llama `gemini-api`) es una herramienta **gratis y open source (licencia Apache 2.0)** de Google, del repo [google-gemini/gemini-api-cli](https://github.com/google-gemini/gemini-api-cli). Según su README, le da a un agente con acceso a la terminal, como Claude Code, la capacidad de usar los modelos de Gemini: generar imágenes, voz o video, y **analizar archivos y links de YouTube**. Tu agente sigue siendo Claude Code; Gemini es el que «mira» el video y le devuelve la respuesta.

La idea del reel: pegas el link de un video o Short público de YouTube y le preguntas a Gemini en qué segundo está el gancho y dónde están los cortes.

Esta guía te cuenta qué necesitas, los tres pasos de instalación, un plan de prueba y los límites. Las explicaciones son nuestras; los comandos y las cifras salen de la documentación oficial de Google, consultada el 28-nov-2026. La herramienta está en **beta**: Google avisa que puede haber cambios entre versiones, así que si algo no coincide, manda la documentación.

## Antes de empezar: tres avisos

- **En el plan gratis, Google puede usar lo que envías.** Los términos de Google dicen que en el uso sin costo (como Google AI Studio y la cuota gratis de la API de Gemini) usan lo que envías y las respuestas para mejorar sus productos, y que personas pueden leer y anotar esos datos (los desconectan de tu cuenta antes). Piden **no enviar información sensible, confidencial ni personal**. La tabla de precios de `gemini-4-hydrogen` lo confirma: «Used to improve our products: Yes» en el plan gratis, «No» en el de pago. Con videos públicos de YouTube el riesgo es menor, pero tu pregunta también se envía: **no subas videos privados ni de clientes, y no pongas datos personales en la pregunta**.
- **Solo videos públicos de YouTube.** La documentación dice que no se pueden usar videos privados ni «no listados».
- **La función de YouTube está en vista previa.** Google dice que es gratis por ahora, pero que los precios y los límites **probablemente cambien**.

## Costo real

- **La herramienta es gratis** (Apache 2.0). No cobra por instalarla.
- **El análisis con la clave gratis no cuesta.** En la tabla de precios de Google, el modelo `gemini-4-hydrogen` tiene entrada y salida «Free of charge» en el plan gratis. Eso sí, hay topes: para YouTube, **hasta 8 horas de video por día** en el plan gratis. Los topes de pedidos por minuto o de tokens los muestra tu panel de Google AI Studio; **no los verificamos**.
- **Si activas el pago, sí pagas.** En el plan de pago, la misma tabla marca 1,50 USD por millón de tokens de entrada y 7,50 USD por millón de tokens de salida (incluye los tokens de «pensar»). No hace falta para probar. Los precios pueden cambiar: revísalos el día que contrates.
- **Tu agente va aparte.** Claude Code lo pagas con tu plan de Claude; no verificamos su precio hoy.
- Algunas cuentas o proyectos nuevos pueden necesitar «verificación del proyecto» antes de usar el plan gratis. La documentación lo menciona para proyectos importados o creados fuera de AI Studio.

## Cómo se instala: tres pasos

### 1. Instala Gemini API CLI

En Mac o Linux (el comando del README):

```bash
curl -fsSL https://raw.githubusercontent.com/google-gemini/gemini-api-cli/main/scripts/install.sh | bash
```

En Windows (PowerShell):

```powershell
iwr -useb https://raw.githubusercontent.com/google-gemini/gemini-api-cli/main/scripts/install.ps1 | iex
```

Como todo `curl ... | bash` o `iwr ... | iex`, ese comando ejecuta lo que descarga. Si prefieres revisar antes, el README también ofrece binarios para descargar en [GitHub Releases](https://github.com/google-gemini/gemini-api-cli/releases) o `go install`. Comprueba que quedó instalado con `gemini-api --version`.

### 2. Saca una clave gratis en Google AI Studio y guárdala con un comando

1. Entra a [aistudio.google.com/apikey](https://aistudio.google.com/apikey) con tu cuenta de Google y crea una clave de API. **La clave la creas tú, a mano; no se la pidas a tu agente.** Es un secreto: no la publiques ni la pegues en un chat.
2. Guárdala con el comando que da la documentación:

```bash
gemini-api configure --api-key "TU_CLAVE"
```

Según la documentación, la guarda en el llavero de tu sistema (Keychain en Mac, Credential Manager en Windows, Secret Service en Linux). En Linux sin escritorio se usa `--no-keyring` para guardarla en un archivo de configuración. Con `gemini-api whoami` ves qué clave está activa, enmascarada.

**Ojo con esta trampa que avisa la skill de Google:** si ya tienes una variable `GEMINI_API_KEY` en tu terminal, esa **gana** sobre la clave guardada. Si no sabes por qué cuenta se está usando, corre `gemini-api whoami`.

### 3. Instala su skill para Claude Code

Una skill es una instrucción empaquetada que el agente lee cuando la necesita. La de Google se llama `gemini-api-cli` y vive en el repo [google-gemini/gemini-skills](https://github.com/google-gemini/gemini-skills). El comando que da la documentación de Google AI Studio:

```bash
npx skills add google-gemini/gemini-skills --skill gemini-api-cli
```

El instalador te pregunta para qué agente la quieres. Agrega `--global` si la quieres para todos tus proyectos y no solo para la carpeta actual.

La alternativa que da el README de las skills es instalarla como plugin dentro de Claude Code (instala el paquete completo de Gemini, no solo esta skill):

```
/plugin marketplace add google-gemini/gemini-skills
/plugin install gemini-skills@gemini-skills
```

El README de Gemini API CLI menciona también un comando `gemini-api install-skill`. **Al 28-nov-2026 todavía no está en la versión publicada (v0.5.0, del 20-nov)**: lo probamos y esa versión responde «unknown command». Usa uno de los dos caminos de arriba.

## Cómo se usa

Primero verifica sin gastar nada. `--dry-run` **no hace ninguna llamada**: solo muestra qué se enviaría, con las credenciales ocultas. Es la recomendación del propio README:

```bash
gemini-api analyze "En qué segundo está el gancho" -i "https://www.youtube.com/watch?v=ID_DEL_VIDEO" --dry-run
```

En esa vista previa tiene que aparecer `"model": "gemini-4-hydrogen"`. Ese es el modelo por defecto de `analyze` en la versión v0.5.0; si quieres fijarlo, añade `-m gemini-4-hydrogen`. Para ver los modelos disponibles para tu clave existe `gemini-api models list --all`.

Cuando la vista previa se vea bien, quita `--dry-run`:

```bash
gemini-api analyze "Describe los primeros 3 segundos y dime en qué segundo está cada corte" -i "https://www.youtube.com/watch?v=ID_DEL_VIDEO"
```

Con la skill instalada, también puedes pedírselo a Claude Code en lenguaje normal: pega el link y pregunta, por ejemplo, por los primeros tres segundos. Claude Code llama a `gemini-api` por ti.

**Qué ve Gemini.** Según la documentación, Gemini toma **un cuadro por segundo (1 FPS)** y le pone una marca de tiempo cada segundo. Funciona bien para la mayoría de los videos, pero **puede perder detalles en movimientos rápidos o cambios de escena muy seguidos**. Sirve para preguntas como «¿en qué segundo aparece el gancho?» o «¿cuántos cortes hay?». No es para contar cuadros uno por uno.

**Varios videos a la vez.** `-i` se puede repetir. La documentación dice que, con los modelos Gemini 2.5 y posteriores, caben **hasta 10 videos por pedido**:

```bash
gemini-api analyze "¿Qué ganchos se repiten en estos Shorts?" \
  -i "https://www.youtube.com/watch?v=ID_1" \
  -i "https://www.youtube.com/watch?v=ID_2" \
  --dry-run
```

(Agrega hasta diez `-i`. Quita `--dry-run` cuando la vista previa se vea bien.)

## Plan de prueba: primero un Short, después un lote de 10

1. **Un solo Short real, con `--dry-run`.** Confirma el modelo y que el link quedó bien escrito. La documentación solo muestra links con la forma `youtube.com/watch?v=ID`; si el link de un Short viene como `youtube.com/shorts/ID` y falla, pásalo a la forma `watch?v=ID`.
2. **El mismo Short, sin `--dry-run`.** Pregunta por los primeros tres segundos y compáralo con lo que ves tú. Si Gemini se equivoca en un corte rápido, ya sabes qué esperar de 1 FPS.
3. **Un lote de 10 Shorts de un mismo creador, primero con `--dry-run`.** Revisa que estén los diez links y que sean públicos.
4. **El lote de 10 sin `--dry-run`.** Pregunta qué ganchos se repiten.
5. **Antes de publicar nada con lo que sacaste,** revisa a mano un par de resultados. Gemini puede equivocarse.

**Para tener una idea de tamaño** (aritmética nuestra, con la cifra de la documentación de unos 100 tokens por segundo de video a la resolución por defecto): un Short de 1 minuto son unos 6.000 tokens, y diez de 1 minuto unos 60.000. Eso cabe en la ventana del modelo (1.048.576 tokens). En horas de video son 10 minutos, lejos de las 8 horas diarias del plan gratis.

## Límites honestos

- **Plan gratis: Google puede usar lo que envías.** No subas nada privado o de clientes. Con billing activado, la tabla de precios dice que ya no se usa para mejorar productos, pero entonces pagas.
- **Máximo 8 horas de YouTube al día en el plan gratis.** En el de pago, la documentación dice que no hay tope por duración. No verificamos a qué hora se reinicia el contador.
- **Solo videos públicos.** Privados y no listados no sirven.
- **1 cuadro por segundo.** Puede perder detalles en cortes muy rápidos.
- **Hasta 10 videos por pedido.** No más.
- **Vista previa y beta.** La función de YouTube y la herramienta pueden cambiar. Si un comando falla, revisa la versión y la documentación.
- **Los topes de pedidos por minuto del plan gratis no los verificamos.** Si te sale un error de cuota, espera o baja la cantidad de videos.
- **El resultado es una lectura de IA, no una medición exacta.** Revísalo antes de apoyarte en él.
- **No es de Anthropic ni de Claude.** Es una herramienta de Google que usas desde tu agente.

## Créditos

- Gemini API CLI: [google-gemini/gemini-api-cli](https://github.com/google-gemini/gemini-api-cli), licencia Apache 2.0, de Google. No es un producto mío ni tengo relación con el proyecto.
- Skill `gemini-api-cli`: [google-gemini/gemini-skills](https://github.com/google-gemini/gemini-skills), licencia Apache 2.0.

## Fuentes

Consultadas el 28-nov-2026, America/Caracas:

- README de Gemini API CLI (instalación, clave, `configure`, `--dry-run`, `analyze` con YouTube, `gemini-4-hydrogen` por defecto): https://raw.githubusercontent.com/google-gemini/gemini-api-cli/main/README.md
- Documentación oficial de la CLI (beta, instalación, `configure`, `whoami`, `--dry-run`): https://aistudio.google.com/docs/cli
- Licencia y versión publicada (API de GitHub; v0.5.0 del 20-nov-2026): https://api.github.com/repos/google-gemini/gemini-api-cli y https://api.github.com/repos/google-gemini/gemini-api-cli/releases/latest
- Skill (instalación con `npx skills add`): https://aistudio.google.com/docs/coding-agents y https://github.com/google-gemini/gemini-skills (README y `skills/gemini-api-cli/SKILL.md`)
- Entender video: YouTube en vista previa, 8 horas al día, 10 videos por pedido, solo públicos, 1 FPS, tokens por segundo: https://ai.google.dev/gemini-api/docs/video-understanding
- Modelo `gemini-4-hydrogen` (código del modelo y límites de contexto): https://ai.google.dev/gemini-api/docs/models/gemini-4-hydrogen
- Precios y «Used to improve our products»: https://ai.google.dev/gemini-api/docs/pricing
- Uso de datos en el plan gratis: https://ai.google.dev/gemini-api/terms#data-use-unpaid
- Claves de API: https://aistudio.google.com/docs/api-key
- Prueba local de la versión v0.5.0 (binario oficial verificado con su `checksums.txt`): `analyze ... --dry-run` muestra `gemini-4-hydrogen`; `install-skill` no existe en esa versión.

---
Si quieres aprender a hacer reels con IA paso a paso, la comunidad «Contenido en Sistema» en Skool es gratis: https://www.skool.com/primer-empleado-ia-6500

---

## ¿Vienes del video de HeyGen que liberó una herramienta gratis para que tu agente haga videos?

Esta es la guía anterior de VIDEO, del 18 de noviembre de 2026, tal como se publicó: HyperFrames. Se mantiene aquí completa porque hay gente que la sigue pidiendo. Solo se bajó un nivel a los títulos para que quepan debajo de esta sección; el texto no cambió.

## VIDEO: HyperFrames, la herramienta gratis de HeyGen para que tu agente haga videos

Recurso del video «HeyGen liberó gratis una herramienta para que tu agente haga videos». Brian Anderson / CashFunnel, 18 de noviembre de 2026.

**HyperFrames** es un framework **gratis y open source** del repo [heygen-com/hyperframes](https://github.com/heygen-com/hyperframes). Según su README, convierte HTML, CSS, media y animaciones en videos MP4 deterministas. El tagline del repo: «Write HTML. Render video. Built for agents.» Licencia [Apache 2.0](https://github.com/heygen-com/hyperframes), «with no per-render fees or commercial-use thresholds.» El README también dice que se usa en producción en HeyGen.

Los datos de esta guía salen del README y de la página del repo citados en el paquete del 18-nov-2026 (America/Caracas). Si una versión nueva cambia un comando o una cifra, mandan el GitHub y el sitio.

### Costo

- **El repo es gratis** (Apache 2.0) y **no cobra por cada video** («no per-render fees»). El render se hace en tu computadora o en Docker («Render locally or in Docker»).
- **Tú pones el entorno.** El README pide **Node.js 22+ y FFmpeg**. No afirmamos que el agente los instale solo, ni que esos programas sean gratis: no se verificó en el paquete.
- **No es “todo gratis para siempre”.** Dos de las nueve skills llevan la etiqueta **HyperFrames Pro**. El paquete no abrió una página de precios, así que aquí no hay un precio ni un nombre de plan.
- Para usarlo en Claude Code necesitas Claude Code (un plan de pago de Claude o la API). HyperFrames no trae un modelo propio.

### Cómo se instala en Claude Code

El README indica **dos comandos**:

```
claude plugin marketplace add heygen-com/hyperframes
claude plugin install hyperframes@hyperframes
```

El README dice: «HyperFrames ships 9 skills.» No enumeramos aquí qué hace cada una: hay que reabrir el README el día que las instales, porque esa lista puede cambiar.

### Cómo se usa (según el repo)

La idea es esta: **tú describes el video, el agente escribe el proyecto y HyperFrames lo convierte en un MP4.** Sale «a real project you can change down to the frame», y puedes ver la vista previa en el navegador («Preview instantly in the browser»). No es un generador de video con un modelo de IA: convierte HTML en video. No prometemos calidad del resultado.

El ejemplo del propio README: con `/hyperframes`, «create a 10-second product intro with a fade-in title, a background video, and subtle background music.» Es el ejemplo del repo, no una prueba nuestra.

### Límites honestos

- Hay que instalar **Node.js 22+ y FFmpeg**.
- **Dos de las nueve skills son Pro** (`/reverse-any-video` y `/style-sampling`, con la etiqueta «HyperFrames Pro»). No damos precio.
- No es «sin tocar nada» ni «en automático»: describes el video y puedes editar el proyecto cuadro por cuadro.
- No lo presentes como un editor, ni como algo «solo para Claude Code», ni como si «acabara de salir»: esas frases no están en la fuente.

### Créditos

- HyperFrames: [heygen-com/hyperframes](https://github.com/heygen-com/hyperframes), licencia Apache 2.0. No es un producto mío ni tengo relación con el proyecto.
- Documentación citada en el paquete: [hyperframes.heygen.com/introduction](https://hyperframes.heygen.com/introduction).

### Fuentes

Consultadas en el paquete del 18-nov-2026, America/Caracas:

- README: https://raw.githubusercontent.com/heygen-com/hyperframes/main/README.md
- Repo: https://github.com/heygen-com/hyperframes
- Introducción: https://hyperframes.heygen.com/introduction

---
¿Quieres que lo dejemos instalado en tu Claude Code y armemos juntos el primer proyecto? Escríbeme por DM **@briananderson.ai**.
