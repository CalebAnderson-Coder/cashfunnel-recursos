---
name: acento
description: Elige la paleta de una página web o landing y su color de acento con la regla de temperatura (página cálida → acento frío; página fría → acento cálido). Úsala cuando el usuario pida colores, paleta, color de acento, "que se vea premium", o cuando vayas a diseñar o retocar una landing, una web, un post o una presentación y la página se vea apagada o "de ensayo".
---

# ACENTO: paleta + color de acento por temperatura

Regla única: **página cálida → acento frío. Página fría → acento cálido.**
El acento es el único color de temperatura contraria en toda la página. Por eso salta a la vista y la página deja de verse "de ensayo".

## Paso 1. Lee la página
- Si hay una página, una captura, un HTML o un CSS, saca los colores que ocupan más superficie (fondo, secciones, foto principal). Si no hay nada, pregunta en una línea qué vende la página y qué sensación debe dar, o propón tú 2 opciones.
- Anota la **base** (el color que más ocupa, 60–70 %) y el **secundario** (texto o bloques grandes, 20–30 %).

## Paso 2. Clasifica la temperatura de la base
Usa el tono (hue HSL, 0–360°):
- **Cálida:** rojos, naranjas, amarillos, marrones y neutros con tinte amarillo/rosado (hueso, arena, crema, terracota). Aprox. 0–70° y 330–360°.
- **Fría:** verdes, azules, índigos, violetas fríos y grises azulados (verde botella, celadón, índigo, azul marino). Aprox. 90–300°.
- **Zona dudosa** (70–90°, verde oliva o lima; 300–330°, magentas): decide por el color que más ocupa junto a ella y dilo.
- Neutro puro (blanco, negro o gris sin tinte, saturación < 8 %): la temperatura la pone el secundario o la foto principal.

## Paso 3. Elige el acento de temperatura contraria
- Base cálida → acento frío: azul cobalto, azul eléctrico, verde esmeralda, turquesa.
- Base fría → acento cálido: bermellón, coral, naranja, oro, amarillo mostaza.
- Que sea **más saturado** que la base y el secundario (saturación HSL ≥ 0,6).
- Que tenga **contraste ≥ 3:1 contra la base** (WCAG para elementos gráficos y texto grande). Si no llega, sube o baja su luminosidad, sin cambiar el tono.
- Texto encima del acento (botones): usa blanco o casi negro, el que dé **≥ 4,5:1**.

## Paso 4. Dosis
- Acento en **5–10 %** de la superficie como máximo: una palabra del titular, el botón principal, un detalle de la foto o un ícono.
- Nunca en el fondo, ni en párrafos largos, ni en más de 2–3 sitios por pantalla.
- Si la foto principal puede cambiar, pide que el acento aparezca en ella (un objeto, una prenda, una línea).

## Paso 5. Entrega
Devuelve siempre:
1. Una tabla: nombre · hex · rol (base / secundario / acento) · temperatura · % de superficie.
2. Los contrastes calculados (base/secundario, acento/base, texto/acento).
3. Variables CSS listas:

   ```css
   :root{
     --base:#......;      /* 60–70 % */
     --secundario:#......;/* 20–30 % */
     --acento:#......;    /* 5–10 %: botón, una palabra, un detalle */
     --texto-acento:#......;
   }
   ```

4. Dónde va el acento en ESTA página (3 lugares concretos como máximo).
5. Si ya existe la página, el cambio mínimo de CSS para aplicarlo.

## Ejemplos de referencia (del reel)
| Página | Base | Secundario | Acento | Lectura |
|---|---|---|---|---|
| Teatro, "noche de estreno" | Verde botella `#0F372B` (fría) | Hueso `#EFE7DA` | **Bermellón `#E8392B`** (cálido) | Página fría → acento cálido |
| Balneario, "tumbonas frente al mar" | Arena `#DFBFA0` (cálida) | Terracota `#7A3E26` | **Azul cobalto `#0C45B0`** (frío) | Página cálida → acento frío |
| Kintsugi, "reparado en oro" | Índigo `#0B1325` (fría) | Celadón `#A9CDBE` | **Oro `#F2B53A`** (cálido) | Página fría → acento cálido |

Contrastes medidos (WCAG 2.x): bermellón sobre verde botella 3,15:1; cobalto sobre arena 4,85:1; oro sobre índigo 10,09:1. Texto sobre el acento: negro sobre bermellón 5,05:1 (blanco solo da 4,16:1, sirve para texto grande); blanco sobre cobalto 8,42:1; negro sobre oro 11,45:1.

## No hagas
- No pongas dos acentos de temperaturas distintas en la misma página.
- No uses como acento un color de la misma temperatura que la base: no se nota.
- No cambies la base para que "combine" con el acento: el acento se adapta a la página, no al revés.
