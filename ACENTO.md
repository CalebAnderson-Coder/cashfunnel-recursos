# ACENTO: la skill para elegir el color de acento de tu página

Recurso del video «Verde botella y hueso. Parece un ensayo». Brian Anderson / CashFunnel, noviembre de 2026.

En el video armo tres páginas con dos colores cada una, y las tres se ven apagadas, "de ensayo". Les agrego **un solo color de acento** y cambian por completo. El truco es una regla de temperatura:

> **Página cálida → acento frío. Página fría → acento cálido.**

Aquí tienes la regla explicada, los tres ejemplos con sus códigos, la **skill para Claude Code** que lo hace por ti y un prompt para copiar en cualquier IA.

## La regla en 30 segundos

1. **Mira el color que más ocupa** en tu página (el fondo o la foto grande). Esa es la base.
2. **¿Es cálido o frío?** Cálidos: rojos, naranjas, amarillos, marrones, crema, arena, hueso. Fríos: verdes, azules, índigos, violetas, grises azulados.
3. **El acento va al revés.** Si la base es cálida, el acento es frío (azul cobalto, turquesa, esmeralda). Si la base es fría, el acento es cálido (bermellón, coral, naranja, oro).
4. **Poquito.** El acento ocupa del 5 al 10 % de la página: una palabra del titular, el botón principal o un detalle de la foto. Nunca el fondo.
5. **Que se lea.** El acento necesita un contraste de al menos 3:1 con la base. El texto encima del acento (un botón) necesita 4,5:1.

Por qué funciona: el contraste entre cálido y frío es uno de los siete contrastes de color que describió Johannes Itten en *El arte del color* (1961). Un único color de temperatura contraria es lo primero que mira el ojo, así que guía la atención a donde tú quieres (el botón, la oferta).

## Los tres ejemplos del video

| Página | Base | Secundario | Acento | Regla |
|---|---|---|---|---|
| Teatro: «noche de estreno» | Verde botella `#0F372B` | Hueso `#EFE7DA` | **Bermellón `#E8392B`** | Página fría → acento cálido |
| Balneario: «tumbonas frente al mar» | Arena `#DFBFA0` | Terracota `#7A3E26` | **Azul cobalto `#0C45B0`** | Página cálida → acento frío |
| Kintsugi: «reparado en oro» | Índigo `#0B1325` | Celadón `#A9CDBE` | **Oro `#F2B53A`** | Página fría → acento cálido |

Contrastes medidos con la fórmula de WCAG 2.x:

- Bermellón sobre verde botella: 3,15:1. En un botón bermellón, el texto negro da 5,05:1. El blanco da 4,16:1, solo para texto grande.
- Cobalto sobre arena: 4,85:1. Texto blanco sobre cobalto: 8,42:1.
- Oro sobre índigo: 10,09:1. Texto negro sobre oro: 11,45:1.

Las tres páginas del video son diseños de ejemplo hechos para el video (marcas inventadas). Las fotos se generaron con IA.

## La skill para Claude Code

Archivo: [`acento/.claude/skills/acento/SKILL.md`](acento/.claude/skills/acento/SKILL.md)

Hace los cinco pasos por ti: lee tu página (captura, HTML o CSS), clasifica la temperatura de la base, elige el acento contrario, calcula los contrastes y te devuelve la paleta con variables CSS y los tres lugares donde poner el acento.

### Instalación (2 minutos)

1. Necesitas **Claude Code** instalado y con sesión iniciada. Guía oficial: https://code.claude.com/docs/en/overview. Claude Code requiere un plan de pago de Claude o la API; revisa los precios en https://claude.com/pricing el día que lo contrates. La skill es gratis.
2. Copia la carpeta del skill [`acento/.claude/skills/acento/`](acento/.claude/skills/acento/) (la que contiene `SKILL.md`) a una de estas dos rutas, de modo que el archivo quede exactamente ahí:
   - **Para todos tus proyectos:** `~/.claude/skills/acento/SKILL.md`. En Windows: `C:\Users\TU_USUARIO\.claude\skills\acento\SKILL.md`.
   - **Solo para un proyecto:** `.claude/skills/acento/SKILL.md` dentro de la carpeta del proyecto.
3. Abre Claude Code en esa carpeta (`claude`), o reinícialo si ya estaba abierto. El nombre de la carpeta es el comando: escribe `/acento` para llamarla directo.

No copies la carpeta `acento` de la raíz de este repo: dentro vive `.claude/`, y si la pegas tal cual el `SKILL.md` no queda donde Claude Code lo busca.

### Uso

Claude la usa sola cuando hablas de colores o de diseñar una página. También puedes pedírsela directo:

```text
/acento revisa mi landing (index.html). Dime la base, su temperatura y qué color de acento le pongo, con variables CSS y dónde va.
```

```text
Usa la skill acento: voy a hacer la web de una cafetería con fondo crema y marrón café. Dame la paleta completa con el acento.
```

## Prompt para copiar (sin instalar nada)

Sirve en Claude, ChatGPT, Gemini o cualquier IA. Pega esto y agrega tu página (captura, colores o descripción):

```text
Actúa como director de arte. Voy a darte mi página (captura, colores o descripción).
1. Dime cuál es el color base (el que más ocupa) y el secundario, con su hex.
2. Clasifica la base como CÁLIDA (rojos, naranjas, amarillos, marrones, crema, arena) o FRÍA (verdes, azules, índigos, violetas, grises azulados).
3. Aplica la regla: página cálida → acento frío; página fría → acento cálido. Propón UN color de acento, más saturado que la base, con contraste de al menos 3:1 contra la base. Dame su hex.
4. Dime qué color de texto va encima del acento (blanco o casi negro) con contraste de al menos 4,5:1.
5. El acento ocupa máximo el 10 % de la página: dime los 3 lugares exactos donde va (por ejemplo, una palabra del titular, el botón principal, un detalle de la foto).
6. Entrégame una tabla (nombre, hex, rol, temperatura, % de superficie) y las variables CSS --base, --secundario, --acento y --texto-acento.
No uses dos acentos de temperaturas distintas y no cambies mi color base.
Mi página: [PEGA AQUÍ TU CAPTURA, TUS COLORES O LA DESCRIPCIÓN]
```

## Errores comunes

- **Acento de la misma temperatura que la base** (naranja sobre arena): no se nota.
- **Demasiado acento:** si está en todas partes, deja de ser acento. Máximo 2 o 3 lugares por pantalla.
- **Acento en el texto largo:** cansa y baja la legibilidad. Úsalo en palabras sueltas y botones.
- **Cambiar la base para que combine:** el acento se adapta a tu página, no al revés.

## Fuentes

Consultadas el 19-nov-2026, America/Caracas:

- Johannes Itten, *The Art of Color* (1961; original *Kunst der Farbe*): el contraste cálido-frío es uno de sus siete contrastes de color.
- W3C, WCAG 2.2: contraste mínimo de texto 4,5:1 (1.4.3) y de elementos gráficos 3:1 (1.4.11). https://www.w3.org/TR/WCAG22/
- Claude Code, skills: https://code.claude.com/docs/en/skills

Guía educativa de Brian Anderson. No es un producto de Anthropic ni de ninguna otra marca, ni una promesa de resultados.

---
¿Quieres que te lo armemos para tu negocio? Escríbeme por DM **@briananderson.ai**.
