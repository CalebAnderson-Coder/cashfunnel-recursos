# OPENREPLY: alternativa open source a ManyChat (comentario a DM en Instagram)

Recurso del video sobre OpenReply. Brian Anderson / CashFunnel, noviembre de 2026.

**OpenReply** es software **open source (MIT)** que tú instalas. Alguien comenta una palabra clave en un post o reel y recibe tu link por DM, usando la **API oficial de Instagram** (Meta). No es una app a la que te suscribes, no scrapea Instagram y no te pide la contraseña de la cuenta.

- Repo oficial (licencia MIT, ~3.182 estrellas al 9-nov-2026): https://github.com/diwenne/openreply
- Autor: [diwenne](https://github.com/diwenne). Este software no es mío; aquí te dejo el repo y una guía de instalación con límites claros.
- Documentación de setup: https://github.com/diwenne/openreply/blob/main/docs/setup.md
- Stack y costos de referencia: https://github.com/diwenne/openreply/blob/main/docs/stack.md
- Demo del dashboard (no es un hosting al que te suscribes): https://openreply.diwen.dev

## Qué hace (y qué no)
- Defines una palabra clave en un post o reel. Quien comenta esa palabra recibe un DM con tu link, por la API oficial.
- Puedes conectar varias cuentas de Instagram Business o Creator en un solo panel.
- El software no te cobra por contacto ni tiene plan de asientos. **Hosting, base de datos, Redis y la conexión a Instagram sí pueden tener costo.**
- No reemplaza todo ManyChat (broadcasts, muchos flujos de marketing, etc.). Cubre lo esencial del comment-to-DM y, según el repo, también inbox, triggers de Stories o DMs y links con seguimiento, si los activas.

## Requisitos
- Una cuenta **Instagram Business o Creator** vinculada a una Página de Facebook. Las cuentas personales no sirven.
- Un despliegue **self-hosted** con todo esto a la vez:
  1. La app web
  2. Un **worker siempre encendido** (no basta con un hosting que se duerme)
  3. **PostgreSQL**
  4. **Redis** (el video menciona base de datos, worker y URL pública; Redis también es obligatorio)
  5. Una **URL pública HTTPS** para el webhook de Meta
  6. Email transaccional para magic links (Resend o SMTP)
- Conexión a Instagram: tu **propia app de Meta**, o un proveedor opcional de pago documentado en el repo (por ejemplo Zernio). La App Review de Meta solo hace falta si otras personas van a conectar *sus* cuentas a *tu* app.

## Instalación (resumen)
Lee `docs/setup.md` del repo antes de instalar. El documento incluye un prompt para pegarlo en Claude Code o Cursor y que te guíe.

1. Clona https://github.com/diwenne/openreply y configura las variables de entorno (`.env`).
2. Prepara PostgreSQL, Redis, el worker siempre encendido y una URL HTTPS pública.
3. Configura el email (Resend o SMTP) para los magic links de acceso.
4. Elige la conexión: app de Meta propia o el proveedor documentado.
5. Conecta una cuenta Instagram Business/Creator, crea una campaña con una palabra clave y pruébala **desde otra cuenta**.

El propio repo describe un stack de referencia en planes gratis (Vercel Hobby + Neon + Redis Cloud 30 MB + una VM siempre encendida, por ejemplo Oracle Always Free + Resend). También documenta un camino más simple de pago (por ejemplo Vercel + Railway). El worker no puede vivir solo en un hosting que se apaga (una app de Vercel sin un worker aparte no alcanza).

## Límites honestos
- El repo se publicó en julio de 2026; es un proyecto joven y en evolución, no un producto con soporte comercial.
- Siguen aplicando los límites de Instagram: ventana de mensajería de 24 horas, y el orden de **~750 private replies por hora** que documenta el setup.
- Si ya usas ManyChat, Zernio u otra herramienta que controle los DMs, tienes que ceder el **control de la conversación** a OpenReply en Meta Business Suite. Si no, los botones del DM pueden fallar con un error de “not the thread owner”. No conectes las dos herramientas a la misma cuenta sin un plan para esto.
- Los planes “gratis” de hosting pueden alcanzar para probar o para poco volumen. Un worker 24/7 y más tráfico suelen costar unos dólares al mes. El software en sí no cobra.
- No es un ManyChat completo. Si necesitas toda su automatización de marketing, esto no lo sustituye entero.

## Costo
- Software y repo: gratis (MIT).
- Infra: variable. El `docs/stack.md` del repo muestra un camino en tiers gratis y otro de pago más simple.
- App de Meta: la API no cobra por estos envíos; un proveedor de conexión opcional (si lo usas) sí tiene su propio precio.

Fuente: README, `docs/setup.md` y `docs/stack.md` del repo oficial (revisado el 9-nov-2026).
