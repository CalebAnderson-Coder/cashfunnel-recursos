# BUSCAR: encuentra skills para tu agente

Una skill reúne instrucciones y, en ocasiones, archivos o scripts para una tarea. `find-skills`, de Vercel Labs, ayuda a descubrir opciones; no garantiza encontrar la mejor ni convierte cualquier instalación en segura.

## 1. Antes de empezar
Necesitas Node.js con npm/npx y un agente compatible, como Claude Code o Cursor. Trabaja primero en un proyecto de prueba sin secretos ni datos de clientes. Estos comandos son instrucciones verificadas en documentación; no representan una prueba ejecutada en tu equipo.

## 2. Instala el buscador
Desde la terminal de tu proyecto:

```bash
npx skills add vercel-labs/skills --skill find-skills
```

Revisa los avisos de npm y del instalador. Elige tu agente y el alcance de instalación que necesites. No saltes las confirmaciones por costumbre.

## 3. Haz una primera búsqueda

```bash
npx skills find react testing
```

Cambia `react testing` por tu tarea concreta. También puedes pedirle a tu agente: «Busca una skill para revisar accesibilidad. Muéstrame su origen, qué archivos o scripts incluye y cómo se instala. No instales nada hasta que yo lo apruebe».

## 4. Revisa antes de instalar
Abre el repositorio de origen y lee `SKILL.md` y los scripts asociados. Comprueba autoría, mantenimiento, alcance y compatibilidad. Las instalaciones y estrellas son señales, no una auditoría de seguridad. Revisa si pide ejecutar comandos, descargar archivos, acceder a secretos o enviar información a servicios externos. No compartas credenciales ni datos de clientes para probarla.

## 5. Instala solo lo que elegiste
El formato documentado para una skill concreta es:

```bash
npx skills add <owner/repo> --skill <skill-name>
```

Sustituye los marcadores por el repositorio y nombre verificados del resultado. Prueba con una tarea pequeña y revisa los cambios antes de usarla en producción. Si no hay una opción adecuada, no instales una solo porque aparece primero.

## Fuentes oficiales
- [Documentación de Vercel](https://vercel.com/docs/agent-resources/skills)
- [Código e instrucciones de find-skills](https://github.com/vercel-labs/skills/blob/main/skills/find-skills/SKILL.md)
- [Skills CLI](https://github.com/vercel-labs/skills/)

Guía educativa de Brian Anderson. No es una garantía de seguridad ni un producto oficial de Vercel.
