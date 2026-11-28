# MODERNO: Modern Web Guidance, la guía que hace que tu agente de código arme webs con lo que el navegador ya trae

Pediste la palabra MODERNO. Aquí va el resumen.

Modern Web Guidance es un conjunto de skills, es decir, instrucciones empaquetadas que un agente de código lee cuando las necesita. Le dan al agente buenas prácticas de desarrollo web y datos de compatibilidad entre navegadores, para que deje de usar soluciones viejas y use lo que el navegador ya resuelve solo. Es open source y la cuidan los equipos de Chrome, Edge, Firefox y MDN.

Esta guía te cuenta qué mide la prueba de Chrome, qué necesitas para instalarla y el comando. Las explicaciones son nuestras; los comandos y las cifras salen de las páginas oficiales.

## Antes de empezar: cuatro avisos

- **Sirve si haces web con un agente de código.** Por ejemplo Claude Code o Codex. La documentación dice que funciona con agentes que aceptan skills. Si no usas uno, pásale esta guía a quien te hace la web.
- **Las cifras son de la prueba de Chrome, no de tu web.** El equipo de Chrome dice que, en su propia prueba, los agentes sin guía pasan cerca del 50 % de los chequeos y con la guía cerca del 90 %. No es una auditoría de tu sitio ni una promesa de cuánto va a mejorar.
- **El resultado cambia según el agente.** En la tabla del repositorio del 20 de noviembre de 2026, con 229 tareas, tres agentes pasaron de 49 % a 85 %, de 54 % a 94 % y de 56 % a 97 %.
- **Está en inglés.** El repositorio y las guías que lee el agente están en inglés. Tú le puedes seguir escribiendo a tu agente en español.

## Qué problema resuelve

Los agentes de código aprendieron de mucho código viejo. Por eso tienden a resolver con JavaScript escrito a mano cosas que el navegador ya trae integradas. El equipo de Chrome da un ejemplo: al animar o cerrar ventanas emergentes, los modelos suelen armar arreglos propios en lugar de usar las funciones de HTML y CSS hechas para eso.

Con la guía instalada, cuando le pides una tarea de web, el agente consulta primero la recomendación actual y después escribe el código.

## Qué necesitas

- Un agente de código que acepte skills.
- Node.js versión 22 o más nueva en tu computadora.
- Una terminal abierta en la carpeta de tu proyecto.

## Cómo se instala

Corre este comando:

```
npx modern-web-guidance@latest install
```

Abre un asistente que te hace unas preguntas y deja la skill instalada. Según la documentación, instalar por esta vía activa las actualizaciones automáticas.

Si prefieres instalarla desde tu agente, la documentación oficial da comandos propios para cada uno. Dos ejemplos:

Claude Code:

```
claude plugin marketplace add GoogleChrome/modern-web-guidance
claude plugin install modern-web-guidance@googlechrome
```

Codex:

```
codex plugin marketplace add GoogleChrome/modern-web-guidance
codex plugin add modern-web-guidance@googlechrome
```

La documentación advierte que la mayoría de estas vías alternativas no se actualizan solas.

## Cómo funciona una vez instalada

1. Le pides a tu agente una tarea de web, con tus palabras.
2. El agente activa la skill porque la tarea es de web.
3. Busca la guía que corresponde. Esa búsqueda corre en tu computadora.
4. Lee la guía y escribe el código siguiendo esa recomendación.

No tienes que nombrar la guía en cada pedido. Aun así, revisa el resultado: que el agente active la skill no garantiza que la siga al pie de la letra en cada tarea.

## Probarla sin instalar

Puedes ver qué guías trae antes de instalar nada:

```
npx modern-web-guidance@latest search "animate a dialog modal backdrop"
```

Te devuelve una lista de guías relacionadas con esa búsqueda. La búsqueda va en inglés.

## Si tu proyecto ya existe: el modo de modernización (auditoría)

Para webs que ya existen, la documentación de Chrome describe un **flujo de modernización** (en el README aparece como el escaneo `legacy-scan`). Busca patrones viejos en tu proyecto y le ayuda al agente a cambiarlos por funciones nuevas del navegador. Pide la **versión 1.0 o más nueva**: instala o actualiza con `npx modern-web-guidance@latest install` o `npx modern-web-guidance@latest update`.

