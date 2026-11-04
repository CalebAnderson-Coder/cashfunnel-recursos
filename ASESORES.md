# ASESORES — Roast Room: un consejo de asesores con IA en Claude Code (gratis)
*Recurso del video "Armé un consejo de asesores con IA" — Brian Anderson / CashFunnel*

**Roast Room** (de Nate Herk / AI Automation Society) es gratis y open source. Llevas una decisión difícil de tu negocio, un consejo de asesores IA la discute, vota y te da un veredicto con puntajes y un PDF.
- Repo: https://github.com/nateherkai/roast-room

## El consejo por defecto (7)
Bezos (estrategia, ¿es reversible?) · Paul Graham (producto, ¿la gente lo quiere?) · Hormozi (oferta, precio, ventas) · Gary Vee (marketing, atención) · Dan Martell (equipo y tu tiempo) · Gino Wickman (operaciones) · Buffett (dinero y riesgo). Hay 5 más de reserva (Naval, Codie Sanchez, Leila Hormozi, Sara Blakely, Elon Musk) y puedes crear otro con `/newroaster`.
Cada asesor es un subagente con su "cerebro": notas sacadas de sus libros, cartas, charlas y videos públicos. **Son personajes de IA, no las personas reales.**

## Lo que necesitas
- **Claude Code** con tu plan de Claude (no necesita API key).
- **Node.js 20+** para la sala visual (opcional).

## Montarlo
```bash
git clone https://github.com/nateherkai/roast-room.git
cd roast-room
npm start            # abre http://localhost:4730
claude               # en la misma carpeta
/roast-room ¿Subo mis precios 20% este trimestre?
```
Responde las preguntas del "Chair", mira el debate y descarga el PDF. El reporte completo queda en `sessions/`.

## Ojo
Un consejo completo usa bastante de tu plan (muchas corridas de subagentes). Úsalo para decisiones que importan.
