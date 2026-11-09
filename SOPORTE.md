# SOPORTE: lo primero que le daría a un agente de soporte

Uber movió unos 320 millones de viajes y pedidos en su semana de Halloween. Los agentes de IA pidieron **4 viajes** y unos **500 pedidos** de comida. Esa misma semana, Airbnb dijo que su asistente de IA resolvió cerca del **40%** del soporte sin una persona, y que el costo de soporte por reserva bajó más de **17%**.

La lección es simple: la IA deja plata donde tu cliente está esperando, no donde ya es rápido.

Esta guía es lo primero que yo le daría a un agente de soporte en un negocio pequeño o mediano. Es educativa. No es un producto de Uber ni de Airbnb.

## 1. Los datos (con fuente)
| Dato | Fuente |
|---|---|
| ~320 millones de viajes y pedidos (Uber + Uber Eats) en la semana de Halloween; agentes de IA: ~500 pedidos de comida y **4 viajes** | [Transcripción Q3 2026 Uber (Motley Fool)](https://www.fool.com/earnings/call-transcripts/2026/11/04/uber-uber-q3-2026-earnings-call-transcript/) · [The Verge](https://www.theverge.com/transportation/1026306/uber-ai-agents-q3-earnings-disintermediation) · [Thurrott](https://www.thurrott.com/a-i/343596/uber-only-had-four-rides-booked-by-ai-agents-last-week) |
| Pedir un viaje ~50 s; reordenar comida ~90 s (CEO Dara Khosrowshahi) | Misma transcripción Uber |
| ~40% de los casos de soporte resueltos sin agente humano; costo de soporte por reserva −17% interanual; asistente en 50+ idiomas | [Resultados Q3 2026 Airbnb](https://news.airbnb.com/airbnb-q3-2026-financial-results) |

## 2. La regla
- **Automatiza** donde el cliente espera: respuestas, reclamos, estado de un pedido o pago, seguimientos.
- **No automatices** donde el cliente ya es rápido o disfruta elegir (pedir un Uber, armar un viaje).
- Empieza por tareas aburridas y repetidas. El agente registra y avisa; **el dinero lo aprueba una persona**.

## 3. Primero esto (lista corta)
Dale al agente solo estas cuatro cosas, con respuestas ya escritas por ti:

1. **Preguntas repetidas** de horario, precio, dirección y estado de pedido.
2. **Confirmación de pagos** ya recibidos (sin cobrar ni emitir reembolsos solo).
3. **Recordatorios** de cuota o seguimiento amable.
4. **Primer filtro de reclamos**: clasificar y responder lo que esté en tu base; el resto a una persona.

### Plantilla: tus 10 preguntas más repetidas
Cópialas de tu WhatsApp o inbox de los últimos 30 días:

| # | Pregunta exacta del cliente | Respuesta corta aprobada | ¿Puede responder el agente solo? (sí/no) |
|---|---|---|---|
| 1 | | | |
| 2 | | | |
| 3 | | | |
| 4 | | | |
| 5 | | | |
| 6 | | | |
| 7 | | | |
| 8 | | | |
| 9 | | | |
| 10 | | | |

Si no cabe en “sí”, no lo dejes solo: pásalo a humano.

## 4. Cuándo pasa a una persona
El agente **deja de responder solo** y escala cuando hay:

- Dinero: cobros, descuentos, reembolsos, disputas.
- Enojo o amenaza de queja pública.
- Excepciones a tu política.
- Cualquier cosa que no esté en su base de respuestas.

Antes de conectar un agente a WhatsApp, CRM o pagos, revisa:
- [`PERMISOS`](https://github.com/CalebAnderson-Coder/cashfunnel-recursos/blob/main/PERMISOS.md) — 8 accesos que nunca le doy a un agente.
- [`AUDITAR`](https://github.com/CalebAnderson-Coder/cashfunnel-recursos/blob/main/AUDITAR.md) — 5 cosas a revisar antes de conectar.

## 5. Cómo medirlo (1 hoja, cada semana)
Usa las mismas tres métricas que importan en soporte con IA:

| Métrica | Cómo contarla | Meta inicial sugerida |
|---|---|---|
| % resuelto sin humano | Casos cerrados solo por el agente ÷ total de casos de la semana | Empieza midiendo; no inventes un % |
| Tiempo a primera respuesta | Minutos desde el mensaje del cliente hasta la primera respuesta del agente | Menos que tu promedio humano actual |
| Casos devueltos a persona | Cuántos escaló el agente y por qué motivo | Baja semana a semana sin esconder errores |

Una hoja de cálculo basta. Si no mides, no sabes si el agente ayuda o solo contesta rápido mal.

## 6. Ejemplo real: Inova
En Inova los agentes **no venden**. Registran pagos y mandan recordatorios. En los últimos 30 días el panel mostró **287 recordatorios de cuota** enviados, con **9 agentes activos** hoy. Una persona sigue aprobando el dinero.

Eso es soporte operativo, no un chatbot de ventas.

## 7. Herramientas para arrancar (sin inventar cifras)
Empieza por lo que ya documentamos en [`BOT`](https://github.com/CalebAnderson-Coder/cashfunnel-recursos/blob/main/BOT.md):

1. **WhatsApp Business** — mensaje de ausencia, bienvenida y respuestas rápidas ([app de negocio](https://business.whatsapp.com/products/business-app)).
2. **Meta Business Agent** — IA dentro de WhatsApp Business (disponible según país/negocio; gratis hasta un límite que Meta no publica).
3. **Make + ChatGPT** — escenario con WhatsApp Business Cloud ([integración oficial](https://www.make.com/integrations/openai-gpt-3/whatsapp-business-cloud)).

Checklist general de datos y primera tarea: [`AGENTE`](https://github.com/CalebAnderson-Coder/cashfunnel-recursos/blob/main/AGENTE.md).

## Regla de oro
El agente responde, clasifica y recuerda. **Pagos, descuentos y excepciones los aprueba una persona.**

---
Guía educativa de Brian Anderson / CashFunnel. Fuentes revisadas el 9-nov-2026 (hora Caracas). No es un producto oficial de Uber, Airbnb, Meta ni Make.
¿Quieres que lo armemos para tu negocio? Escríbeme por DM en TikTok o Instagram: @briananderson.ai