Dos formas de usarlo:

1. **Pídeselo al agente en tus palabras.** La documentación da este ejemplo de pedido (en inglés): «Modernize this repository using Modern Web Guidance. Scan our frontend files for legacy patterns, verify the findings, and propose a modernization plan before making any code edits.» Es decir: que escanee, verifique y **te proponga un plan antes de tocar código**. También puedes apuntarlo a una carpeta concreta.
2. **Correr el escaneo tú mismo** en la carpeta del proyecto:

```
npx modern-web-guidance@latest legacy-scan .
```

Lo que dice la documentación sobre cómo funciona: el escaneo corre en tu computadora y **no hace llamadas a un modelo de IA ni gasta tokens**. Los hallazgos los revisa después tu agente, que descarta los falsos positivos mirando el código de alrededor.

Ten en cuenta sus límites:

- **Es una lista corta de patrones, no una auditoría completa.** Revisa solo los patrones que se pueden detectar sin falsos positivos: según la documentación, cerca del 20 % de unas 200 guías. No revisa todo tu código ni garantiza que tu web quede «moderna».
- **No es obligatorio que cambie algo.** Código viejo que funciona puede dejarse como está; decide con quien te hace la web.
- Si nombras un solo componente en tu pedido, el agente hace una consulta normal de guía, no el escaneo del proyecto.
- La documentación dice que la integración con CI/CD (revisión automática al subir cambios) todavía está en desarrollo.

## Privacidad

El repositorio avisa que la herramienta envía a Google datos de uso anónimos: conteo de instalaciones, nombre del agente, qué guías se consultan y las búsquedas que hace el agente. Dice que no recoge tus pedidos originales. Para desactivarlo, define la variable de entorno `DISABLE_TELEMETRY=1`.

## Cuánto cuesta

El código del proyecto se publica con licencia Apache 2.0 y se instala con un comando, sin pago al proyecto. Eso no cubre lo que ya pagues por tu agente de código.

## Por dónde empezar si no programas

1. Pregúntale a quien te hace la web si usa un agente de código.
2. Si lo usa, pásale esta guía y el enlace del repositorio.
3. Pídele que te cuente qué cambió en tu proyecto después de instalarla.

## Enlaces

- Repositorio oficial: https://github.com/GoogleChrome/modern-web-guidance
- Cómo empezar (documentación de Chrome): https://developer.chrome.com/docs/modern-web-guidance/get-started
- La medición del equipo de Chrome: https://developer.chrome.com/blog/top-10-things-ai-gets-wrong-in-web-dev
- Tablero con los resultados de la prueba: https://googlechrome.github.io/modern-web-guidance-src/
- Flujo de modernización (documentación de Chrome): https://developer.chrome.com/docs/modern-web-guidance/modernization-workflow

## Fuentes

Consultadas el 28-nov-2026 (America/Caracas):

- README oficial (instalación, «Requires Node.js 22 or later», `legacy-scan`, telemetría, tabla de resultados del 20-nov): https://raw.githubusercontent.com/GoogleChrome/modern-web-guidance/main/README.md
- Licencia Apache 2.0 (API de GitHub): https://api.github.com/repos/GoogleChrome/modern-web-guidance
- Instalación y actualizaciones automáticas: https://developer.chrome.com/docs/modern-web-guidance/get-started
- Flujo de modernización, escaneo local sin llamadas a un modelo y alcance del ~20 %: https://developer.chrome.com/docs/modern-web-guidance/modernization-workflow
- Cifra «cerca de 50 % → cerca de 90 %»: https://developer.chrome.com/blog/top-10-things-ai-gets-wrong-in-web-dev

---

Guía de Brian Anderson / CashFunnel, noviembre de 2026. Resumen propio en español; los nombres, comandos y enlaces salen de las páginas oficiales. Este material no es de los autores originales ni está patrocinado por ellos.

Si quieres aprender a hacer reels con IA paso a paso, la comunidad «Contenido en Sistema» en Skool es gratis: https://www.skool.com/primer-empleado-ia-6500
