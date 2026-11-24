# TRAMPA: BLA, la herramienta gratis que le pone trampas a la IA que intenta copiar tu app

Recurso del video sobre BLA (Blind LLM Agents). Brian Anderson / CashFunnel, noviembre de 2026.

**BLA** (`bla-agents`) es una herramienta **gratis y open source (licencia MIT)** que endurece lo que tú publicas (tu app, tu web, tu juego) para que a los agentes de IA que hacen ingeniería inversa les cueste mucho más entenderlo. Planta señuelos (llaves y código falsos, mapas de código trampa) y obstáculos que gastan los tokens y el presupuesto del analizador, sin cambiar lo que ven tus usuarios.

No es un antivirus ni un candado mágico: sube el costo de copiarte, no lo hace imposible (más abajo, los límites).

La palabra clave del video es **TRAMPA**.

## Enlaces oficiales

- **Repo:** https://github.com/qybaihe/bla (licencia MIT, unas **6.700 estrellas** y versión v3.6.0 el 24-nov-2026)
- **Sitio y guía de inicio:** https://bla.tools · https://bla.tools/get-started/
- **Preguntas frecuentes (con sus límites):** https://bla.tools/faq/
- **Paquete npm:** `bla-agents`
- Este software no es mío: te dejo el repo oficial y una guía con límites claros. Instálalo solo desde el repo o desde `npm i bla-agents`.

## Qué hace (y qué no)

- **Señuelos (Poison):** mete canarios con formato válido, mapas de código (SourceMaps) trampa y máquinas de estado «sombra» que parecen lógica real. La IA que analiza tu app se va por caminos falsos.
- **Agota el presupuesto (Exhaust):** dispara los límites por defecto del analizador y, según estimaciones de su propio modelo (no una medición), multiplica de **300× a 2.800×** los tokens que tendría que gastar.
- **Tu app sigue igual:** las trampas quedan en ramas que nunca se ejecutan, así que el resultado y la velocidad no cambian (según el README, los 14 objetivos de sus pruebas pasan los chequeos de equivalencia de entrada y salida).
- **Formatos:** JavaScript/TypeScript, Electron (ASAR), WebAssembly, Python, SQLite, binarios nativos, modelos GGUF/Safetensors y Android (DEX).
- **No es** para atacar ni para romper software ajeno: el proyecto es solo defensivo, para proteger **lo tuyo**.

## Requisitos

- **Node.js 22.13 o más nuevo** (o 24+). No necesitas compiladores ni empaquetadores extra.
- Tu proyecto ya **compilado** (`dist/`, `build/`, el `.asar`, el `.wasm`…): BLA trabaja sobre lo que sale del build, no sobre tu código fuente.
- Opcional: Claude Code, Codex, Cursor, Windsurf, Gemini CLI u otro agente compatible, si quieres pedírselo en lenguaje natural.

## Cómo usarlo (2 caminos)

### A. Un comando en la terminal

1. Compila tu proyecto como siempre.
2. En la carpeta del proyecto corre:

```sh
npx bla-agents harden .
```

   Revisa, protege y verifica. Escribe una copia protegida en `.bla-hardened/`: **todavía no se publica nada**.
3. Prueba esa copia. Si todo funciona, reemplaza tu build con la versión protegida:

```sh
npx bla-agents harden . --apply
```

4. ¿Algo salió mal? Vuelve al build original con `npx bla-agents harden . --restore`.

### B. Desde Claude Code o Codex

1. Registra BLA una vez en tu agente:

```sh
npx bla-agents setup
```

2. Pídeselo en el chat: «Harden my software against REA» (protege mi software contra agentes de ingeniería inversa).
3. El agente corre las herramientas de BLA por orden y **te pregunta antes** de reemplazar tu build. Después corre tus pruebas.

Hazlo **justo antes de publicar** cada versión, igual que en el video.

## Límites honestos

- **No es un sello anti-copia.** El propio sitio lo dice: sube el costo del análisis y planta señuelos, pero no es magia. Muchos de los límites que BLA dispara los puede subir quien analiza; en ese caso la trampa solo le hace gastar más intentos.
- **La ingeniería inversa manual** (una persona con Ghidra, Frida, LLDB o JADX) queda fuera de lo que miden sus pruebas.
- **Prueba antes de publicar.** `--apply` solo reemplaza el build (nunca tu código fuente) y guarda el original aparte, pero corre tus pruebas sobre la versión protegida antes de lanzarla.
- **Proyecto joven y muy activo:** saca versiones casi a diario. Fija la versión que probaste en tu pipeline.
- **No protege secretos mal guardados.** Si tu app trae una API key real en el código del cliente, sácala de ahí; BLA no la convierte en segura.

## Costo

- Herramienta y código: **gratis** (MIT).
- Si lo usas desde Claude Code o Codex, eso gasta de tu plan de siempre.

## Fuentes

- README del repo (secciones «30-Second Quick Start» y «How BLA Works»), consultado el 24-nov-2026.
- https://bla.tools, https://bla.tools/get-started/ y https://bla.tools/faq/, consultados el 24-nov-2026.
