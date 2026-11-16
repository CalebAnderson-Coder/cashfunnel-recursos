# HUMANO: Humanizer, la skill que revisa 26 señales de texto hecho por IA

Recurso del video «Humanizer: la skill gratis que revisa 26 señales de texto hecho por IA». Brian Anderson / CashFunnel, 16 de noviembre de 2026.

**Humanizer** es una skill **gratis y open source** (licencia [MIT](https://github.com/blader/humanizer/blob/main/LICENSE)) que publica [blader](https://github.com/blader) en GitHub. Revisa tu texto en busca de **26 patrones** típicos de prosa generada por IA (palabras recurrentes, tríos forzados, rayas por todas partes, lenguaje de vendedor, y el resto de la lista) y te propone una reescritura. Está construida sobre [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing), la página de consejos que usan los editores de Wikipedia para detectar texto generado por IA. No es una política oficial de Wikipedia, ni un “detector oficial”, ni un producto de Anthropic.

Repo: [github.com/blader/humanizer](https://github.com/blader/humanizer)

**No es ANTISLOP.** ANTISLOP limpia código. Humanizer trabaja sobre prosa.

## Costo real

- **La skill es gratis** (MIT). Humanizer no te cobra.
- La corres en un agente que sí puede ser de pago: Claude Code, Codex, Claude Desktop u otros que soporten skills. Claude Code **no** está en el plan Free de Anthropic; Pro cuesta **20 USD al mes** si pagas mes a mes (17 USD al mes si pagas el año por adelantado, 200 USD). Revisa [claude.com/pricing](https://claude.com/pricing) el día que lo contrates.
- Si ya usas uno de esos agentes, instalar Humanizer no añade una suscripción.

## Cómo instalarla

Una vez instalada, la corres con `/humanizer`.

**Claude Code** (2.1.142 o más nuevo):

```
/plugin marketplace add blader/humanizer
/plugin install humanizer@humanizer
```

En versiones anteriores:

```bash
npx skills add blader/humanizer --global --agent claude-code
```

**Codex:**

```bash
npx skills add blader/humanizer --global --agent codex
```

**Claude.ai y Claude Desktop:** descarga el repo como ZIP (Code → Download ZIP) y súbelo como skill en Ajustes.

**Otros agentes** (Gemini CLI, GitHub Copilot, Windsurf, etc.):

```bash
npx skills add blader/humanizer --global --agent '*'
```

Quita `--global` si solo la quieres en el proyecto actual. Si tu agente no aparece en esa CLI, copia `SKILL.md` a su carpeta de skills.

## Primera prueba

En Claude Code (u otro agente ya instalado):

```
/humanizer

[pega aquí un párrafo que hayas escrito con IA]
```

También puedes pedirlo en lenguaje natural (`Please humanize this text: …`) o apuntarle a un archivo (`Humanize the prose in docs/lanzamiento.md`). En un archivo, cambia solo la prosa: deja en paz código, datos, frontmatter y destinos de enlaces.

Si quieres que suene más a ti, incluye una muestra:

```
/humanizer

Aquí va una muestra de cómo escribo yo (2 o 3 párrafos):
[pega texto tuyo]

Ahora humaniza este texto:
[pega el texto de IA]
```

El repo dice que sigue el ritmo, el vocabulario, la puntuación y las rarezas deliberadas de la muestra, incluidas las rayas si tú las usas.

Lo que vas a ver, si pegas texto: una **primera versión**, una **crítica** de lo que todavía suena artificial, y la **versión final**. El README lo describe así: marca las señales (las más fuertes primero), arma un borrador, lo contrasta otra vez con los 26 patrones y con las afirmaciones del original, y entrega el final. Conserva cada afirmación que ya estaba en el texto.

## Límites honestos

- **Revisa 26 señales; no “quita toda señal de IA”.** El número de patrones cambia entre versiones de terceros (algunos citan 24 o 29). El README oficial, el 16-nov-2026, dice 26.
- **No está hecha para engañar detectores de IA.** Lo dice el propio repo: edita para lectores humanos; los detectores **siguen marcando la mayoría** de sus textos. No la uses para hacer pasar un texto como “indetectable”.
- La página de Wikipedia es una **página de consejos** de WikiProject AI Cleanup, no una política. Ella misma advierte que no todo texto con esas señales fue escrito por IA.
- El resultado no queda perfecto solo porque pasó por la skill. Léelo antes de publicarlo.
- “La primera skill que instalaría” es una recomendación de este video, no una afirmación del repo.

## Fuentes

Consultadas el 16-nov-2026, America/Caracas:

- README, instalación, 26 patrones, voz con muestra, detectores y licencia MIT: https://github.com/blader/humanizer
- Guía de Wikipedia (página de consejos, no política): https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing
- Precios de Claude: https://claude.com/pricing

---
¿Quieres que la dejemos instalada en tu agente, con una muestra de tu voz? Escríbeme por DM **@briananderson.ai**.
