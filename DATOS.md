# DATOS: Reverse API Engineer, saca los datos de una web sin copiarlos a mano

Recurso del video «Reverse API Engineer: saca los datos de una web sin copiarlos a mano». Brian Anderson / CashFunnel, 16 de noviembre de 2026.

**Reverse API Engineer** es una herramienta **gratis y de código abierto** (licencia [MIT](https://github.com/kalil0321/reverse-api-engineer/blob/main/LICENSE)) publicada por [kalil0321](https://github.com/kalil0321). Abres un sitio en un navegador que lanza la herramienta, la usas con normalidad, ella graba el tráfico de red (un archivo HAR) y un modelo de IA te escribe un **cliente de API tipado**: un programa que pide esos datos directo, sin copiarlos de la pantalla.

- Repo: [github.com/kalil0321/reverse-api-engineer](https://github.com/kalil0321/reverse-api-engineer) (unas 3,7 mil estrellas al 16-nov-2026)
- Paquete: [pypi.org/project/reverse-api-engineer](https://pypi.org/project/reverse-api-engineer/) (versión 0.16.0 ese mismo día)
- No lo hizo GitHub ni Anthropic: es de un desarrollador independiente.

**No es APIKIT** (listas de APIs de modelos), **ni CONECTORES**, **ni MCP5**. Aquí el tema es sacar el cliente de un sitio concreto.

Sirve, por ejemplo, para precios, inventario o listados. Eso es un ejemplo de uso nuestro, no una promesa del repo: no funciona en cualquier tienda ni en cualquier sitio.

## Costo real

- **La herramienta es gratis** (MIT, en GitHub y en PyPI).
- **El modelo de IA lo pones tú.** El README pide **Python 3.11+** y, para el **modo agente**, una **API key**. El SDK por defecto es `claude`. En la configuración aparecen también OpenCode, Codex, Cursor, Copilot y Hermes; no afirmamos el precio de cada uno.
- Revisar y correr el código generado es trabajo tuyo (o de alguien técnico). El README lo pide explícitamente: *«review before executing»*.

## Cómo instalarla

Necesitas **Python 3.11 o más nuevo**. Hoy **no hay soporte** para macOS Intel ni para Windows de 32 bits (lo avisa el README, por un cambio de la librería `cryptography`). Usa Linux, macOS con Apple Silicon o Windows de 64 bits.

Modo manual (tú manejas el navegador; es el más fácil de entender la primera vez):

```bash
uv tool install "reverse-api-engineer[manual]"   # o: pip install "reverse-api-engineer[manual]"
playwright install chromium
```

El modo agente es el predeterminado en las docs actuales y no necesita el extra `[manual]`; captura con herramientas de navegador lanzadas por `npx`. Para que tu agente sepa manejar la CLI:

```bash
npx skills add kalil0321/reverse-api-engineer
```

Funciona con Claude Code, Codex, Cursor, OpenCode y otros agentes que soporten skills.

## Primera prueba (modo manual)

```bash
reverse-api-engineer
```

Cambia de modo con **Shift+Tab** hasta `manual`. Pide un objetivo concreto, por ejemplo: “trae los precios de esta lista de productos”. Se abre un navegador (Chromium de Playwright, no tu Chrome de siempre, salvo que uses el proveedor chrome-mcp del modo agente). Navega, filtra, paginas; cuando termines, cierra.

La herramienta deja un cliente en una carpeta tipo `./scripts/nombre_descriptivo/`, con `api_client.py`, `README.md` y `example_usage.py` (si eliges Python, que es la salida por defecto). También puede generar JavaScript, TypeScript, Go, Java, C#, PHP, Ruby, C o PowerShell.

**Antes de correr el código, léelo.** Mira a qué dominio llama, qué credenciales usa y qué hace con los datos. Luego ejecuta el ejemplo en un entorno de prueba.

Si ya capturaste el tráfico y solo quieres regenerar el cliente, usa el modo `engineer`.

## El modo agente

En `agent`, la IA navega sola. PyPI lo presenta como el modo por defecto. Sirve cuando el flujo es repetible; no lo uses el día 1 si todavía estás entendiendo la herramienta, y no lo apuntes a una cuenta o un pago sin supervisión.

## Tres avisos (léelos antes de usarla)

1. **Úsala solo donde tengas permiso.** Sacar datos de un sitio ajeno puede violar sus términos. El repo no trae un aviso legal; este criterio es nuestro (y el sentido común).
2. **Los sitios con anti-bots fuertes pueden bloquearla** o pedirte pasos manuales. Lo dice el README. Esta herramienta no “se salta” protecciones.
3. **El resultado es código, no una hoja mágica.** Si no programas, pídele a tu agente (Claude Code u otro) que te explique el cliente y que lo corra contigo, o pásaselo a alguien técnico. No lo ejecutes a ciegas.

## Fuentes

Consultadas el 16-nov-2026, America/Caracas:

- Repo, licencia MIT, modos, instalación, lenguajes, avisos y estrellas: https://github.com/kalil0321/reverse-api-engineer
- README: https://raw.githubusercontent.com/kalil0321/reverse-api-engineer/main/README.md
- PyPI 0.16.0, “The agent that turns websites into APIs.”: https://pypi.org/project/reverse-api-engineer/

---
¿Quieres que revisemos juntos un primer cliente, en un sitio donde sí tengas permiso? Escríbeme por DM **@briananderson.ai**.
