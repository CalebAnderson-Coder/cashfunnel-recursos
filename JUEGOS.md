# JUEGOS: 79 skills gratis para que tu agente cree videojuegos

Recurso del video «Claude Code ya crea videojuegos completos». Brian Anderson / CashFunnel, noviembre de 2026.

**awesome-gamedev-agent-skills** es una colección **gratis y open source (licencia Apache-2.0)** de **79 skills de desarrollo de videojuegos más un router** para tu agente de código (Claude Code, Cursor, Codex, Gemini CLI, GitHub Copilot y más). Cubre **12 motores**: Godot, Unity, Unreal, Ebitengine, Phaser, PixiJS, three.js, Bevy, pygame, LÖVE, Defold y Roblox.

Tú no eliges skills: describes lo que quieres y el **router** detecta tu motor (por ejemplo, un `project.godot` significa Godot) y carga solo las 2 o 3 skills que hacen falta antes de que el agente escriba código.

Matiz honesto: no es un motor ni un generador mágico de juegos. Le da a tu agente el conocimiento correcto de cada motor; el juego lo sigues construyendo tú con él, paso a paso.

## Enlace oficial

- **Repo:** https://github.com/gamedev-skills/awesome-gamedev-agent-skills (licencia Apache-2.0, unas **10.500 estrellas** el 23-nov-2026)
- **La palabra clave del video es JUEGOS.**

## Cómo instalarlo

**Opción 1, cualquier agente** (necesita Node.js 22.20 o superior):

```sh
npx skills add gamedev-skills/awesome-gamedev-agent-skills
```

Añade `--list` para ver antes qué instala, `-g` para todos tus proyectos o `-a claude-code` (o `-a cursor`, `-a gemini-cli`…) para un agente concreto.

**Opción 2, plugin de Claude Code:**

```sh
claude plugin marketplace add gamedev-skills/awesome-gamedev-agent-skills
claude plugin install gamedev@awesome-gamedev-agent-skills
```

¿Solo usas un motor? Instala el router y tu motor nada más:

```sh
claude plugin install router@awesome-gamedev-agent-skills
claude plugin install godot@awesome-gamedev-agent-skills   # o: unity · unreal · ebitengine · web-engines · other-engines
```

## Cómo pedírselo

Habla normal; el router elige las skills. Ejemplos del propio README:

| Lo que pides | Skills que carga solo |
|---|---|
| «add a double jump to my Godot player» | `godot-2d-movement` + `platformer` |
| «make an inventory for my Unity RPG» | `unity-scriptableobjects` + `rpg` + `save-systems` |
| «procedural dungeon roguelike in Godot» | `godot-tilemap` + `procedural-gen` + `roguelike` |
| «make a cohesive pixel-art player, enemies, and tiles» | `create-game-assets` + el importador de tu motor |
| «publish my game on itch with butler» | `itch-publish` |

En español también funciona: «añade un doble salto a mi personaje de Godot».

Para publicar hay skills de flujo como `steam-publish` (SteamPipe, `steamcmd`, ramas beta) e `itch-publish`.

## Requisitos y límites

- Las skills son gratis, pero **necesitas un agente de código** (por ejemplo Claude Code) y su plan va aparte.
- Están fijadas a versiones actuales de cada motor (Godot 4.7.2, Unity 6.3 LTS, Unreal 5.8, Phaser 4.2.1, three.js r187…, revisadas el 11-nov-2026 según el README).
- El README reporta que en 366 pruebas a ciegas se cargó la skill correcta en el 98,7 % de los pedidos que necesitaban una; los detalles y límites están en `evals/RESULTS.md` del repo.
- Publicar en Steam requiere tu propia cuenta de Steamworks y su cuota; la skill solo te guía en el proceso.

## Créditos de las imágenes del video

- Página del repo y su banner: capturas de https://github.com/gamedev-skills/awesome-gamedev-agent-skills (Apache-2.0).
- Juego de plataformas de demostración: hecho por nosotros con **Kenney Pixel Platformer** (CC0). Personajes y muebles: **Kenney Toon Characters** y **Furniture Kit** (CC0).
- Escenas 3D: ejemplos oficiales de **three.js** (MIT); modelo «Littlest Tokyo» de **Glen Fox**, licencia **CC-BY 4.0**.
- Logos de motores: **simple-icons** (CC0); marcas de sus dueños.
- Tiendas: capturas públicas de Steam e itch.io.
- La terminal de Claude Code del video es una recreación con el ejemplo real del README.
