# TOKENS: 3 herramientas gratis para cuando Claude Code te corta por límite

Recurso del video «3 herramientas gratis para cuando Claude Code te corta por límite». Brian Anderson / CashFunnel, 16 de noviembre de 2026.

Tres herramientas **gratis y open source** para cuando Claude Code se te corta a mitad de tarea. **Ninguna te sube el límite** de tu plan. Una hace que el agente escriba menos, otra mide tu consumo y otra ordena el trabajo.

- **Ponytail**, de [DietrichGebert](https://github.com/DietrichGebert): una skill (una instrucción que se le instala al agente) para que escriba solo lo que la tarea necesita. Código: [github.com/DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail) (192.081 estrellas al 16-nov-2026, API de GitHub). Licencia [MIT](https://github.com/DietrichGebert/ponytail/blob/main/LICENSE).
- **ccusage**, de [ryoppippi](https://github.com/ryoppippi): lee los datos de uso que ya están en tu computadora y te arma reportes. Código: [github.com/ccusage/ccusage](https://github.com/ccusage/ccusage) (el atajo [github.com/ryoppippi/ccusage](https://github.com/ryoppippi/ccusage) apunta al mismo repo; 19.453 estrellas al 16-nov-2026). La licencia del programa, en `apps/ccusage/LICENSE`, es [MIT](https://github.com/ccusage/ccusage/blob/main/apps/ccusage/LICENSE) (Copyright 2025 ryoppippi). Docs: [ccusage.com](https://ccusage.com/).
- **Agent Skills**, de [Addy Osmani](https://github.com/addyosmani): un paquete de skills de ingeniería para agentes. Código: [github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) (118.291 estrellas al 16-nov-2026). Licencia [MIT](https://github.com/addyosmani/agent-skills). El README lo confirma: «MIT - use these skills in your projects, teams, and tools.»

**No es LÍMITE** (tres reglas antes de darle dinero a un agente), **ni SKILLS** (Marketing Skills de Corey Haines), **ni SETUP** (ECC). Aquí el tema es instalar y usar estas tres herramientas.

Los datos de esta guía salen de los README, de las licencias y de la guía de bloques de ccusage, consultados el 16-nov-2026. Si una versión nueva cambia un comando o una cifra, mandan el GitHub y el sitio.

## Costo real

- **Las tres herramientas son gratis** (MIT). No te cobran por instalarlas. Ponytail tiene un botón de Sponsor: es una donación, no un precio.
- **Tú pagas Claude Code** (u otro agente donde las corras). En [claude.com/pricing](https://claude.com/pricing) (consultado el 16-nov-2026), **Claude Code no está en el plan Free**. El plan Pro cuesta **20 USD al mes** si pagas mes a mes, o **17 USD al mes** si pagas el año por adelantado (200 USD). Los precios no incluyen impuestos y pueden cambiar: revísalos el día que contrates.
- ccusage también reporta uso de Codex y de otros agentes. No afirmamos el precio de cada uno.

## 1. Ponytail: que escriba solo lo que hace falta

El README la define así: «Ponytail is one prompt» (`skills/ponytail/SKILL.md`). Se instala como plugin o como skill. Su regla, en palabras del autor, **nunca fue «los menos tokens posibles»**: es escribir solo lo que la tarea necesita, y no recortar validación, manejo de errores, seguridad ni accesibilidad. El código sale más chico porque es el necesario, no porque esté «golfed». El menor costo y la menor latencia, dice, son un efecto secundario.

**La medición es del autor, no una auditoría externa.** El README (consultado el 16-nov-2026) publica, en un benchmark con Claude Code, el mismo agente con y sin la skill, **39 tareas**, Opus 5.5, 5 corridas cada una: **53 % menos código** y **45 % menos tokens**. También lista 41 % menos tiempo y 26 % menos costo, y un dato de tests (98 % de la lógica riesgosa sale con test, frente a 68 % sin la skill). No uses esas cifras como promesa de lo que te va a pasar a ti, ni como ahorro de plata garantizado. Versiones anteriores del README publicaron otros números; valen solo los de hoy.

Instálala solo desde `DietrichGebert/ponytail` en GitHub o `@dietrichgebert/ponytail` en npm. El README avisa que no publica archivos `.exe` ni `.dll`: una copia que sí los traiga no es la suya.

**En Claude Code:**

```
/plugin marketplace add DietrichGebert/ponytail
/plugin install ponytail@ponytail
```

En Codex, el README indica `codex plugin marketplace add DietrichGebert/ponytail` y `codex plugin add ponytail@ponytail`, y después abrir `/hooks` para confiar en sus dos hooks. En otros agentes, copia `AGENTS.md` al proyecto o instala `skills/ponytail/SKILL.md` como skill (el paso a paso está en [INSTALL.md](https://github.com/DietrichGebert/ponytail/blob/main/INSTALL.md)).

Queda activa en la sesión. Comandos útiles: `/ponytail` (nivel o apagarla), `/ponytail-review` y `/ponytail-audit`. Hay una banda de costos en Claude Code 2.1.290 o más nuevo; no es necesaria para usar la skill.

## 2. ccusage: mide tu consumo

El README dice: «ccusage reads local usage data from coding agent CLIs and turns it into daily, weekly, monthly, and session reports.» No tiene que «subir» tus logs a un servicio para armarte el reporte básico. Para correrla sin red, el comando trae `--offline`.

La guía de bloques, en [ccusage.com/guide/blocks-reports](https://ccusage.com/guide/blocks-reports), lo explica así: **«Blocks reports show your Claude Code usage grouped by 5-hour billing windows.»** En el bloque activo te muestra el **tiempo que le queda a esa ventana de cinco horas** («Time remaining in the 5-hour window» / «Currently running block with time remaining»).

Eso no es, por sí solo, el límite de tu plan ni el porcentaje que te queda del cupo. Si quieres comparar contra un tope, tú se lo pasas con `--token-limit`. El monitor en vivo `blocks --live` **fue retirado en la v18.0.0**; el sitio indica usar el comando `statusline` para el seguimiento en tiempo real.

Necesitas un runner de Node (`npx`, `bunx` o similar). No afirmamos una versión mínima de Node.

```bash
npx ccusage@latest
npx ccusage@latest blocks
npx ccusage@latest blocks --active
```

`blocks --active` se concentra en la ventana que está corriendo: tiempo restante, ritmo de tokens y una proyección. También hay reportes `daily`, `weekly`, `monthly` y `session`.

## 3. Agent Skills (Addy Osmani): ordena el trabajo

El README las presenta como «Production-grade engineering skills for AI coding agents.» El creador es Addy Osmani; en la tabla del equipo aparecen dos colaboradores (Federico Bartoli y Joan León). **No es un producto de Google.**

El paquete trae **25 skills en total: 24 de ciclo más la meta-skill `using-agent-skills`**. Las 24 cubren el ciclo: **definir, planear, construir, verificar, revisar y lanzar** (Define, Plan, Build, Verify, Review, Ship). Hay 9 comandos de entrada (`/spec`, `/plan`, `/build`, `/test`, `/constraints`, `/review`, `/webperf`, `/code-simplify`, `/ship`). En Claude Code, si un comando choca con uno propio (como `/review`), el README pide la forma con espacio de nombres: `/agent-skills:review`.

El README también dice que las skills «activate automatically based on what you're doing». Es la afirmación del repo, no una garantía de que el agente siempre elija la correcta. Este paquete **no promete ahorrar tokens** ni subirte el límite: ordena el trabajo en pasos.

**La vía más rápida**, según el README (sirve en Claude Code, Cursor, Codex, Copilot y otros):

```bash
npx skills add addyosmani/agent-skills
```

Eso instala las 25. También puedes listarlas antes con `--list` o instalar una sola con `--skill`.

**En Claude Code**, como plugin:

```
/plugin marketplace add addyosmani/agent-skills
/plugin install agent-skills@addy-agent-skills
```

Si el marketplace falla por SSH, el README sugiere añadir el repo por HTTPS: `/plugin marketplace add https://github.com/addyosmani/agent-skills.git`.

## Ejemplo concreto (dueño de un negocio)

Imagina que estás armando, con Claude Code, la web de reservas de tu consultorio, y se te corta la sesión a mitad del formulario.

1. En la terminal, corre `npx ccusage@latest blocks --active`. Vas a ver cuánto le queda a la ventana de cinco horas. Si está por cerrarse, guarda, cierra el pedido grande y retoma en la siguiente ventana, o parte el trabajo.
2. Instala Ponytail con los dos comandos de plugin. En la próxima sesión, pídele una sola cosa concreta: el formulario de reserva, no «toda la web». La skill apunta a que el agente reutilice lo que ya hay y no arme un calendario de 300 líneas si basta un campo de fecha.
3. Instala Agent Skills y empieza con `/spec` o `/plan`. Define la reserva (quién agenda, qué horarios, qué pasa si alguien cancela) y parte el trabajo en tareas chicas, en vez de un solo hilo eterno que se come la ventana.

Ese ejemplo es nuestro, para que se vea el uso. Ninguno de los tres repos habla de un consultorio, y ninguno te garantiza que dejes de toparte con el límite.

## Límites honestos

- **Ninguna te sube el límite** de Claude Code. Una escribe menos, otra mide tu consumo, otra ordena el trabajo.
- Las cifras de Ponytail (53 % menos código, 45 % menos tokens, y las demás del README) son del autor, con un método y un conjunto de tareas concretos. No son una auditoría externa y no prometen el mismo resultado en tu proyecto.
- ccusage te muestra el uso y el tiempo que le queda al bloque de cinco horas. No te «avisa en vivo» con `blocks --live` (ya no existe en v18). No confundas ese reporte con el cupo de tu plan.
- Agent Skills no es un ahorrador de tokens. El README habla de «progressive disclosure» para que cada skill cargue solo lo necesario; eso no es una promesa de que gastes menos en tu plan.
- «Gratis» se sostiene por la licencia MIT y porque no hay un pago para instalarlas. Claude Code sigue siendo de pago.

## Fuentes

Consultadas el 16-nov-2026, America/Caracas:

- Ponytail (README, benchmark de 39 tareas, instalación, «Ponytail is one prompt», «The rule was never "fewest tokens."», MIT): https://github.com/DietrichGebert/ponytail y https://raw.githubusercontent.com/DietrichGebert/ponytail/main/README.md
- Estrellas de Ponytail (192.081) y licencia MIT: https://api.github.com/repos/DietrichGebert/ponytail
- ccusage (README, «reads local usage data», `npx ccusage@latest`, MIT en `apps/ccusage/LICENSE`): https://github.com/ccusage/ccusage · https://raw.githubusercontent.com/ccusage/ccusage/main/apps/ccusage/README.md · https://raw.githubusercontent.com/ccusage/ccusage/main/apps/ccusage/LICENSE
- Estrellas de ccusage (19.453): https://api.github.com/repos/ccusage/ccusage (el clasificador de GitHub marca el repo como «Other» porque el LICENSE de la raíz solo apunta a `./apps/ccusage/LICENSE`; el archivo del programa es MIT)
- Bloques de 5 horas, tiempo restante y retiro de `blocks --live` en v18.0.0: https://ccusage.com/guide/blocks-reports
- Agent Skills (README, 24 + 1, fases, instalación, MIT, equipo): https://github.com/addyosmani/agent-skills y https://raw.githubusercontent.com/addyosmani/agent-skills/main/README.md
- Estrellas de Agent Skills (118.291) y licencia MIT: https://api.github.com/repos/addyosmani/agent-skills
- Precios de Claude y que Claude Code no está en el plan Free: https://claude.com/pricing

---
¿Quieres que las dejemos instaladas en tu Claude Code y veamos juntos tu primera ventana de uso? Escríbeme por DM **@briananderson.ai**.
