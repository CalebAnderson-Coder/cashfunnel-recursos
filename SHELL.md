# SHELL — AweShell: tu agente publica la web y te da un enlace público

Palabra: **SHELL**
Alias: AWESHELL, AWE SHELL, HOSTING

> AweShell deja que tu agente (o tú, a mano) publique un sitio estático y te devuelva un enlace público.

**Oficial:** [https://aweshell.ai/en](https://aweshell.ai/en)  
**CLI:** [https://aweshell.ai/doc/cli-setup.md](https://aweshell.ai/doc/cli-setup.md) · `npm install -g @aweray/aweshell-cli`  
**Consola (AweRay):** [https://aweshell-console.aweray.com/en/console/file-hosting](https://aweshell-console.aweray.com/en/console/file-hosting)

Lo hace AweRay PTE. No confundir con otros proyectos llamados «aweshell» (hay un paquete de Emacs y otras tools). Este es aweshell.ai / `@aweray/aweshell-cli`. No hay repositorio público en GitHub (github.com/aweshell da 404).

## Qué es (y qué no es)

AweShell Drop publica un sitio **estático** (HTML, CSS, JS y archivos que el navegador descarga directo) a un enlace público, o deja que un agente lo publique por ti con un prompt. Para algo que todavía corre en tu computadora (por ejemplo localhost:3000) usan un **túnel local**, no un deploy en la nube.

No es un servidor con base de datos ni un reemplazo de Vercel/Netlify para apps completas. «Cualquier web que construya el agente» es una frase de video, no del sitio oficial.

## Precio y límites (lo que sí está escrito)

El hosting estático básico es gratis, según [la página de features](https://aweshell.ai/en/features) («Basic static hosting is completely free»; «AweShell agent publishing and basic static hosting are free»). No hay página de precios (`/en/pricing` da 404). No inventamos tarifas del túnel, del ancho de banda ni de planes de pago.

Límites oficiales:

- Un archivo < 25 MB; máximo 2000 archivos; total < 100 MB.
- Enlaces **sin reclamar**: tienen un límite de vigencia. El sitio no dice cuántos días.
- Enlaces **reclamados** a una cuenta AweRay: se quedan «a largo plazo» y se pueden apagar desde la consola. **No dicen «para siempre».**
- Subdominio propio: un prefijo de al menos 6 caracteres (letras, números y guiones), no un dominio que tú compraste. Cada cuenta tiene 2 cupos, hoy.
- Actualizar: le dices al agente «update the resource I just published» o lo vuelves a subir en la consola; el enlace público no cambia.
- Cifrado: el sitio habla de HTTPS automático, no de cifrado de archivos en reposo.

## Camino A — prompt + agente

1. Entra a [https://aweshell.ai/en](https://aweshell.ai/en) y copia el prompt oficial («Copy prompt for agents to publish»).
2. Pégalo en Gemini, GPT, Codex u otro agente que pueda ejecutar comandos. La home oficial lista Gemini, GPT, Codex y «Other Agents». Claude Code no aparece con nombre en esa lista, pero el CLI está pensado para agentes que ejecutan comandos y el flujo es el mismo.
3. Pídele que publique el sitio (el HTML de la carpeta actual, un zip o el build).
4. El agente instala el CLI si hace falta (`npm install -g @aweray/aweshell-cli`) y te devuelve el enlace.
5. Reclama ese enlace en tu cuenta AweRay para que no caduque.

## Camino B — arrastrar archivos

Arrastra un archivo, un `.zip` o una carpeta (por ejemplo el `dist` de un front-end) a la página. Te da el mismo tipo de enlace.

## Reclamar, actualizar, subdominio, túnel

- Reclama el enlace en tu cuenta para dejarlo «a largo plazo».
- Para actualizar, pide «actualiza el recurso que acabas de publicar» o súbelo de nuevo en la consola. El enlace no cambia.
- Si quieres una dirección más limpia, asigna un prefijo de subdominio en la consola (2 por cuenta).
- Si el sitio aún no está listo, usa el túnel local para que un cliente lo vea desde tu computadora, sin publicarlo.

## Checklist de primera prueba

- [ ] Una landing mínima (un HTML, un zip o la carpeta del build).
- [ ] Publicarla con el prompt o arrastrándola a AweShell.
- [ ] Abrir el enlace en el teléfono.
- [ ] Reclamar el enlace en una cuenta AweRay.
- [ ] (Opcional) Pedir una actualización y comprobar que el enlace es el mismo.

## Nota

El paquete npm también apunta a https://ficp.io; no afirmamos una relación más allá de lo que esté en el registro.
