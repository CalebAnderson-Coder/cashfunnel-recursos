# COMANDO: CLI-Anything, el repo abierto para que un agente maneje Blender, GIMP y LibreOffice

Recurso del video «Claude Code maneja Blender y GIMP sin tocar un solo botón». Brian Anderson / CashFunnel, 18 de noviembre de 2026.

**CLI-Anything** es el repositorio [HKUDS/CLI-Anything](https://github.com/HKUDS/CLI-Anything) («Making ALL Software Agent-Native»). Licencia [Apache 2.0](https://github.com/HKUDS/CLI-Anything): «free to use, modify, and distribute.» El repo es abierto y gratis. Eso no hace gratis a Claude Code ni al modelo.

Los datos de esta guía salen del README del repo, consultado en el paquete del 18-nov-2026 (America/Caracas). Si una versión nueva cambia un comando o un límite, manda el GitHub.

## Para qué sirve

Un agente trabaja bien por terminal. El README lo dice así: «CLI is the universal interface for both humans and AI agents.» Muchos programas solo traen botones. Este repo apunta a que le pidas el trabajo al agente y él use el programa.

Ya trae ejemplos (nombres del README):

- **LibreOffice** — Office Suite (Writer, Calc, Impress)
- **GIMP** — Image Editing
- **Blender** — 3D Modeling & Rendering

No citamos una cantidad total de aplicaciones ni de tests: el README se contradice en esas cifras. No decimos «cualquier programa» ni «sin que hagas nada». Tampoco comparamos con MCP: el README no lo hace.

## Cómo se instala en Claude Code

El README indica, como plugin:

```
/plugin marketplace add HKUDS/CLI-Anything
/plugin install cli-anything
/cli-anything ./gimp
```

Escribes `/cli-anything` y la carpeta del programa. El repo también lista otros agentes; no es solo para Claude Code.

## Siete fases (en corto)

El pipeline del README, resumido como en el video:

1. **Lee el código fuente** (Analyze: «Scans source code, maps GUI actions to APIs»).
2. **Diseña los comandos** (Design: «Architects command groups, state model, output formats»).
3. **Construye la herramienta** (Implement: «Builds Click CLI with REPL, JSON output, undo/redo»).
4. **La prueba y la instala** (Write Tests + Publish: test suite y «Creates setup.py, installs to PATH»).

El README nombra siete fases en total (incluye Plan Tests y Document). No decimos que quede «lista para producción».

## Tres límites (del propio README)

1. **Trabaja desde el código.** Si el programa no comparte el código («only provides compiled binaries that require decompilation»), la calidad y la cobertura «will degrade substantially». No decimos que «no funciona»: se degrada.
2. **Pide modelos de primera línea.** «CLI-Anything relies on frontier-class models.» «Weaker or smaller models may produce incomplete or incorrect CLIs that require significant manual correction.» No nombramos versiones de modelo ni precios: esa lista cambia.
3. **Suele hacer falta refinarla.** «Running `/refine` one or more times is often needed to push the CLI's performance and coverage to production quality.» La fuente dice «often», no «siempre».

## Límites honestos

- El software del repo es gratis (Apache 2.0). Claude Code y el modelo se pagan aparte.
- La calidad depende de que haya código fuente y de un modelo de primera línea.
- No prometemos ahorro de tiempo ni un resultado listo para producción.
- Esta guía no afirma una afiliación universitaria: no se verificó en una fuente primaria del paquete.

## Fuentes

Consultadas en el paquete del 18-nov-2026, America/Caracas:

- https://github.com/HKUDS/CLI-Anything

---
¿Quieres que lo instalemos en tu Claude Code y elijamos un solo programa para el primer intento? Escríbeme por DM **@briananderson.ai**.
