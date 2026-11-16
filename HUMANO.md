# HUMANO: Humanizer, la skill que revisa 26 señales de texto hecho por IA

Recurso del video «Humanizer: la skill gratis que revisa 26 señales de texto hecho por IA». Brian Anderson / CashFunnel, 16 de noviembre de 2026.

**Humanizer** es una skill **gratis y open source** (licencia [MIT](https://github.com/blader/humanizer/blob/main/LICENSE)) que publica [blader](https://github.com/blader) en GitHub. Revisa tu texto en busca de **26 patrones** típicos de prosa generada por IA y te propone una reescritura, sin cambiar lo que el texto afirma. Está construida sobre [Wikipedia: Signs of AI writing](https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing), la guía que, según el propio README, usan los editores de Wikipedia para detectar texto generado por IA. No es una política oficial de Wikipedia, ni un «detector oficial», ni un producto de Anthropic.

- Código: [github.com/blader/humanizer](https://github.com/blader/humanizer) (69.867 estrellas al 16-nov-2026, según la API de GitHub)
- No es **ANTISLOP**: ANTISLOP limpia código. Humanizer trabaja sobre prosa.

Los datos de esta guía salen del README del repo, de su licencia MIT y de la página de Wikipedia citada, consultados el 16-nov-2026. Si una versión nueva cambia el número de patrones o los comandos de instalación, manda el GitHub.

## Costo real

- **La skill es gratis** (MIT). Humanizer no te cobra.
- **Tú pagas la herramienta de IA donde la corres.** El README la instala en Claude Code, Codex, Claude.ai / Claude Desktop, pi y otros agentes que soporten skills (Gemini CLI, GitHub Copilot, Windsurf, entre ellos). En [claude.com/pricing](https://claude.com/pricing) (consultado el 16-nov-2026), **Claude Code no está en el plan Free**. El plan Pro cuesta **20 USD al mes** si pagas mes a mes, o **17 USD al mes** si pagas el año por adelantado (200 USD). Los precios no incluyen impuestos y pueden cambiar: revísalos el día que contrates. No afirmamos el precio de Codex ni de los demás agentes.
- Si ya usas uno de esos agentes, instalar Humanizer no añade una suscripción.

## Cómo instalarla

Una vez instalada, la corres con `/humanizer`.

**Claude Code** (2.1.142 o más nuevo, según el README):

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

**Claude.ai y Claude Desktop:** descarga el repo como ZIP (**Code → Download ZIP**) y súbelo como skill en Ajustes.

**Otros agentes** (Gemini CLI, GitHub Copilot, Windsurf, etc.):

```bash
npx skills add blader/humanizer --global --agent '*'
```

Quita `--global` si solo la quieres en el proyecto actual. Si tu agente no aparece en esa CLI, el README indica copiar `SKILL.md` a su carpeta de skills.

## Cómo se usa

En Claude Code (u otro agente ya instalado):

```
/humanizer

[pega aquí un párrafo que hayas escrito con IA]
```

También puedes pedirlo en lenguaje natural (`Please humanize this text: …`) o apuntarle a un archivo (`Humanize the prose in docs/lanzamiento.md`). En un archivo, el README dice que cambia solo la prosa: deja en paz código, datos, frontmatter y destinos de enlaces.

Si quieres que suene más a ti, incluye una muestra:

```
/humanizer

Aquí va una muestra de cómo escribo yo (2 o 3 párrafos):
[pega texto tuyo]

Ahora humaniza este texto:
[pega el texto de IA]
```

El repo dice que sigue el ritmo, el vocabulario, la puntuación y las rarezas deliberadas de la muestra, incluidas las rayas si tú las usas.

Lo que vas a ver, si pegas texto: una **primera versión**, una **crítica** de lo que todavía suena artificial, y la **versión final**. El README lo describe así: marca las señales (las más fuertes primero), arma un borrador, lo contrasta otra vez con los 26 patrones y con las afirmaciones del original, y entrega el final. Conserva cada afirmación que ya estaba en el texto. Donde el texto es genérico, puede añadir un detalle que «sepa que es verdad»: revísalo, no vaya a colarse un dato que no es el de tu negocio.

Entre los 26 patrones están, por ejemplo, las **palabras típicas de IA** (#12), los **tríos forzados** (#6), las **rayas como conector universal** (#8) y el **lenguaje de vendedor** (#16). El README numera 26 en total, del más fuerte al más débil; los cinco primeros los reescribe en cuanto los ve, y los marcados como *weak alone* (como las rayas) solo los toca cuando hay varias señales juntas.

## Ejemplo concreto (dueño de un negocio)

Imagina que tienes una panadería y ChatGPT te armó la descripción de un pan de masa madre para Instagram. El texto habla de «un testimonio de tradición», de «innovación, inspiración y sabor» y cierra con «déjalo calar». Eso es justo el tipo de señal que busca Humanizer.

1. Instala la skill en Claude Code con los comandos de arriba.
2. Abre Claude Code y pega el bloque `/humanizer`, con 2 o 3 párrafos tuyos (un WhatsApp a un cliente, un post que sí escribiste tú) y después la descripción de IA.
3. Lee la primera versión, la crítica y la final. Comprueba que no cambió el precio, el horario ni un ingrediente, y que no añadió un dato que tú no diste.
4. Publica solo cuando el texto te suene a ti.

Ese ejemplo es nuestro, para que se vea el uso. El repo no habla de panaderías.

## Límites honestos

- **Revisa 26 señales; no «quita toda señal de IA».** El número de patrones cambia entre versiones: sitios de terceros han citado 24 o 29. El README oficial, el 16-nov-2026, dice 26.
- **No está hecha para engañar detectores de IA.** Lo dice el propio repo: edita para lectores humanos; los detectores **siguen marcando la mayoría** de sus textos. No la uses para hacer pasar un texto como «indetectable».
- La página de Wikipedia, consultada el 16-nov-2026, se presenta como una **guía de campo** (field guide), descriptiva y no prescriptiva. Ella misma advierte que no todo texto con esas señales fue escrito por IA. No es una política.
- El resultado no queda perfecto solo porque pasó por la skill. Léelo antes de publicarlo.
- «La primera skill que instalaría» es una recomendación de este video, no una afirmación del repo.

## Fuentes

Consultadas el 16-nov-2026, America/Caracas:

- README (26 patrones, instalación, muestra de voz, flujo de reescritura, detectores) y licencia MIT: https://github.com/blader/humanizer y https://raw.githubusercontent.com/blader/humanizer/main/README.md
- Estrellas (69.867) y licencia MIT: https://api.github.com/repos/blader/humanizer
- Guía de Wikipedia (field guide, no política): https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing
- Precios de Claude y que Claude Code no está en el plan Free: https://claude.com/pricing

---
¿Quieres que la dejemos instalada en tu agente, con una muestra de tu voz? Escríbeme por DM **@briananderson.ai**.
