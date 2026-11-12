# APIKIT — Awesome Free LLM APIs: capas gratis de APIs de IA

Palabra: **APIKIT**
Alias: API-KIT, API KIT

> Un directorio público de capas gratis de APIs de LLM, con límites, ventana de contexto y fragmentos de configuración. No es una API nuestra ni un cupón ilimitado.

**Repo (verificado HTTP 200 el 12-nov-2026, America/Caracas):** [github.com/open-free-llm-api/awesome-freellm-apis](https://github.com/open-free-llm-api/awesome-freellm-apis)  
**Directorio vivo:** [freellm.net](https://freellm.net)  
**Configs de un clic (Claude Code, Cursor, Codex y otros):** [freellm.net/config/](https://freellm.net/config/)  
**Licencia del repo:** MIT, © open-free-llm-api. No es un producto mío.

Cifra del README el 12-nov-2026: **542+ APIs de 31 proveedores**. El propio README dice que los datos se refrescan a diario («Last updated: 2026-11-12»). En el video se dice «más de 540 / 31»; usa siempre la cifra vigente del README o de freellm.net el día que lo abras.

## Qué es (y qué no es)

Es un directorio estructurado de **capas gratis** de APIs de LLM (Gemini, Groq, NVIDIA, DeepSeek, Mistral y más), con transparencia sobre si piden tarjeta, teléfono o solo un registro, y con snippets para pegar en tu agente o editor.

No es «gratis para siempre, sin condiciones». Cada proveedor tiene su propio límite, sus requisitos de alta y sus términos. El repo lo dice con claridad: las cuotas cambian y hay proveedores que «gradúan» el plan. Léelo antes de usarlo en un negocio.

Tampoco sustituye a ciegas un plan de pago cuando hace falta calidad, una cuota estable o un acuerdo comercial. Es una opción para tareas que aguantan una capa gratis, y un complemento.

## Cómo empezar (lo que recomienda el propio README)

El README sugiere empezar por **Groq**: correo, sin tarjeta, 30 RPM y 14.400 RPD en el ejemplo de la capa gratis (cifras del README del 12-nov-2026).

1. Entra a [console.groq.com/keys](https://console.groq.com/keys), regístrate con un correo (sin tarjeta, según el README) y copia la clave.
2. Elige el proveedor y el modelo en el [directorio del repo](https://github.com/open-free-llm-api/awesome-freellm-apis) o en [freellm.net](https://freellm.net).
3. Pega la configuración en tu herramienta. Lo más simple es usar el generador: [freellm.net/config/](https://freellm.net/config/) (hay anclas para Claude Code, Cursor, Codex, OpenCode y otros).

El README también incluye ejemplos de Python (SDK de OpenAI apuntando a Groq), Cursor (Settings → Models → Add Model) y Codex (`OPENAI_BASE_URL` + `OPENAI_API_KEY`). Para **Claude Code**, el ejemplo del README del 12-nov-2026 usa OpenRouter (`ANTHROPIC_BASE_URL` + `ANTHROPIC_AUTH_TOKEN`) y advierte que los modelos Anthropic en OpenRouter piden un *top-up* de 10 USD (una vez). No lo presentes como un camino 100 % gratis sin leer esa nota.

## Límites y requisitos (lo que sí está en el README hoy)

Revisado el 12-nov-2026 en el README. Confirma la fila del proveedor el día que lo uses; esas celdas se actualizan.

- **No todas te piden lo mismo para registrarte.** En la tabla «Permanent Free Tiers»:
  - Sin tarjeta, según la columna *Credit Card?*: por ejemplo Groq, Google Gemini, Mistral AI, Cohere, Cloudflare Workers AI, Kilo Code, LLM7.io, Hugging Face, Z AI (Zhipu AI) y Cerebras aparecen como «No».
  - **NVIDIA NIM** aparece como «Phone verification» (verificación por teléfono), no como «No».
  - Varios aparecen como «Registration» (hay que registrarse; el README no detalla en esa celda si piden tarjeta).
- **OpenRouter** no está en esa tabla de capas permanentes: está en «Renewable Credits», con «Free tier + $10 topup → 1K RPD».
- Cada modelo trae su propia ventana de contexto y su rate limit (por ejemplo, el snippet de Groq cita 30 RPM y 14.400 RPD). No copies un límite de un proveedor a otro.
- El criterio de inclusión del repo es que el proveedor ofrezca una **capa gratis** (no solo un crédito de prueba); si hay créditos de prueba, deben estar rotulados.

Antes de usarlo en un negocio: lee la fila del proveedor, los términos de uso (incluida la privacidad y si el uso comercial está permitido) y prueba primero con una clave en un proyecto sin datos de clientes.

## Checklist de primera prueba

- [ ] Abrir el [repo](https://github.com/open-free-llm-api/awesome-freellm-apis) o [freellm.net](https://freellm.net) y anotar la cifra y la fecha del día.
- [ ] Elegir un proveedor (el README sugiere Groq para empezar) y crear la clave en su consola oficial.
- [ ] Leer la fila: tarjeta / teléfono / registro, rate limit y términos.
- [ ] Pegar el snippet desde [freellm.net/config/](https://freellm.net/config/) en Claude Code, Cursor o Codex.
- [ ] Hacer una llamada de prueba corta, sin datos sensibles, y comprobar que responde dentro del límite.

## Fuentes

- Repo: [github.com/open-free-llm-api/awesome-freellm-apis](https://github.com/open-free-llm-api/awesome-freellm-apis) (README, 12-nov-2026)
- Sitio y configs: [freellm.net](https://freellm.net), [freellm.net/config/](https://freellm.net/config/)
- Clave de Groq (punto de partida del README): [console.groq.com/keys](https://console.groq.com/keys)
- Licencia: MIT

Guía educativa de Brian Anderson. No es un producto de open-free-llm-api ni una promesa de que una capa gratis vaya a mantenerse igual.
