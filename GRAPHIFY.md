# GRAPHIFY: un mapa local de tu código para el agente

Fuentes oficiales y del autor verificadas el 10-nov-2026, America/Caracas. Guía educativa; no es un benchmark propio ni un producto de Graphify Labs.

## Qué es y qué no es

Graphify open source arma un **mapa de tu código** (clases, funciones, imports y otras relaciones) y lo guarda en tu computadora. En la siguiente sesión, el agente puede consultar ese grafo en vez de volver a leerse el repositorio entero.

- Repo oficial: [Graphify-Labs/graphify](https://github.com/Graphify-Labs/graphify) (rama documentada `v8`). Licencia **Apache 2.0**.
- El mapa de **código** se construye en local con tree-sitter (AST). No sale de tu máquina. Documentos, PDF, imágenes o video pueden usar el modelo de tu asistente o una API configurada para un pase semántico; eso no es lo mismo que “todo queda offline”.
- **Graphify Cloud** es otro producto, de pago (hay una prueba de 14 días en [app.graphify.com](https://app.graphify.com/login)). No es lo que comparte este recurso. Las cifras promocionales de Cloud (por ejemplo “80% fewer tokens” en el README) no son una medición nuestra ni una promesa de facturación.

## Cómo se instala hoy

El paquete oficial en PyPI se llama `graphifyy` (con doble y). El comando que queda instalado es `graphify`. Otros paquetes `graphify*` en PyPI no son el de Graphify Labs. Hace falta Python 3.10 o posterior. La vía recomendada en el README de `v8` y en [docs.graphify.com/open-source/installation](https://docs.graphify.com/open-source/installation) es `uv` (o `pipx`):

```bash
uv tool install graphifyy
graphify install
```

Si después no encuentras el comando, `uv tool update-shell` y abre una terminal nueva. `pipx install graphifyy` es la alternativa oficial. `pip install graphifyy` existe, pero puede exigir ajustes de PATH; no lo uses como único paso.

`graphify install` detecta tu asistente y registra la skill. En el asistente, en la carpeta del proyecto:

```text
/graphify .
```

Eso construye el grafo del directorio actual (por lo general `graphify-out/` con `graph.html`, `GRAPH_REPORT.md` y `graph.json`). Para otro asistente, pasa `--platform`, por ejemplo `graphify install --platform codex`. Documentación: [docs.graphify.com](https://docs.graphify.com) y [quickstart](https://docs.graphify.com/open-source/quickstart).

## Cómo leer los números de tokens

El **49×** que se menciona en el video no es una garantía para todos los repositorios. Viene de un test del autor (Tirth Kanani, Medium, marzo 2026) al agregar un rate limiter en el monorepo de Next.js (del orden de 27 732 archivos). No es un benchmark ejecutado aquí.

La documentación oficial del `graphify benchmark` ([token-benchmark](https://docs.graphify.com/open-source/features/token-benchmark)) compara tokens de leer el corpus entero frente a consultar el grafo: es una **guía de escala**, no una cifra de facturación. En un repo chico el ahorro casi no se nota; un corpus pequeño cabe en la ventana de contexto de todos modos.

No uses como promesa las cifras que aparecen en shorts ajenos y no están sostenidas igual en las docs actuales — en particular **71.5×** (u “71.5x with Obsidian”) y la idea de que un plan de **20 USD rinde como uno de 200 USD**. Este recurso no las afirma.

## Antes de usarlo en un proyecto real

- Trabaja primero en un repo de prueba, sin secretos ni datos de clientes.
- Revisa la licencia Apache 2.0 y conserva avisos si redistribuyes código. Marcas y logos no quedan licenciados automáticamente por eso.
- Confirma en las docs vigentes el método de instalación (el paquete es `graphifyy`) y qué parte del corpus se queda local frente a la que puede ir a un modelo.
- Si mides tokens, anota el repo, el tamaño, la tarea concreta y si el número salió de `graphify benchmark` o de una factura real. No tomes el benchmark como costo de API.

## Fuentes

- Código e instalación: [github.com/Graphify-Labs/graphify](https://github.com/Graphify-Labs/graphify) (README de la rama `v8`, 10-nov-2026)
- Docs: [docs.graphify.com](https://docs.graphify.com), [instalación](https://docs.graphify.com/open-source/installation), [token-benchmark](https://docs.graphify.com/open-source/features/token-benchmark)
- Licencia del proyecto OSS: Apache 2.0

Guía educativa de Brian Anderson. No es una garantía de ahorro de tokens ni un producto oficial de Graphify Labs.
