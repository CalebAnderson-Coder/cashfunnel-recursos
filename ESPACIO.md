# ESPACIO: un comando y Claude te anima el espacio en 3D

Recurso del video «Un comando en Claude anima el espacio». Brian Anderson / CashFunnel, noviembre de 2026.

En el video escribo un solo comando y Claude Code arma una escena 3D animada: un astronauta saltando en la Luna, el sistema solar y un agujero negro. Aquí tienes los **tres comandos**, las **tres páginas que generó Claude Code** y los pasos para hacerlo tú.

**Cómo está hecho el video, sin trucos escondidos:**
- Las tres escenas son páginas HTML con [three.js](https://threejs.org) que **escribió Claude Code** con los comandos de abajo, en la PC de Brian, el 14-nov-2026. Las grabamos cuadro a cuadro en un navegador sin ventana.
- La pantalla de chat del teléfono del video es una **recreación del flujo** para que se vea en vertical; no es una captura de la app de Claude. En la vida real escribes el comando en Claude Code (terminal, app de escritorio o extensión del editor).
- En el agujero negro hicimos **un arreglo de una línea** a lo que generó Claude (la esfera negra no se dibujaba). Después subimos las etiquetas a 34/30 px para que se lean bien en el celular. Ambos cambios ya van escritos dentro del comando `/a-fondo`, así que a ti te debería salir bien a la primera.
- El dato de la Luna es real: la gravedad en la Luna es aproximadamente **1/6** de la de la Tierra (NASA: [datos de la Luna](https://science.nasa.gov/moon/facts/), «one-sixth»; [ficha NSSDC](https://nssdc.gsfc.nasa.gov/planetary/factsheet/moonfact.html): 1,62 m/s² frente a 9,8 m/s², relación 0,165). Y el sistema solar tiene **8 planetas** ([NASA, planetas](https://science.nasa.gov/solar-system/planets/)).

## Qué necesitas

1. **Claude Code** instalado y con sesión iniciada. Guía oficial: https://docs.anthropic.com/en/docs/claude-code/overview — necesitas una cuenta de Claude con acceso a Claude Code (plan de pago o API). Revisa los planes en https://claude.com/pricing el día que lo contrates.
2. **Un navegador moderno** (Chrome, Edge o Firefox) para abrir el HTML. Las páginas cargan three.js y las fuentes desde internet (jsDelivr y Google Fonts), así que abre el archivo con conexión.

## Paso a paso (5 minutos)

1. Crea una carpeta vacía, por ejemplo `espacio`.
2. Dentro, crea la carpeta `.claude/commands/` y copia ahí los tres archivos de [`espacio/.claude/commands/`](espacio/.claude/commands/):
   - [`peli-3d.md`](espacio/.claude/commands/peli-3d.md) → comando `/peli-3d` (corto 3D cinematográfico)
   - [`explica-3d.md`](espacio/.claude/commands/explica-3d.md) → comando `/explica-3d` (explicador 3D)
   - [`a-fondo.md`](espacio/.claude/commands/a-fondo.md) → comando `/a-fondo` (inmersión cinematográfica)
   Cada archivo es un comando personalizado de Claude Code (*custom slash command*): el texto que hay dentro es la receta completa de la escena (tamaño vertical 1080×1920, luces, cámara, tiempos, tipografía y textos en español).
3. Abre Claude Code en esa carpeta (`cd espacio` y luego `claude`).
4. Escribe **un** comando:

```text
/peli-3d ¿y si saltaras en la Luna?
```

```text
/explica-3d nuestro sistema solar
```

```text
/a-fondo cómo funciona un agujero negro
```

5. Claude Code escribe el archivo (`luna.html`, `sistema_solar.html` o `agujero_negro.html`). Ábrelo con doble clic: la animación se reproduce sola en bucle.

¿Lo quieres sin terminal interactiva? También funciona así (modo no interactivo):

```bash
claude -p "/peli-3d ¿y si saltaras en la Luna?" --permission-mode acceptEdits
```

## Las tres páginas que generó Claude Code (las del video)

Descárgalas y ábrelas en el navegador:

- [`espacio/escenas/luna.html`](espacio/escenas/luna.html) — astronauta que salta con la gravedad de la Luna, la Tierra al fondo.
- [`espacio/escenas/sistema_solar.html`](espacio/escenas/sistema_solar.html) — el Sol y los 8 planetas con su nombre, en órbita.
- [`espacio/escenas/agujero_negro.html`](espacio/escenas/agujero_negro.html) — disco de acreción, anillo de luz y 3 etiquetas: horizonte de sucesos, singularidad y disco de acreción.

Cada página dura menos de 3 segundos y se repite en bucle. Si le añades `?capture` a la URL, la animación se detiene y puedes mover el tiempo a mano desde la consola con `setTime(1.5)`. Así la grabamos para el video.

## Cámbialo por tu tema

Los comandos sirven para cualquier idea, no solo el espacio. Abre el `.md` del comando y cambia la sección «Escena» por lo que quieras mostrar (un volcán, el corazón humano, cómo vuela un avión). Las «Reglas técnicas comunes» del final mantienen el formato vertical, el tipeo del titular y la etiqueta de abajo.

Consejos que aprendimos haciéndolo:
- Da **medidas en píxeles** (dónde va cada objeto y qué tamaño tiene). Con «grande» o «centrado» Claude adivina; con «560 px de alto, botas en y≈1290» acierta.
- Si algo sale mal, **no lo arregles a mano: corrige el comando** y vuelve a ejecutarlo. Así la próxima vez sale bien con un solo comando.
- En three.js, un objeto que tiene que quedar encima de efectos aditivos necesita `transparent: true` además de `renderOrder`; si no, desaparece (eso fue lo que arreglamos en el agujero negro).

## Créditos y licencias

- three.js — MIT (https://github.com/mrdoob/three.js).
- Fuentes: Inter, JetBrains Mono y Cormorant Garamond — SIL Open Font License (Google Fonts).
- Música del video: «Blip Stream» — Kevin MacLeod (incompetech.com). Licensed under Creative Commons: By Attribution 4.0 License. http://creativecommons.org/licenses/by/4.0/
- Los tres comandos y las páginas de esta carpeta: libres para que los uses y modifiques.
