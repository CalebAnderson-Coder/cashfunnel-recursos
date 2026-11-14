# FLINT: un modelo open source para programar en tu máquina

Recurso del video sobre Recursive Flint. Brian Anderson / CashFunnel, noviembre de 2026.

**Flint** es un modelo de lenguaje open source de Recursive, hecho para agentes de código. Corre **en tu máquina**, sin mandar tus datos a una API. La idea del video: deja las tareas chicas y del día a día (un rename, un arreglo puntual, un archivo suelto) en Flint, y guarda Claude para lo difícil, así no gastas el cupo de tu plan.

Matiz honesto: Flint **no reemplaza** a Claude en tareas complejas. Recursive mismo dice que puede necesitar más guía que los modelos cerrados grandes y recomienda partir las tareas complejas en subtareas con instrucciones explícitas.

## Enlaces oficiales

- **Modelo en Hugging Face:** https://huggingface.co/RecursiveSI/flint
- **Anuncio oficial:** https://www.recursive.com/updates/introducing-recursive-flint
- **Motor local `rec` (para Mac):** https://github.com/recursive-oss/rec
- **Documentación:** https://docs.recursive.com/getting-started

## El plan de pago que te ahorras (Claude Pro)

En https://claude.com/pricing, consultada el **14-nov-2026** (America/Caracas): Claude Pro cuesta **US$20 al mes con facturación mensual** (US$17 al mes si pagas el año por adelantado). Según el centro de ayuda de Claude, Claude y Claude Code comparten el mismo cupo de uso del plan, con límites que se reinician (https://support.claude.com/en/articles/11145838). Flint es gratis (licencia **Apache 2.0**); lo que pagas es tu equipo y la electricidad.

## Qué es Flint (datos oficiales)

- Mixture-of-experts: **39,8 mil millones de parámetros en total**, unos **2,5 mil millones activos** por token.
- Pensado para investigar código, arreglar bugs, implementar funciones y escribir tests. Soporta razonamiento y uso de herramientas.
- Resultados publicados por Recursive: 54,9 % en Terminal-Bench 2.1, 74,2 % en SWE-bench Verified.
- Velocidad publicada: más de 125 tokens por segundo en un MacBook Pro M4 Pro, con su motor optimizado y contextos cortos.

## Ojo: pide una máquina capaz

No es para cualquier laptop. Lo documentado hoy:

**En Mac (la vía más simple, con `rec`):**
- Apple Silicon **M4 Pro, M4 Max, M5 Pro o M5 Max**.
- **Al menos 48 GB** de memoria unificada.
- Unos **30 GB** libres en disco.
- Node.js 22 y npm (para el harness pi).

```bash
curl -fsSL https://raw.githubusercontent.com/recursive-oss/rec/main/install.sh | bash
rec launch pi        # recomendado por Recursive
rec launch opencode  # alternativa
```

Revisa el script antes de ejecutarlo; instala `rec` en `~/.local/bin` y los datos en `~/.local/share/rec`. `rec` está optimizado para una sesión a la vez.

**En servidor NVIDIA (el checkpoint completo BF16):** la tarjeta del modelo indica una GPU **B300 o H200** por réplica con el kit SGLang incluido, y una descarga de **unos 80 GB**. Recursive también menciona variantes cuantizadas para NVIDIA RTX Spark (64 GB).

## Cómo repartir el trabajo

- **Flint (local):** renombrar variables y funciones, corregir un bug puntual, cambios acotados en un solo archivo, explicar un fragmento, escribir un test simple.
- **Claude:** refactors grandes, arquitectura, cambios en muchos archivos, depuración difícil.

Prompt de ejemplo para Flint:

```text
En src/utils/dates.ts, renombra la función fmt a formatDate y actualiza sus usos en ese archivo. No toques otros archivos. Muéstrame el diff.
```

Revisa siempre el diff y corre tus tests: el modelo puede equivocarse (la propia tarjeta lo advierte).

## Fuentes

Consultadas el 14-nov-2026, America/Caracas:

- Tarjeta del modelo: https://huggingface.co/RecursiveSI/flint (Apache 2.0, especificaciones, requisitos BF16)
- Anuncio: https://www.recursive.com/updates/introducing-recursive-flint (velocidad en M4 Pro, uso local, recomendación de guiar tareas complejas)
- Motor local: https://github.com/recursive-oss/rec (requisitos de Mac e instalación)
- Precios de Claude: https://claude.com/pricing (Pro US$20/mes facturado mensualmente)
- Límites de uso: https://support.claude.com/en/articles/11145838

Guía educativa de Brian Anderson. No es un producto de Recursive ni de Anthropic, ni una promesa de ahorro o resultados.
