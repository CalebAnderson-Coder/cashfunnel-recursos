# MAPA: más de 230 agentes de IA gratis, ordenados por área de tu empresa

Recurso del video sobre Agency Agents. Brian Anderson / CashFunnel, noviembre de 2026.

**Agency Agents** (`msitarzewski/agency-agents`) es un proyecto **gratis y open source (licencia MIT)** con cientos de agentes de IA listos para usar: cada uno es un archivo de texto con su misión, su forma de trabajar y lo que entrega. Vienen ordenados por área (ventas, marketing, soporte, finanzas, ingeniería, diseño y más) y se instalan en Claude Code, Codex, Cursor y otras herramientas.

La palabra clave del video es **MAPA**.

## Enlaces oficiales

- **Repo:** https://github.com/msitarzewski/agency-agents (licencia MIT; unas **170.000 estrellas** el 24-nov-2026)
- **App de escritorio (opcional):** https://agencyagents.app · descargas en https://github.com/msitarzewski/agency-agents-app/releases/latest
- Este proyecto no es mío: te dejo el repo oficial y un mapa para empezar. Instálalo solo desde ahí.

## El mapa por área (ejemplos del README)

| Área | Agente | Para qué sirve |
|---|---|---|
| Ventas | Outbound Strategist | Prospección con señales y secuencias multicanal |
| Ventas | Discovery Coach / Deal Strategist | Calificar oportunidades y planear cómo ganarlas |
| Ventas | Proposal Strategist | Escribir propuestas que convencen |
| Marketing | (división Marketing) | Contenido, calendario, SEO, redes y visibilidad en buscadores de IA |
| Soporte | Support Responder | Responder a clientes y resolver casos |
| Soporte | Executive Summary Generator | Resúmenes ejecutivos para quien decide |
| Finanzas | Bookkeeper & Controller | Libros, conciliaciones y cierre de mes |
| Finanzas | FP&A Analyst / Financial Analyst | Presupuesto, proyecciones y análisis |

Hay más divisiones: ingeniería, diseño, producto, gestión de proyectos, pruebas, seguridad, medios pagados, desarrollo de juegos, investigación y otras. La lista completa, con un enlace a cada archivo, está en el README.

## Qué trae cada agente

Según el README, cada archivo trae:

- identidad y personalidad,
- misión y flujo de trabajo (su proceso paso a paso),
- entregables concretos, con ejemplos,
- métricas de éxito y estilo de comunicación.

## Cómo instalarlos (3 caminos)

### A. La app (sin terminal)

Descarga **Agency Agents** para macOS, Linux o Windows desde el enlace de arriba. Te deja ver todos los agentes e instalarlos en Claude Code, Cursor, Codex, Gemini CLI y otras herramientas con un clic, y los mantiene actualizados.

### B. En Claude Code, con un comando

```sh
git clone https://github.com/msitarzewski/agency-agents.git
cd agency-agents
./scripts/install.sh --tool claude-code
```

¿Solo quieres un área? Por ejemplo:

```sh
./scripts/install.sh --tool claude-code --division sales
./scripts/install.sh --list teams   # ver equipos y cuántos agentes trae cada uno
```

Luego, en Claude Code, llámalo por su nombre: «Activa el modo Proposal Strategist y ayúdame con esta propuesta».

### C. En Codex, Cursor y otras herramientas

```sh
./scripts/convert.sh               # genera los archivos para cada herramienta
./scripts/install.sh --tool codex  # o: --tool cursor, --tool gemini-cli, --tool windsurf…
```

`./scripts/install.sh` sin opciones abre un asistente que detecta lo que tienes instalado.

## Límites honestos

- **Son instrucciones, no conexiones.** Un agente no se conecta solo a tu correo, tu CRM ni tu contabilidad: esas conexiones las haces tú (con los conectores de tu herramienta) y decides qué permisos le das.
- **Revisa lo que sale.** Propuestas, respuestas a clientes y números de finanzas los revisa una persona antes de enviarlos o usarlos.
- **No les des acceso a todo.** Empieza con un área y pocos permisos; amplía cuando veas que funciona.
- **Gasta de tu plan.** Los agentes son gratis, pero corren sobre tu Claude, Codex o Cursor, y eso gasta de tu plan de siempre.

## Costo

- Agentes, scripts y app: **gratis** (MIT).
- El uso de tu herramienta de IA: lo de tu plan de siempre.

## Fuentes

- README del repo (secciones «Quick Start», «The Agency Roster» y «Use as Reference»), consultado el 24-nov-2026.
- Datos del repo en la API de GitHub (licencia MIT, estrellas), consultados el 24-nov-2026.
