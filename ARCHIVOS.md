# ARCHIVOS — Las plantillas de los 4 archivos .md que convierten a Claude en un empleado
*Recurso del video "¿Para qué pagas Claude si lo usas como un chat?" — Brian Anderson / CashFunnel*

Estructura (en la carpeta de tu proyecto o de trabajo con Claude Code / Cowork):
```
mi-negocio/
├── AGENTS.md          ← quién eres y cómo trabajas (lo lee siempre)
├── memory.md          ← lo que aprende de ti
├── contexto/          ← info pesada y detallada
│   ├── oferta.md
│   ├── clientes.md
│   └── marca.md
└── skills/            ← procesos reutilizables
    └── responder-cotizacion/SKILL.md
```
En Claude Code el archivo que se lee automáticamente se llama `CLAUDE.md`; puedes poner ahí una línea: `Lee AGENTS.md y memory.md antes de cualquier tarea.`

## 1. AGENTS.md (lo que le darías a un empleado nuevo)
```markdown
# Mi negocio
- Qué vendo: …   A quién: …   Precio: …
# Mi voz
- Tuteo, frases cortas, sin emojis en correos.
# Cómo me gusta trabajar
- Antes de enviar, publicar o pagar: pregúntame.
- Si falta información, búscala en /contexto antes de preguntar.
```
## 2. contexto/ (información más pesada)
Catálogo, precios, preguntas frecuentes, perfil de cliente, guía de marca. Un archivo por tema.
## 3. memory.md (sus preferencias aprendidas)
```markdown
# Preferencias aprendidas
- 2026-11-04: No firmar correos con "Saludos"; usar "Un abrazo, Brian".
```
Instrucción en AGENTS.md: *"Cuando te corrija algo, anótalo en memory.md con la fecha."*
## 4. skills/ (procesos de una vez para siempre)
Le muestras un proceso una vez y le pides: *"Empaqueta esto como un skill en skills/<nombre>/SKILL.md"*.
```markdown
---
name: responder-cotizacion
description: Úsalo cuando un cliente pida precio o cotización.
---
1. Lee contexto/oferta.md
2. Arma la cotización con el formato de siempre
3. Muéstramela antes de enviarla
```
Así una tarea de cuatro horas se vuelve una sola instrucción.

Docs oficiales: https://docs.anthropic.com/en/docs/claude-code/memory · https://docs.anthropic.com/en/docs/claude-code/skills
