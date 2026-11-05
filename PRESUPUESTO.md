# PRESUPUESTO — Bot de equipo que te dice dónde mover tu presupuesto de anuncios
*Recurso del video "Le pusimos un bot a decidir el presupuesto de marketing" — Brian Anderson / CashFunnel (5-nov-2026)*

Es un patrón para armar tu propio bot. No es un SaaS. Funciona con Grok Bot (bot de equipo), ChatGPT/Claude con proyecto compartido, o cualquier agente que lea hojas de cálculo.

## Checklist
1. **Fuentes de datos**: exporta de Meta Ads o Google Ads: campaña, gasto, resultados y costo por resultado (CPA). Súmale una hoja de **presupuesto mensual** con presupuesto, gastado y restante.
2. **Metas escritas**: CPA máximo aceptable (ej. $25 por cliente), presupuesto restante del mes y clientes objetivo.
3. **Etiqueta tus experimentos**: marca como `experimento` las campañas en prueba. Regla: no recomendar recortarlas antes de X días o X clics/resultados.
4. **Instrucciones fijas del bot** (guárdalas una vez para todo el equipo):
   - Solo lectura. **Nunca edita ni pausa campañas.**
   - Todo cambio lo aprueba una persona.
   - Si una campaña tiene pocos datos (ej. menos de 20 resultados), lo dice antes de opinar.
5. **Lógica**: gasto vs. clientes por campaña → compara contra el CPA meta → propone mover dinero **dentro** del presupuesto restante, nunca subirlo.
6. **Entrega**: resumen semanal por Slack o email: "dónde podríamos mover el gasto", con los números que lo respaldan.
7. **Repregunta siempre**: "¿Por qué recomiendas ese cambio?", "¿Cuántos datos tenemos de esa campaña?", "¿Qué riesgo tiene?"
8. **Decisión humana**: tú revisas los números, cuestionas la recomendación y decides si haces el cambio.

## Prompt plantilla (cópialo)
```
Eres "Presupuesto", el analista de anuncios de nuestro equipo.
Datos: [hoja Campañas] y [hoja Presupuesto mensual].
Metas: CPA máximo $[25]; presupuesto del mes $[6.000]; clientes objetivo [300].
Experimentos: campañas con etiqueta "experimento". No recomiendes recortarlas antes de [14] días o [1.000] clics.
Reglas: solo lectura. Nunca edites ni pauses campañas. Si una campaña tiene menos de [20] resultados, avísalo primero.
Tarea: compara gasto vs. clientes de cada campaña contra la meta y el presupuesto restante.
Entrega: máximo 5 líneas. Qué mover, de dónde a dónde, cuánto por día y por qué (con números). Termina con: "¿Lo apruebas?"
```

## Hoja de ejemplo (columnas)
| Campaña | Gasto | Clientes | CPA | Meta CPA | Etiqueta |
|---|---|---|---|---|---|
| Leads — Webinar | $1.676 | 142 | $11,80 | $25 | escalar |
| Lookalike 2% | $840 | 31 | $27,10 | $25 | — |
| Prueba — Reels UGC | $239 | 12 | $19,90 | $25 | experimento |
*(números de ejemplo)*

## Regla de oro
El bot **recomienda**; el dinero lo mueve **una persona**.

---
¿Quieres que te lo armemos con tus cuentas? Escríbeme por DM **@briananderson.ai**.
