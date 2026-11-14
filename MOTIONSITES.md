# MOTIONSITES: una skill gratis para que Claude arme landings cinematográficas

Recurso del video sobre MotionSites Web Builder. Brian Anderson / CashFunnel, noviembre de 2026.

**MotionSites Web Builder** es una **skill (plugin) gratis y open source para Claude y Claude Code**. El README oficial la describe así: *“a free Claude skill”* que hace que Claude arme *“award-level, cinematic landing pages instead of average AI layouts.”* No es un constructor visual ni un sustituto de Figma o Framer: es una skill que le pide a Claude que estudie diseños de ejemplo, elija media real, escriba una especificación precisa, construya la página y **se haga capturas a sí mismo y la corrija** hasta pasar una barra de calidad.

Matiz honesto: lo que viene en la skill es una **muestra gratis**. El mismo README dice que MotionSites Unlimited (prompts premium, fondos, plantillas y un MCP) es una oferta de pago aparte. Esta guía cubre solo la skill gratis.

## Enlaces oficiales

- **Repo de la skill:** https://github.com/Motionsites-AI/claude-skill
- **Última release (el zip para Claude):** https://github.com/Motionsites-AI/claude-skill/releases/latest
- **Sitio de MotionSites (galería y ejemplos):** https://motionsites.ai
- **Claude:** https://claude.com
- **Documentación de Claude Code:** https://code.claude.com/docs

## Cómo instalarla

Hay dos vías oficiales, según dónde trabajes. Las dos salen del README del repo.

### En Claude.ai o en Claude desktop

1. Descarga **`motionsites-web-builder.zip`** desde la [última release](https://github.com/Motionsites-AI/claude-skill/releases/latest). Hoy la release publicada es la **v1.0.0** (14-nov-2026, America/Caracas).
2. En Claude, abre **Customize → Skills → + → Create skill → Upload a skill**, elige el zip y activa la skill.
3. El README pide que la **ejecución de código** esté encendida en **Settings → Capabilities**.

### En Claude Code (plugin)

En Claude Code, corre:

```text
/plugin marketplace add Motionsites-AI/claude-skill
/plugin install motionsites-web-builder@motionsites
```

Si no tienes una clave SSH de GitHub, el README indica esta alternativa:

```text
/plugin marketplace add https://github.com/Motionsites-AI/claude-skill.git
```

Y después el mismo `/plugin install motionsites-web-builder@motionsites`.

### En Claude Code (manual)

Copia `plugins/motionsites-web-builder/skills/motionsites-web-builder` a `~/.claude/skills/`.

### Opcional: que Claude vea su propio trabajo

El bucle de capturas y corrección funciona mejor con Playwright, según el README:

```bash
pip install playwright && python -m playwright install chromium
```

## Cómo pedírselo a Claude

El README dice que basta con pedirle un sitio: la skill se activa sola. Ejemplos oficiales (en inglés, como están en el repo):

```text
Build a landing page hero for a luxury sleep-tracking ring.
```

```text
Make a portfolio homepage for an architectural photographer in Lisbon. Editorial and quiet.
```

```text
Write a Lovable prompt for a waitlist page for my AI travel app.
```

```text
Here's my current site: make it look award-winning.
```

En español también puedes describir tu negocio y el tono que quieres, por ejemplo: «Arma una landing cinematográfica para mi estudio de arquitectura en Caracas, editorial y sobria. Muéstrame el plan antes de escribir código.» Revisa el resultado en móvil y escritorio antes de darlo por bueno.

## Qué trae la skill (datos del README)

El README, consultado el **14-nov-2026** (America/Caracas), lista:

- **40 prompts de ejemplo**, tomados de los más votados en MotionSites. Claude lee los 2 o 3 más cercanos a cada brief.
- Una **estantería de media**: más de 50 videos de héroe cinematográficos, 30 recortes 3D transparentes y 29 imágenes, alojados en público.
- **Más de 55 recetas de técnica** con código (bucles de video, vidrio líquido, titulares palabra a palabra, carruseles de profundidad, modelos 3D con Three.js, entre otras).
- Reglas de gusto con números (escala tipográfica, tracking, espacio, color, tiempo de movimiento y copy).
- Una **plantilla de especificación** que Claude escribe antes de programar, y un bucle de captura + script de QA (assets rotos, desbordes en móvil, fuentes, reproducción de video).
- Un **modo prompt**: en lugar de código, puedes pedirle un prompt afinado para Lovable, Bolt, v0, Cursor, Manus, Google AI Studio o Kimi.

La galería del sitio oficial (https://motionsites.ai) muestra ejemplos reales de esas verticales (tiendas, portfolios, editoriales). No hace falta un pack nuestro.

## Requisitos, licencia y límites

- La skill es gratis, pero **necesitas Claude o Claude Code**; tu plan va aparte.
- En Claude.ai / desktop, la ejecución de código tiene que estar activa.
- **Licencia partida** (archivo LICENSE del repo): las instrucciones, referencias y scripts de la skill (todo menos las carpetas `examples` y `media`) están en **MIT**. Los prompts de ejemplo y la media son **© MotionSites**. Puedes usarlos para armar sitios, también para clientes, con esta skill. No puedes revenderlos ni redistribuirlos como una colección de prompts o de media.
- La media de la estantería está alojada por MotionSites; una página que la use depende de que esos enlaces sigan en línea. El propio material sugiere sustituirla por tus archivos cuando puedas.
- Lo que viene en la skill es una **muestra**. MotionSites Unlimited es de pago; esta guía no cita un precio: mira https://motionsites.ai/unlimited el día que te interese. El README también avisa que, al terminar un encargo, Claude puede mencionar esa oferta en el chat (no en tu código). Puedes pedirle que no lo vuelva a mencionar.
- Empieza en un proyecto de prueba. No pegues claves en el chat ni en el repositorio. No prometemos más conversión ni que “ya no se vea hecha por una IA”.

## Fuentes

Consultadas el 14-nov-2026, America/Caracas (todas HTTP 200):

- README: https://github.com/Motionsites-AI/claude-skill (skill gratis, instalación en Claude y en Claude Code, contenido, “Want the full library?”)
- LICENSE: https://github.com/Motionsites-AI/claude-skill/blob/main/LICENSE (MIT para instrucciones y código; © MotionSites para ejemplos y media)
- Última release: https://github.com/Motionsites-AI/claude-skill/releases/latest (v1.0.0, zip `motionsites-web-builder.zip`)
- Sitio y galería: https://motionsites.ai
- Claude: https://claude.com · Claude Code: https://code.claude.com/docs

Guía educativa de Brian Anderson. No es un producto de MotionSites ni de Anthropic, ni una promesa de resultados de negocio.
