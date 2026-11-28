# TOKENS: FreeLLMAPI, un solo endpoint para los planes gratis de muchos proveedores de IA

Recurso del video sobre FreeLLMAPI. Brian Anderson / CashFunnel, 28 de noviembre de 2026.

> **Aviso importante: es para experimentar, NO para producción. No metas datos de clientes.** El propio proyecto lo dice así: es para experimentación personal y aprendizaje, no para producción. Tu pedido sale de tu computadora hacia el proveedor gratis que el router elija en ese momento, y cada proveedor tiene sus propias reglas sobre lo que hace con tus datos. Úsalo con pruebas, ideas y proyectos propios. Nada de listas de clientes, mensajes de clientes, contratos ni datos personales.

**FreeLLMAPI** es un programa **gratis y open source (licencia MIT)**, del repo [tashfeenahmed/freellmapi](https://github.com/tashfeenahmed/freellmapi) (59.527 estrellas al 28-nov-2026, API de GitHub). Lo instalas en tu computadora y hace de «puerta única»: tú creas cuentas gratis en varios proveedores de IA, le pasas esas claves y él te da **un solo endpoint compatible con OpenAI**. Para cada pedido elige un modelo que esté disponible y dentro de los límites del plan gratis; si uno se llena o falla, pasa al siguiente.

Esta guía te cuenta qué es, cómo se instala, cómo se usa y dónde se queda corto. Las explicaciones son nuestras; los comandos y las cifras salen del README y de la documentación oficial, consultados el 28-nov-2026.

**No es lo mismo que la guía de abajo.** Aquí el tema es seguir usando un agente sin pagar por cada pedido, con planes gratis de otros proveedores. Más abajo está la guía anterior de TOKENS (Ponytail, ccusage y Agent Skills), para escribir menos y medir tu consumo.

## Qué hace (y qué no)

- **Junta los planes gratis de muchos proveedores en un solo lugar.** El README dice que reúne 87 proveedores y 1.313 endpoints gratis, y habla de unos 10.100 millones de tokens al mes «de capacidad listada». Son cifras del propio proyecto, sumadas sobre el papel: **no son lo que tú vas a poder usar.** Para usar un proveedor necesitas tu propia cuenta y tu propia clave en ese proveedor.
- **Reparte los pedidos solo.** Tiene un «router» que elige el modelo, cambia al siguiente cuando uno llega a su tope y lleva la cuenta de lo que gastas de cada plan gratis.
- **Habla varios idiomas de API.** Sirve para clientes compatibles con OpenAI, y el README dice que también atiende el formato de Anthropic, así que se puede conectar a Claude Code (ver más abajo).
- **Tus claves se guardan cifradas en tu computadora** (el README dice AES-256-GCM en una base SQLite local) y tus programas solo ven una clave única que empieza con `freellmapi-`.
- **No es un modelo nuevo ni un truco para tener «Claude gratis».** Los modelos que contesten serán los de los proveedores gratis, no los de Anthropic ni de OpenAI de tu plan de pago.

## Costo real

- **El programa es gratis** (MIT). No te cobra por instalarlo ni por cada pedido.
- **Tú pones el entorno.** La instalación de una línea necesita **Docker** (el script también acepta Podman). En Windows hay una app de escritorio en la Microsoft Store, y en Mac un instalador en Releases.
- **Los proveedores gratis son gratis hasta su tope.** Los topes y las condiciones los pone cada proveedor y cambian sin aviso. El README lo dice: los proveedores lanzan y retiran modelos y cambian cuotas sin aviso. No verificamos el tope de cada uno.
- **Hay una versión de pago opcional.** El README ofrece «Premium (live catalog)» a **19 USD al año**: la lista de modelos se actualiza el mismo día. La versión gratis recibe la lista una vez al mes, con unos 30 días de atraso respecto a la de pago. No la necesitas para probarlo.
- **Si algún día lo usas de verdad,** el propio README dice que cambies a una API de pago antes de lanzar.

## Cómo se instala

La vía rápida del README (necesita Docker; prepara una carpeta `~/freellmapi`, genera una clave de cifrado y arranca el contenedor):

```bash
curl -fsSL https://freellmapi.co/install.sh | bash
```

Como todo `curl ... | bash`, ese comando ejecuta lo que descarga. El README enlaza el script para que lo leas antes: [freellmapi.co/install.sh](https://freellmapi.co/install.sh). Si no usas Docker o prefieres la app de escritorio, las otras opciones están en la [guía de instalación](https://github.com/tashfeenahmed/freellmapi/blob/main/docs/en/install/01-install.md).

Cuando termina:

1. Abre **http://localhost:3001** en tu navegador.
2. En la página **Keys**, pega las claves de los proveedores donde ya tengas cuenta gratis.
3. En esa misma página, copia la **clave única** (empieza con `freellmapi-`). Es la que usarás en tus programas.

Por defecto el programa queda disponible **solo en tu computadora**. La documentación avisa que es de un solo usuario y que **no lo expongas a internet**.

## Cómo se usa

Cualquier programa que acepte la dirección de un servicio «compatible con OpenAI» sirve. Apúntalo a `http://localhost:3001/v1` con tu clave única. Ejemplo del README, en Python:

```python
from openai import OpenAI

client = OpenAI(
    base_url="http://localhost:3001/v1",
    api_key="freellmapi-tu-clave-unica",
)

resp = client.chat.completions.create(
    model="auto",
    messages=[{"role": "user", "content": "Resume la caída de Roma en una frase."}],
)
print(resp.choices[0].message.content)
```

Con `model="auto"` el router elige. Cada respuesta trae una cabecera `X-Routed-Via` que dice qué proveedor y qué modelo contestó, para que veas quién te respondió.

**Con Claude Code.** El README trae un comando que lo configura:

```bash
npx freellmapi setup-claude --url http://localhost:3001 --dry-run
```

`--dry-run` solo **muestra** qué cambiaría y no escribe nada. Si el cambio te convence, repítelo sin `--dry-run`: según la documentación, mezcla con tu configuración y guarda antes una copia de respaldo. La alternativa `npx freellmapi launch` abre Claude Code con las credenciales solo en esa sesión y no las deja escritas en disco. Necesitas Node.js 20.18 o más nueva para esos comandos. `npx freellmapi list` muestra los demás agentes que soporta, como Codex, Cline, Aider y OpenCode.

Ojo: con esto Claude Code deja de hablar con Claude y habla con los modelos gratis que el router elija. No esperes la misma calidad. No verificamos si tu versión de Claude Code exige sesión o plan de Anthropic para arrancar.

## Primera prueba sencilla

1. Instálalo y arranca el contenedor.
2. Pega **una sola clave** de un proveedor donde ya tengas cuenta gratis.
3. Corre el ejemplo de Python con una pregunta tuya, **sin datos de clientes**.
4. Mira la cabecera `X-Routed-Via` para ver quién respondió.
5. Después prueba con Claude Code, empezando por `--dry-run`.

## Límites honestos

- **Para experimentar, no para producción.** Es lo que dice el repo. No tiene garantía de servicio: si necesitas que funcione, usa un proveedor de pago con contrato.
- **No metas datos de clientes.** Tu pedido va a un proveedor gratis que tú no eliges pedido por pedido. Para Google lo verificamos: en el plan gratis de la API de Gemini, Google puede usar lo que envías para mejorar sus productos, y revisores humanos pueden leerlo (términos y tabla de precios de Google). De los demás proveedores no verificamos sus reglas.
- **La calidad baja con el uso del día.** La documentación dice que los modelos mejor puestos tienen los topes diarios más bajos; cuando se llenan, el router baja a modelos más pequeños y la «inteligencia» del endpoint cae hacia el final del día, hasta que se reinicia a medianoche UTC.
- **Los modelos más fuertes duran poco.** La documentación dice que los modelos grandes sí aparecen en planes gratis, pero con los topes más chicos y con más riesgo de que los quiten o los pasen a pago.
- **La velocidad es muy dispareja.** Depende de qué proveedor te toque; unos son rapidísimos y otros no.
- **Los planes gratis pueden cambiar sin aviso.** Si pasa, verás errores 429 o de autenticación hasta que llegue la actualización del catálogo.
- **Puede romper los términos de un proveedor.** El repo revisó los términos de cada proveedor en mayo de 2026 (no es consejo legal). Marca a algunos como «precaución» y a **Cohere como «evitar»** para uso personal. Una cuenta por proveedor, sin revender y sin compartir tu endpoint con otras personas. Tú eres responsable de cumplir esos términos.
- **Es de un solo usuario.** No lo compartas con tu equipo ni con clientes.
- **Los números son del proyecto.** Los 10.100 millones de tokens y los 1.313 endpoints son capacidad «listada», no tu capacidad real.

## Créditos

- FreeLLMAPI: [tashfeenahmed/freellmapi](https://github.com/tashfeenahmed/freellmapi), licencia MIT. No es un producto mío ni tengo relación con el proyecto.
- Sitio del proyecto: [freellmapi.co](https://freellmapi.co).

## Fuentes

Consultadas el 28-nov-2026, America/Caracas:

- README (qué es, cifras, instalación, Premium 19 USD/año, aviso «not production», licencia MIT): https://raw.githubusercontent.com/tashfeenahmed/freellmapi/main/README.md
- Estrellas y licencia (API de GitHub): https://api.github.com/repos/tashfeenahmed/freellmapi
- Instalación (Docker, `localhost:3001`, clave única): https://github.com/tashfeenahmed/freellmapi/blob/main/docs/en/install/01-install.md
- Límites y revisión de términos por proveedor: https://github.com/tashfeenahmed/freellmapi/blob/main/docs/en/architecture/00-high-level-index.md
- API y ejemplo de Python: https://github.com/tashfeenahmed/freellmapi/blob/main/docs/en/api/01-rest-api.md
- Claude Code, `setup-claude`, `launch`: https://github.com/tashfeenahmed/freellmapi/blob/main/docs/en/clients/01-agent-clients.md y https://github.com/tashfeenahmed/freellmapi/blob/main/cli/README.md
- Paquete npm `freellmapi` (lista de comandos con `--help`, Node 20.18+): https://www.npmjs.com/package/freellmapi
- Uso de datos en el plan gratis de Gemini: https://ai.google.dev/gemini-api/terms#data-use-unpaid y https://ai.google.dev/gemini-api/docs/pricing

---
Si quieres aprender a hacer reels con IA paso a paso, la comunidad «Contenido en Sistema» en Skool es gratis: https://www.skool.com/primer-empleado-ia-6500

---

## ¿Vienes del video de cuando Claude Code te corta por límite?

Esta es la guía anterior de TOKENS, del 16 de noviembre de 2026, tal como se publicó: Ponytail, ccusage y Agent Skills. Se mantiene aquí completa porque hay gente que la sigue pidiendo. Solo se bajó un nivel a los títulos para que quepan debajo de esta sección; el texto no cambió.

## TOKENS: 3 herramientas gratis para cuando Claude Code te corta por límite

Recurso del video «3 herramientas gratis para cuando Claude Code te corta por límite». Brian Anderson / CashFunnel, 16 de noviembre de 2026.

Tres herramientas **gratis y open source** para cuando Claude Code se te corta a mitad de tarea. **Ninguna te sube el límite** de tu plan. Una hace que el agente escriba menos, otra mide tu consumo y otra ordena el trabajo.

- **Ponytail**, de [DietrichGebert](https://github.com/DietrichGebert): una skill (una instrucción que se le instala al agente) para que escriba solo lo que la tarea necesita. Código: [github.com/DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail) (192.081 estrellas al 16-nov-2026, API de GitHub). Licencia [MIT](https://github.com/DietrichGebert/ponytail/blob/main/LICENSE).
- **ccusage**, de [ryoppippi](https://github.com/ryoppippi): lee los datos de uso que ya están en tu computadora y te arma reportes. Código: [github.com/ccusage/ccusage](https://github.com/ccusage/ccusage) (el atajo [github.com/ryoppippi/ccusage](https://github.com/ryoppippi/ccusage) apunta al mismo repo; 19.453 estrellas al 16-nov-2026). La licencia del programa, en `apps/ccusage/LICENSE`, es [MIT](https://github.com/ccusage/ccusage/blob/main/apps/ccusage/LICENSE) (Copyright 2025 ryoppippi). Docs: [ccusage.com](https://ccusage.com/).
- **Agent Skills**, de [Addy Osmani](https://github.com/addyosmani): un paquete de skills de ingeniería para agentes. Código: [github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) (118.291 estrellas al 16-nov-2026). Licencia [MIT](https://github.com/addyosmani/agent-skills). El README lo confirma: «MIT - use these skills in your projects, teams, and tools.»

**No es LÍMITE** (tres reglas antes de darle dinero a un agente), **ni SKILLS** (Marketing Skills de Corey Haines), **ni SETUP** (ECC). Aquí el tema es instalar y usar estas tres herramientas.

Los datos de esta guía salen de los README, de las licencias y de la guía de bloques de ccusage, consultados el 16-nov-2026. Si una versión nueva cambia un comando o una cifra, mandan el GitHub y el sitio.

### Costo real

- **Las tres herramientas son gratis** (MIT). No te cobran por instalarlas. Ponytail tiene un botón de Sponsor: es una donación, no un precio.
- **Tú pagas Claude Code** (u otro agente donde las corras). En [claude.com/pricing](https://claude.com/pricing) (consultado el 16-nov-2026), **Claude Code no está en el plan Free**. El plan Pro cuesta **20 USD al mes** si pagas mes a mes, o **17 USD al mes** si pagas el año por adelantado (200 USD). Los precios no incluyen impuestos y pueden cambiar: revísalos el día que contrates.
- ccusage también reporta uso de Codex y de otros agentes. No afirmamos el precio de cada uno.

### 1. Ponytail: que escriba solo lo que hace falta

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

### 2. ccusage: mide tu consumo

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

### 3. Agent Skills (Addy Osmani): ordena el trabajo

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

### Ejemplo concreto (dueño de un negocio)

Imagina que estás armando, con Claude Code, la web de reservas de tu consultorio, y se te corta la sesión a mitad del formulario.

1. En la terminal, corre `npx ccusage@latest blocks --active`. Vas a ver cuánto le queda a la ventana de cinco horas. Si está por cerrarse, guarda, cierra el pedido grande y retoma en la siguiente ventana, o parte el trabajo.
2. Instala Ponytail con los dos comandos de plugin. En la próxima sesión, pídele una sola cosa concreta: el formulario de reserva, no «toda la web». La skill apunta a que el agente reutilice lo que ya hay y no arme un calendario de 300 líneas si basta un campo de fecha.
3. Instala Agent Skills y empieza con `/spec` o `/plan`. Define la reserva (quién agenda, qué horarios, qué pasa si alguien cancela) y parte el trabajo en tareas chicas, en vez de un solo hilo eterno que se come la ventana.

Ese ejemplo es nuestro, para que se vea el uso. Ninguno de los tres repos habla de un consultorio, y ninguno te garantiza que dejes de toparte con el límite.

### Límites honestos

- **Ninguna te sube el límite** de Claude Code. Una escribe menos, otra mide tu consumo, otra ordena el trabajo.
- Las cifras de Ponytail (53 % menos código, 45 % menos tokens, y las demás del README) son del autor, con un método y un conjunto de tareas concretos. No son una auditoría externa y no prometen el mismo resultado en tu proyecto.
- ccusage te muestra el uso y el tiempo que le queda al bloque de cinco horas. No te «avisa en vivo» con `blocks --live` (ya no existe en v18). No confundas ese reporte con el cupo de tu plan.
- Agent Skills no es un ahorrador de tokens. El README habla de «progressive disclosure» para que cada skill cargue solo lo necesario; eso no es una promesa de que gastes menos en tu plan.
- «Gratis» se sostiene por la licencia MIT y porque no hay un pago para instalarlas. Claude Code sigue siendo de pago.

### Fuentes

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
