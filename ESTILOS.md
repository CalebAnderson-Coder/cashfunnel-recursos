# ESTILOS: Lemo-Opuscar, 99 estilos de animación para Claude

Recurso del video sobre Lemo-Opuscar. Brian Anderson / CashFunnel, noviembre de 2026.

Lemo-Opuscar es una **skill (plugin) gratis y open source para Claude Code** con 99 estilos de película: pizarra, caricatura, acuarela, documental y muchos más. Eliges un estilo, le cuentas tu idea y el agente arma la historia, la narración y el guion gráfico, y renderiza la película **en código**, cuadro por cuadro. No es un modelo de video ni usa metraje de stock.

El gancho del video la compara con **After Effects**, que cobra desde 23 dólares al mes. Matiz honesto: no es un sustituto 1:1 de After Effects (no es un editor con línea de tiempo); es una forma de que tu agente haga animaciones en código.

## Enlaces oficiales

- **Galería (para elegir estilo):** https://lemomo-ai.github.io/lemo-opuscar/
- **Repo oficial:** https://github.com/lemomo-ai/lemo-opuscar
- **Índice de estilos:** https://github.com/lemomo-ai/lemo-opuscar/blob/main/styles/README.md

## Precio de la alternativa de pago (After Effects)

En la página oficial de planes de Adobe After Effects, consultada el **14-nov-2026** (America/Caracas): plan individual **US$22,99 al mes** con compromiso anual y pago mensual. El video lo redondea a “23 dólares al mes”. Otros ciclos de pago cuestan distinto; revisa https://www.adobe.com/products/aftereffects/plans.html el día que lo contrates.

## Cómo instalarla

En tu terminal, con Claude Code instalado:

```sh
claude plugin marketplace add lemomo-ai/lemo-opuscar
claude plugin install lemo-opuscar@lemolab
```

Después úsala desde cualquier carpeta. La primera vez descarga las guías, herramientas y prompts de estilo a `~/lemo-opuscar`. El proyecto de cada película (del código al video terminado) queda en la carpeta desde donde la pediste.

Alternativa: clonar el repo (las películas quedan en `films/<nombre>/`):

```sh
git clone https://github.com/lemomo-ai/lemo-opuscar.git
cd lemo-opuscar
claude
```

Para actualizar (y luego reiniciar Claude Code):

```sh
claude plugin marketplace update lemolab && claude plugin update lemo-opuscar@lemolab
```

## Cómo pedírselo a Claude

Una frase basta. Nombra el estilo en inglés o por su carpeta (ver el índice):

```text
Make a 45-second film in the watercolor style about the coffee farm my family runs. Warm female narrator.
```

En español también funciona describirlo, por ejemplo: «Haz una película de 40 segundos en estilo whiteboard sobre cómo funciona mi negocio, con narración en español». Puedes añadir duración, narrador, tus fotos o tu música.

**Tu propio estilo:** el README explica cómo cambiar un estilo o empezar uno en blanco con los colores, el logo y el tono de tu marca, y guardarlo en la librería (sección “Make a style your own”).

## Requisitos y límites (ojo antes de instalar)

- La skill es gratis, pero **necesitas Claude Code** y tu plan de Claude va aparte.
- Está **afinada para Claude**: Fable, Opus y Sonnet funcionan; el README pide esfuerzo **alto** (`/effort high` en Claude Code). Otros modelos pueden no reproducir bien los estilos.
- Una película le toma al agente **unos 30–60 minutos** y bastantes tokens.
- Necesitas **Node 20+, ffmpeg 7+ y Python 3.11+** (o uv); el agente instala el resto. Ubuntu 24.04 trae ffmpeg 6.1, que es muy viejo: usa una build estática.
- Prueba primero con una película corta.

## Licencias (en corto)

- **Código:** MIT.
- **Documentos y prompts de estilo** (`STYLE.md`, guías): CC BY-NC 4.0, es decir, uso no comercial con crédito a «Lemo-Opuscar by Lemomo (LemoLab)». Puedes usarlos para hacer tus propias películas, incluidas comerciales.
- **Películas demo de la galería:** CC BY 4.0, con crédito.
- **Las películas que hagas tú:** son tuyas, también para uso comercial; el material de terceros que uses conserva su licencia.
- Seis pistas de voz de las demos no son CC BY 4.0 (ver la sección Licence del README).

## Fuentes

Consultadas el 14-nov-2026, America/Caracas:

- README oficial: https://github.com/lemomo-ai/lemo-opuscar (99 estilos, instalación, “Before you start”, Licence)
- Galería: https://lemomo-ai.github.io/lemo-opuscar/
- Adobe After Effects, planes: https://www.adobe.com/products/aftereffects/plans.html

Guía educativa de Brian Anderson. No es un producto de Lemomo, Anthropic ni Adobe, ni una promesa de resultados.
