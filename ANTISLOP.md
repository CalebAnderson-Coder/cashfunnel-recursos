# ANTISLOP: 3 skills de Claude Code para que tu interfaz no se vea hecha por IA

Si le pides una página a un agente sin más contexto, casi siempre sale lo mismo: la misma fuente, degradados morados, tarjetas dentro de tarjetas y botones de píldora. Estas tres skills open source le dan a Claude Code (y a otros agentes compatibles) criterio de diseño, movimiento con intención y un pase final de pulido.

Trabaja primero en un proyecto de prueba, sin secretos ni datos de clientes. Los comandos salen de la documentación oficial de cada repositorio (revisada el 9-nov-2026). No son una prueba ejecutada en tu equipo.

## Antes de empezar
- Node.js con `npx`. Taste Skill pide Node 22 o superior y Chrome, Edge o Chromium instalado.
- Claude Code u otro agente compatible con skills.
- Un proyecto donde puedas revisar los cambios antes de aceptarlos.

## 1. Taste Skill: opinión estética
Le da al agente dirección de arte y reglas concretas para no armar la típica landing genérica: un solo sistema de diseño, fotos y UI reales, y una revisión en navegador real antes de entregar.

```bash
npx skills add https://github.com/Leonxlnx/taste-skill --skill "design-taste-frontend"
```

Como plugin de Claude Code, dentro de Claude Code:

```
/plugin marketplace add Leonxlnx/taste-skill
/plugin install taste-skill@taste-skill
```

Úsala al construir o rediseñar: «Rediseña la página de inicio de mi negocio usando Taste Skill».
No instala dependencias ni usa API keys propias.
- Repositorio: https://github.com/Leonxlnx/taste-skill
- Web: https://tasteskill.dev

## 2. Skills de Emil Kowalski: movimiento con intención
Emil Kowalski (ex Vercel y Linear, autor de Sonner y Vaul) publica un paquete de skills de diseño y animación: curvas de easing correctas, duraciones, coreografía y revisión de animaciones.

```bash
npx skills@latest add emilkowalski/skills
```

Incluye, entre otras, `emil-design-eng` (la principal), `animate`, `review-animations`, `improve-animations`, `find-animation-opportunities` y `choreograph`.
Ejemplos de prompt: «Agrega una entrada correcta a este modal», «Revisa las animaciones de este componente», «Esto se siente mecánico, arréglalo».
- Repositorio: https://github.com/emilkowalski/skills
- Página del autor: https://emilkowal.ski/skill

## 3. Impeccable: vocabulario de diseño y pase de pulido
Más de veinte comandos para guiar al agente (`typeset`, `colorize`, `layout`, `animate`, `critique`, `audit`, `polish`…) y un detector de patrones típicos de IA.

```bash
npx impeccable install
```

Recarga tu herramienta y en el proyecto corre una vez:

```
/impeccable init
```

Eso crea `PRODUCT.md` con el contexto de tu producto. Antes de entregar, corre el pulido sobre una parte concreta:

```
/impeccable polish la página de precios
```

Funciona mejor con objetivos acotados (una sección o un componente) que con toda la web de golpe.
- Repositorio: https://github.com/pbakaus/impeccable
- Documentación: https://impeccable.style/docs

## Orden recomendado
1. **Taste Skill** al construir o rediseñar, para evitar el look genérico desde el inicio.
2. **Skills de Emil** cuando la estructura ya está pero la interfaz se siente plana.
3. **Impeccable `polish`** como último pase antes de entregar.

## Prueba de 10 minutos
1. Abre un proyecto de prueba (una landing o un panel sencillo).
2. Instala las tres skills.
3. Pide: «Rediseña el hero con Taste Skill, agrega una entrada con buen easing y luego corre /impeccable polish sobre el hero».
4. Revisa el resultado en móvil y escritorio, y lee cada cambio antes de aceptarlo.

## Qué cuesta
- Las tres skills son gratis y open source: Taste Skill y las skills de Emil con licencia MIT, Impeccable con Apache-2.0.
- Claude Code u otro agente se paga según tu plan.

## Antes de instalar cualquier skill
Lee el `SKILL.md` y los scripts que trae. Revisa qué comandos ejecuta y a qué servicios se conecta. Las estrellas de GitHub no equivalen a una auditoría de seguridad.

## Relacionado
- `DISEÑO`: incluye Taste Skill dentro de un pack de cinco plugins de diseño.
- `WEB`: Motion como librería de código y kits de UI. Aquí, el movimiento llega como skill del agente.

Guía educativa de Brian Anderson. No es un producto oficial de Taste Skill, Emil Kowalski ni Impeccable.
¿Quieres que lo apliquemos a la web de tu negocio? Escríbeme por DM en TikTok o Instagram: @briananderson.ai
