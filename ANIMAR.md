# ANIMAR: tres librerías gratis para las webs que te arma Claude

Recurso del video sobre Motion, Anime.js y Shadcn Charts. Brian Anderson / CashFunnel, noviembre de 2026.

Tres librerías open source para movimiento y datos en una web. **No son plugins de Claude Code.** Son librerías web: Claude (o Claude Code) puede instalarlas y usarlas cuando le pides una página o un panel.

El gancho del video dice que hacen en código lo que **Framer** cobra desde 10 dólares al mes. Matiz honesto: no son un sustituto 1:1 de un sitio alojado en Framer; son código que tú (o tu agente) integras en tu propio proyecto.

## Los tres enlaces oficiales

1. **Motion** — https://motion.dev — transiciones y animación para la web. Antes se llamaba Framer Motion. Open source (MIT).
2. **Anime.js** — https://animejs.com — movimiento a medida: resortes, líneas de tiempo, formas. Open source (MIT). Documentación: https://animejs.com/documentation
3. **Shadcn Charts** — https://ui.shadcn.com/docs/components/chart — componentes de gráficos que heredan el diseño de tu proyecto. La URL documentada redirige hoy a https://ui.shadcn.com/docs/components/base/chart (ambas responden). El código del kit shadcn/ui es MIT.

Demos reales: los propios sitios. No hace falta un “pack” nuestro.

## Precio de la alternativa de pago (Framer)

En la página oficial https://www.framer.com/pricing, consultada el **14-nov-2026** (America/Caracas), con la facturación anual seleccionada (“Yearly billing”):

- Plan **Basic**: **10 USD al mes**
- Plan **Pro**: **30 USD al mes**

El propio sitio dice: *“All prices are monthly and billed according to the billing cycle selected at checkout.”* El gancho usa “desde 10 dólares al mes”, que es el plan de pago de entrada en esa vista anual. Al cambiar el ciclo de facturación, el cargo en caja puede ser otro; revisa la página el día que lo contrates. Hay plan Free, con límites (por ejemplo, para conectar un dominio propio Framer indica que hay que pasar a un plan de pago).

## 1. Motion

Sitio: https://motion.dev · Repo: https://github.com/motiondivision/motion · Docs: https://motion.dev/docs

El sitio oficial la presenta como *“Free and open source. Previously Framer Motion.”* El README confirma: **Framer Motion ahora es Motion**. En React se importa desde `motion/react`, ya no desde `framer-motion`. Sirve para React, JavaScript y Vue. Licencia **MIT** (el README y el paquete npm `motion`).

Instalación oficial:

```bash
# React / JavaScript
npm install motion

# Vue
npm install motion-v
```

Ejemplo oficial (React):

```jsx
import { motion } from "motion/react"

function Component() {
  return <motion.div animate={{ x: 100 }} />
}
```

Hay ejemplos oficiales en https://motion.dev/examples. Si usas un agente, el README documenta `npx motion-ai` (skill MIT) y un MCP en https://mcp.motion.dev.

**Motion+ no es lo mismo** que la librería. Motion+ es una oferta de pago aparte (licencia personal o plan Business) con ejemplos extra, APIs premium y otras funciones. Para lo que muestra el video basta la librería gratis.

## 2. Anime.js

Sitio: https://animejs.com · Repo: https://github.com/juliangarnier/anime · Docs: https://animejs.com/documentation

El sitio oficial la describe como un motor de animación JavaScript, y dice que *“Anime.js is 100% free.”* Licencia **MIT**. El README y las demos oficiales cubren resortes (`createSpring`), líneas de tiempo (`createTimeline`) y formas SVG (morph, line drawing, motion path), entre otras APIs.

Instalación oficial (el sitio indica `npm i animejs`):

```bash
npm i animejs
```

Uso oficial de la v4 (módulos ES):

```javascript
import { animate, stagger } from "animejs"

animate(".square", {
  x: 320,
  rotate: { from: -180 },
  duration: 1250,
  delay: stagger(65, { from: "center" }),
  ease: "inOutQuint",
  loop: true,
  alternate: true,
})
```

Si vienes de la v3, el proyecto publica una guía de migración en el wiki del repo. Esta guía no asume que un snippet de v3 funcione igual en v4.

## 3. Shadcn Charts

Docs: https://ui.shadcn.com/docs/components/chart (redirige a `/docs/components/base/chart`) · Repo del kit: https://github.com/shadcn-ui/ui

La documentación oficial dice: *“Beautiful charts. Built using Recharts. Copy and paste into your apps.”* Son componentes que copias a tu proyecto, pensados para verse bien de entrada y **quedar con tu diseño** (temas y personalización). Por debajo usan Recharts; no te encierran en una capa que oculte esa librería. Hoy las docs advierten que el componente usa **Recharts v3**.

No es `npm install shadcn-charts`. Primero necesitas un proyecto web (por lo general React + Tailwind, con shadcn/ui ya inicializado). Luego, el comando documentado:

```bash
npx shadcn@latest add chart
```

La misma página documenta equivalentes con pnpm, yarn y bun (`pnpm dlx shadcn@latest add chart`, `yarn dlx shadcn@latest add chart`, `bun shadcn@latest add chart`). El CLI te pedirá dependencias (entre ellas Recharts). No es “un clic y listo” si todavía no tienes el proyecto armado.

## Cómo pedírselo a Claude

Un prompt honesto, del estilo:

```text
Usa Motion para las transiciones de esta landing, Anime.js para el micro-movimiento del hero, y Shadcn Charts para el gráfico de [dato].
No inventes otra librería. Instala solo las dependencias oficiales (npm install motion, npm i animejs, npx shadcn@latest add chart).
Muéstrame los comandos antes de ejecutarlos y no toques archivos fuera de este proyecto.
```

Sustituye `[dato]` por la métrica real. Revisa el diff y el resultado en el navegador (móvil y escritorio) antes de darlo por bueno. El recurso **WEB** también menciona Motion, junto con otras piezas; esta guía es la de las tres librerías del video ANIMAR.

## Requisitos y límites

- Hace falta un entorno de proyecto web habitual (Node y un framework: React, Vue u otro, según la librería).
- Las tres librerías son gratis y MIT. Tu plan de Claude/Claude Code, el hosting y cualquier herramienta de pago (Framer, Motion+, etc.) van aparte.
- No prometemos más conversión ni que “ya no se vea hecha por una IA”.
- Empieza en un repo de prueba. No pegues claves en el chat ni en el repositorio.

## Fuentes

Consultadas el 14-nov-2026, America/Caracas (todas HTTP 200):

- Motion: https://motion.dev, https://github.com/motiondivision/motion (README: MIT; “Framer Motion is now Motion”)
- Anime.js: https://animejs.com, https://github.com/juliangarnier/anime, paquete npm `animejs` (MIT)
- Shadcn Charts: https://ui.shadcn.com/docs/components/chart → https://ui.shadcn.com/docs/components/base/chart; licencia MIT de https://github.com/shadcn-ui/ui
- Framer: https://www.framer.com/pricing (Basic 10 USD/mes y Pro 30 USD/mes con facturación anual seleccionada; texto oficial sobre el ciclo de facturación citado arriba)

Guía educativa de Brian Anderson. No es un producto de Motion, Anime.js, shadcn/ui ni Framer, ni una promesa de resultados de negocio.
