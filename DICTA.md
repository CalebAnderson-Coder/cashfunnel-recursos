# DICTA: Handy, la app gratis para dictar en cualquier programa

Recurso del video «Deja de teclear». Brian Anderson / CashFunnel, 23 de noviembre de 2026.

Handy es una app de escritorio **gratis y open source** (licencia [MIT](https://github.com/cjpais/Handy/blob/main/LICENSE)) que convierte tu voz en texto y lo pega en la app que tengas abierta. Funciona **sin internet**: el audio se procesa en tu computadora.

- Sitio y descargas: [handy.computer](https://handy.computer)
- Código: [github.com/cjpais/Handy](https://github.com/cjpais/Handy) (unas 39,8 mil estrellas al 23-nov-2026)
- Versión al escribir esta guía: v0.10.1 (14-nov-2026)

Los datos salen del README oficial, consultado el 23-nov-2026. Si algo cambia en una versión nueva, manda el repo.

## Cómo funciona

1. **Aprietas** tu atajo de teclado (lo configuras en Ajustes).
2. **Hablas** mientras el atajo está activo (o en modo pulsar para empezar / pulsar para terminar).
3. **Sueltas**, y Handy transcribe tu voz con Whisper.
4. El texto **se pega** donde está tu cursor: tu correo, WhatsApp Web, un documento o el chat con la IA.

## Modelos (y el español)

- **Whisper** (Small, Medium, Turbo, Large): entiende español. Usa la GPU si tienes una. Medium es un buen punto de partida (unos 492 MB).
- **Parakeet V3**: optimizado para CPU, con detección automática de idioma.
- Ojo: el modelo «Parakeet Unified EN» es **solo inglés**. Para español usa Whisper.
- La primera vez Handy descarga el modelo; después todo corre local.

## Cómo se instala, por sistema

Descarga desde [handy.computer](https://handy.computer) o desde [GitHub Releases](https://github.com/cjpais/Handy/releases).

- **Mac:** el `.dmg`. También `brew install --cask handy`.
- **Windows:** el instalador `setup.exe`. También `winget install cjpais.Handy`.
- **Linux:** `.deb` (`sudo apt install ./Handy_…_amd64.deb`), `.rpm` o AppImage.
- El cask de Homebrew y el paquete de winget **no los mantienen los desarrolladores de Handy**. Si dudas, baja del sitio oficial.

Al abrirla por primera vez, dale los permisos que pide: **micrófono** y **accesibilidad** (para poder escribir en otras apps).

## Límites honestos

- **Apps como administrador (Windows):** Windows no deja que Handy pegue texto en apps que corren como administrador. El texto queda guardado en el historial. Para usarlo ahí, abre Handy también como administrador.
- **Linux:** para escribir en otras apps necesitas `xdotool` (X11) o `wtype` / `dotool` (Wayland). En Ubuntu 26.04 con Wayland, `wtype` no funciona: hay que usar `ydotool` (ver el README).
- **La precisión depende del modelo y de tu micrófono.** Los modelos grandes son más precisos pero más lentos en computadoras sin GPU.
- Es una app de la comunidad: no tiene soporte comercial.

## Créditos

- Handy, de [CJ Pais](https://github.com/cjpais) y contribuidores, licencia MIT.
- Sitio oficial: https://handy.computer
