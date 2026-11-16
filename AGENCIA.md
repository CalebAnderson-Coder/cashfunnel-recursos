# AGENCIA: una agencia de IA gratis dentro de Claude Code

Recurso del video «Una agencia de IA completa, gratis en GitHub». Brian Anderson / CashFunnel, 16 de noviembre de 2026.

**The Agency** (`agency-agents`) es un repositorio **gratis y open source** (licencia [MIT](https://github.com/msitarzewski/agency-agents/blob/main/LICENSE)) con cientos de agentes especialistas listos para usar: SEO, anuncios, contenido, ventas, desarrollo web, QA y más. Cada agente es un archivo `.md` con su identidad, su personalidad, su método de trabajo y lo que entrega.

- Código: [github.com/msitarzewski/agency-agents](https://github.com/msitarzewski/agency-agents) (unas 169 mil estrellas al 16-nov-2026)
- App de escritorio para instalarlos: [agencyagents.app](https://agencyagents.app) · [descargas (releases)](https://github.com/msitarzewski/agency-agents-app/releases/latest) · [código de la app](https://github.com/msitarzewski/agency-agents-app) (también MIT)

Los datos de esta guía salen del README del repo, de `scripts/install.sh`, de la guía de [integración con Claude Code](https://github.com/msitarzewski/agency-agents/blob/main/integrations/claude-code/README.md) y del sitio de la app, consultados el 16-nov-2026. Si algo cambia en una versión nueva, mandan el sitio y el GitHub.

## Cuántos agentes trae

El video dice «más de 200». El README habla de «230+». Al 16-nov-2026, el instalador oficial (`./scripts/install.sh --list teams`) cuenta **283 agentes en 18 divisiones**: ingeniería (66), especializados (59), marketing (37), desarrollo de videojuegos (21), GIS (13), seguridad (12), diseño (10), ventas (9), testing (9), paid media (7), gestión de proyectos (7) y otras. El número sube con cada versión.

## Costo

- **El repo y la app son gratis** (MIT). La app no pide cuenta y, según su sitio, no tiene telemetría.
- **Tú pagas la herramienta de IA donde los usas.** Para Claude Code necesitas un plan de pago de Claude (Pro o superior) o la API de Anthropic. Los agentes son instrucciones: no traen modelo propio.

## Cómo instalarlos en Claude Code

### Opción 1: la app (sin terminal)

1. Descarga la app desde [agencyagents.app](https://agencyagents.app) o desde las [releases](https://github.com/msitarzewski/agency-agents-app/releases/latest) (al 16-nov-2026, versión 0.3.2):
   - **Mac (M1 o superior):** el `.dmg` `aarch64`. **Mac Intel:** el `.dmg` `x64`. Ambos firmados y notarizados, macOS 13 o superior. También: `brew install --cask msitarzewski/agency-agents/agency-agents`.
   - **Windows:** el instalador `x64-setup.exe` (o `arm64-setup.exe`). Hoy **no está firmado**: Windows muestra «Windows protegió tu PC». Haz clic en **Más información → Ejecutar de todas formas**. Descárgalo solo desde los links oficiales de arriba.
   - **Linux:** `.deb`, `.rpm` o `.AppImage`.
2. Ten Claude Code instalado. La app detecta tus herramientas en el panel **Tools**.
3. En **Agents**, filtra por división, abre un agente y lee su persona antes de instalarlo.
4. Instala uno, varios o un equipo completo (panel **Teams**) en **Claude Code**. Puedes instalarlos para todos tus proyectos o solo para uno (**Projects**).
5. Abre Claude Code y escribe `/agents` para ver los que quedaron instalados.

La app lleva un registro local de lo que instaló, avisa si un archivo cambió y te deja actualizar o desinstalar. Antes de sobrescribir algo, guarda una copia.

### Opción 2: por terminal

Necesitas `git` y bash (en Windows, Git Bash o WSL).

```bash
git clone https://github.com/msitarzewski/agency-agents.git
cd agency-agents

# Todos los agentes a Claude Code (~/.claude/agents/)
./scripts/install.sh --tool claude-code

# O solo las divisiones que te sirven
./scripts/install.sh --tool claude-code --division marketing,paid-media,sales
```

**Consejo:** no instales los 283 si no los vas a usar. Empieza con marketing, paid-media y sales.

## Cómo se usan

En una sesión de Claude Code, nombra al agente en tu pedido. Por ejemplo: *«Usa el agente SEO Specialist para…»*. Claude Code delega la tarea a ese especialista, con su método y su forma de entregar.

## 5 especialistas para probar hoy (con prompt listo)

Copia el prompt, cambia lo que va entre corchetes y pégalo en Claude Code.

**1. SEO Specialist** (`marketing/marketing-seo-specialist.md`): SEO técnico, contenido y autoridad.
> Usa el agente SEO Specialist. Audita el SEO técnico de [URL de mi web]: títulos, meta descripciones, encabezados, velocidad, indexación y enlaces internos. Dame las 10 correcciones con más impacto, ordenadas de mayor a menor, y explica cada una en una línea.

**2. Ad Creative Strategist** (`paid-media/paid-media-creative-strategist.md`): textos de anuncios para Meta y Google y pruebas creativas.
> Usa el agente Ad Creative Strategist. Vendo [producto o servicio] a [cliente ideal] en [ciudad o país]. Escríbeme 5 anuncios para Meta (texto principal, título y descripción) y un anuncio de búsqueda de Google con 10 títulos y 4 descripciones. Propón qué probar primero.

**3. Offer & Lead Gen Strategist** (`sales/sales-offer-lead-gen-strategist.md`): ofertas e imanes de leads.
> Usa el agente Offer & Lead Gen Strategist. Mi negocio es [qué vendes], a [precio], para [a quién]. Dame 3 imanes de leads que atraigan a compradores de verdad (no curiosos) y una oferta de entrada para cada uno, con el título y la promesa en una frase.

**4. Content Creator** (`marketing/marketing-content-creator.md`): calendario editorial y textos para redes.
> Usa el agente Content Creator. Ármame un calendario de 2 semanas para Instagram y TikTok de [mi negocio]: 3 pilares de contenido, 10 ideas de reels con el gancho de los primeros 3 segundos y el texto de cada publicación.

**5. Frontend Developer** (`engineering/engineering-frontend-developer.md`): construir o mejorar la web.
> Usa el agente Frontend Developer. Créame una landing de una sola página para [mi oferta], con titular, beneficios, testimonios de ejemplo marcados como «[REEMPLAZAR]», preguntas frecuentes y un botón de WhatsApp. Que cargue rápido en el celular.

## Límites honestos

- **Son instrucciones, no empleados.** Cada agente es un prompt muy bien armado. La calidad depende del modelo y del contexto que le des. Revisa todo antes de publicarlo o mandárselo a un cliente.
- **Más agentes no es mejor.** Cada agente instalado es un archivo más que Claude Code tiene que considerar. Instala solo los que vas a usar.
- **Windows sin firma.** El aviso de SmartScreen es esperado; instala la app solo desde los links oficiales.
- **La app no ejecuta agentes.** Solo los instala en tus herramientas (Claude Code, Codex, Cursor, Gemini CLI y otras). El trabajo lo hace tu herramienta de IA.
- **No los conectes a tus cuentas sin revisar.** Un agente que puede publicar, gastar o escribirle a clientes necesita tus reglas primero (mira [PERMISOS](PERMISOS.md)).

## Créditos

- The Agency (`agency-agents`): [Michael Sitarzewski](https://github.com/msitarzewski) y contribuidores, licencia MIT.
- App Agency Agents: [msitarzewski/agency-agents-app](https://github.com/msitarzewski/agency-agents-app), licencia MIT.
- No es un producto mío ni tengo relación con el proyecto.

---
¿Quieres que lo configuremos para tu negocio? Escríbeme por DM **@briananderson.ai**.
