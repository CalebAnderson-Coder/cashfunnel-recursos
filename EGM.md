# EGM: plugin de Google que revisa el plan antes del código

Recurso del video sobre Elephant Goldfish Model (EGM). Brian Anderson / CashFunnel, noviembre de 2026.

**Elephant Goldfish Model** es un plugin open source para diseñar y revisar software con agentes. El Elefante conoce tu proyecto y escribe el plan. Los Goldfish lo revisan sin ese contexto. Tú apruebas. Recién ahí se implementa. No escribe el código por ti ni “elimina bugs solo”: revisa el **plan** antes de una sola línea.

Esto no es un producto mío ni un producto de Google Cloud con soporte o SLA. El propio repositorio aclara: *“This is not an officially supported Google product.”*

## Enlaces oficiales

- Repo: https://github.com/google/elephant-goldfish-model
- Sitio: https://egm.dev
- Anuncio (22 de octubre de 2026): https://opensource.googleblog.com/2026/10/introducing-elephant-goldfish-model-plugin.html
- Integración con Claude Code: https://github.com/google/elephant-goldfish-model/blob/main/docs/claude.md
- Flujo de trabajo: https://github.com/google/elephant-goldfish-model/blob/main/docs/getting_started.md
- Otros entornos (Antigravity, Codex, Cowork, etc.): https://github.com/google/elephant-goldfish-model/blob/main/docs/harnesses.md

Licencia **Apache 2.0**. En el blog oficial, Google dice que el plugin se desarrolló internamente para sus ingenieros, que ahora es open source, y que *“Thousands of Googlers use this plugin every day to ship production Google code.”* No hay un número exacto publicado, ni afirma que lo use “todo Google”.

## Qué hace (y qué no)

Según el README y el blog oficiales:

1. **Elefante** (`/egm:egm-brainstorm` y `/egm:egm-draft`): una sesión con el contexto del proyecto. Diseña, discute y redacta un documento de plan. En esta fase no se escribe el código.
2. **Goldfish** (`/egm:egm-review`): sesiones **sin** el chat anterior. Resumen el plan, lo critican y hacen una comprobación de si está listo para implementar. Si no pueden explicar el plan, el documento está ambiguo.
3. **Tú** resuelves los intercambios, apruebas el diseño y decides qué se construye. Recién ahí le pides a tu agente que implemente.

También hay otras skills oficiales (`egm-resolve`, `egm-bootstrap`, `egm-drift-report`, `egm-review-loop`) si las necesitas; no hace falta seguir la secuencia completa. El README lo deja explícito.

Lo que **no** hace:

- No sustituye tests ni tu criterio. El README lo dice: una revisión no reemplaza las pruebas ni el juicio humano.
- No garantiza código perfecto ni un ahorro fijo de horas o tokens. El video lo menciona en cualitativo (“eso te ahorra horas y tokens”); las fuentes oficiales no publican una cifra. Aquí no inventamos una.
- No es un plugin que hayamos comprobado en el Claude gratis de la web. Esta guía se centra en **Claude Code**, que es lo que documenta el proyecto para esa audiencia.

## Requisitos (Claude Code)

- **Claude Code 2.1.271 o posterior.** La guía oficial (`docs/claude.md`) lo pide para el aislamiento real de los Goldfish (`omitClaudeMd`). Las versiones más viejas **no** deben presentarse como entorno verificado.
- Claude Code es un producto de pago de Anthropic (usas tu plan). El plugin EGM es gratis; los tokens o el plan del agente los pones tú.
- Los Goldfish necesitan subagentes con contexto fresco. Si tu agente no puede crearlos, EGM detiene la revisión. Está documentado en el README.

## Instalación en Claude Code

Comandos oficiales del README y de `docs/claude.md` (verificados el 14-nov-2026, America/Caracas):

```sh
claude plugin marketplace add google/elephant-goldfish-model
claude plugin install egm@egm
```

Luego, según `docs/claude.md`, activa el plugin e inicia una **sesión nueva**:

```sh
claude plugin enable egm@egm
```

En esa sesión nueva:

```text
/egm:egm-brainstorm
/egm:egm-draft
/egm:egm-review
```

Ejemplo oficial del README (añadir un envío de webhooks a un proyecto):

```text
/egm:egm-brainstorm Add webhook delivery to this project.
/egm:egm-draft
/egm:egm-review design_draft.md
```

Usa la ruta del borrador que te devuelva el agente. El README indica que el brief queda en `concepts_brief.md`, el borrador en `design_draft.md`, y que las especificaciones aprobadas se guardan bajo `docs/designs/`. Elige un hallazgo de la revisión, corrígelo o ignóralo con criterio, y **tú** apruebas antes de implementar.

Instala el plugin completo. El proyecto avisa que copiar solo la carpeta `skills/` no basta: las skills necesitan leer los prompts de los revisores y los estándares del documento.

## Otros entornos

El mismo repo documenta instalación para Antigravity, Codex CLI, Claude Cowork, ChatGPT desktop y otros. Por ejemplo:

```sh
# Antigravity CLI
agy plugin install https://github.com/google/elephant-goldfish-model

# Codex CLI
codex plugin marketplace add google/elephant-goldfish-model
codex plugin add egm@egm
```

En Codex, las skills se eligen desde el selector; no uses a ciegas el prefijo `/egm:` de Claude Code. El estado de cada entorno (qué está verificado y qué no) está en `docs/harnesses.md`. Esta guía no afirma haber probado todos.

## Límites honestos

- Es open source de un equipo de Google, no un producto oficial de Google Cloud con contrato de soporte.
- Revisa el plan; no “para los bugs en runtime”.
- El humano se queda en el loop: eso es el punto, no un defecto.
- Empieza en un repo de prueba, sin secretos ni datos de clientes.
- No pegues claves de API en el chat ni en el repositorio.

## Fuentes

- Repo y README: https://github.com/google/elephant-goldfish-model (HTTP 200 el 14-nov-2026, America/Caracas)
- Blog de Google Open Source, 22-oct-2026: https://opensource.googleblog.com/2026/10/introducing-elephant-goldfish-model-plugin.html
- `docs/claude.md`, `docs/getting_started.md` y `docs/harnesses.md` del mismo repo
- Licencia: Apache 2.0
- Sitio: https://egm.dev (HTTP 200 el 14-nov-2026)

Guía educativa de Brian Anderson. No es un producto oficial de Google ni una promesa de menos bugs, menos tokens o más velocidad.
