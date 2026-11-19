# VIDEO: HyperFrames, la herramienta gratis de HeyGen para que tu agente haga videos

Recurso del video «HeyGen liberó gratis una herramienta para que tu agente haga videos». Brian Anderson / CashFunnel, 18 de noviembre de 2026.

**HyperFrames** es un framework **gratis y open source** del repo [heygen-com/hyperframes](https://github.com/heygen-com/hyperframes). Según su README, convierte HTML, CSS, media y animaciones en videos MP4 deterministas. El tagline del repo: «Write HTML. Render video. Built for agents.» Licencia [Apache 2.0](https://github.com/heygen-com/hyperframes), «with no per-render fees or commercial-use thresholds.» El README también dice que se usa en producción en HeyGen.

Los datos de esta guía salen del README y de la página del repo citados en el paquete del 18-nov-2026 (America/Caracas). Si una versión nueva cambia un comando o una cifra, mandan el GitHub y el sitio.

## Costo

- **El repo es gratis** (Apache 2.0) y **no cobra por cada video** («no per-render fees»). El render se hace en tu computadora o en Docker («Render locally or in Docker»).
- **Tú pones el entorno.** El README pide **Node.js 22+ y FFmpeg**. No afirmamos que el agente los instale solo, ni que esos programas sean gratis: no se verificó en el paquete.
- **No es “todo gratis para siempre”.** Dos de las nueve skills llevan la etiqueta **HyperFrames Pro**. El paquete no abrió una página de precios, así que aquí no hay un precio ni un nombre de plan.
- Para usarlo en Claude Code necesitas Claude Code (un plan de pago de Claude o la API). HyperFrames no trae un modelo propio.

## Cómo se instala en Claude Code

El README indica **dos comandos**:

```
claude plugin marketplace add heygen-com/hyperframes
claude plugin install hyperframes@hyperframes
```

El README dice: «HyperFrames ships 9 skills.» No enumeramos aquí qué hace cada una: hay que reabrir el README el día que las instales, porque esa lista puede cambiar.

## Cómo se usa (según el repo)

La idea es esta: **tú describes el video, el agente escribe el proyecto y HyperFrames lo convierte en un MP4.** Sale «a real project you can change down to the frame», y puedes ver la vista previa en el navegador («Preview instantly in the browser»). No es un generador de video con un modelo de IA: convierte HTML en video. No prometemos calidad del resultado.

El ejemplo del propio README: con `/hyperframes`, «create a 10-second product intro with a fade-in title, a background video, and subtle background music.» Es el ejemplo del repo, no una prueba nuestra.

## Límites honestos

- Hay que instalar **Node.js 22+ y FFmpeg**.
- **Dos de las nueve skills son Pro** (`/reverse-any-video` y `/style-sampling`, con la etiqueta «HyperFrames Pro»). No damos precio.
- No es «sin tocar nada» ni «en automático»: describes el video y puedes editar el proyecto cuadro por cuadro.
- No lo presentes como un editor, ni como algo «solo para Claude Code», ni como si «acabara de salir»: esas frases no están en la fuente.

## Créditos

- HyperFrames: [heygen-com/hyperframes](https://github.com/heygen-com/hyperframes), licencia Apache 2.0. No es un producto mío ni tengo relación con el proyecto.
- Documentación citada en el paquete: [hyperframes.heygen.com/introduction](https://hyperframes.heygen.com/introduction).

## Fuentes

Consultadas en el paquete del 18-nov-2026, America/Caracas:

- README: https://raw.githubusercontent.com/heygen-com/hyperframes/main/README.md
- Repo: https://github.com/heygen-com/hyperframes
- Introducción: https://hyperframes.heygen.com/introduction

---
¿Quieres que lo dejemos instalado en tu Claude Code y armemos juntos el primer proyecto? Escríbeme por DM **@briananderson.ai**.
