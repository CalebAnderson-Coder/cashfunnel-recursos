# ANUNCIOS: de 30 minutos a 30 segundos, el flujo de Anthropic

Recurso del video «Anthropic: de 30 minutos a 30 segundos por anuncio». Brian Anderson / CashFunnel, 16 de noviembre de 2026.

Esta guía no es un plugin oficial ni un producto que se descargue. Es el método para **armar en tu negocio** los dos flujos que cuenta [el propio blog de Anthropic](https://claude.com/blog/how-anthropic-uses-claude-marketing) (26-ene-2026): Austin Lau, growth marketer, nunca había escrito una línea de código y, una semana después de empezar con Claude Code, tenía un plugin de Figma y un comando para anuncios de Google Ads. Él atribuye el salto de **30 minutos a 30 segundos por anuncio**. Es una cifra de su blog, no una medición independiente.

**No es PRESUPUESTO.** PRESUPUESTO es un bot que te dice dónde mover el gasto. Aquí el tema es **crear** anuncios (titulares, descripciones y variantes), con revisión tuya antes de subirlos.

## Costo real

- **No hay una app de Anthropic que instales para esto.** Armas el flujo tú, con Claude Code.
- **Claude Code no está en el plan Free.** En [claude.com/pricing](https://claude.com/pricing) (consultado el 16-nov-2026, America/Caracas), Pro cuesta **20 USD al mes** si pagas mes a mes, o **17 USD al mes** si pagas el año por adelantado (200 USD). Los precios cambian: revísalos el día que contrates.
- Figma y Google Ads tienen sus propias cuentas y, si aplica, sus propios planes.
- El plugin de Austin y su comando `/rsa` **no están publicados**. Esta guía te deja reconstruir lo que el artículo describe.

## Qué vas a armar

1. **Tu tono de marca y ejemplos tuyos.** Austin le dio a Claude Skills con el tono de Anthropic y ejemplos escritos con los equipos de product marketing y copy. Sin eso, el modelo improvisa tu voz.
2. **Un comando de anuncios** (él lo llamó `/rsa`, de *responsive search ads*). Claude pide datos de la campaña, copy que ya tienes y palabras clave; cruza eso con tu tono y con los límites de Google Ads; y te entrega un CSV listo para subir: el artículo habla de **15 titulares y 4 descripciones** por anuncio.
3. **Revisión manual antes de subir.** El pie de imagen del artículo lo dice con esas palabras: el CSV queda listo «after undergoing manual review». Austin también dice que Claude no siempre acierta a la primera: riffa y refina. La regla: la IA produce, tú apruebas.
4. **(Opcional, más adelante.)** Un plugin de Figma: pegas los titulares y salen decenas de variantes con un clic. El artículo de julio de 2025 habla de «hasta 100» en otro contexto; no mezcles esa cifra con este caso.

## Cómo empezarlo en Claude Code

1. Instala Claude (app de escritorio o CLI) y entra a **Claude Code**: [claude.com/download](https://claude.com/download).
2. Abre una carpeta de trabajo, por ejemplo `anuncios/`, con dos archivos tuyos:
   - `tono.md`: cómo habla tu marca (qué sí, qué no, palabras que usas, palabras que evitas).
   - `ejemplos.md`: 5–10 anuncios **tuyos** que ya hayas publicado o aprobado, con lo que funcionó y lo que no.
3. En la primera sesión, pega este prompt (cámbialo por tu negocio):

```
Voy a crear anuncios de búsqueda responsivos para Google Ads.

Primero lee tono.md y ejemplos.md. No inventes beneficios, precios ni pruebas que yo no te haya dado.

Te voy a pasar: nombre de la campaña, el grupo de anuncios, la URL de destino, las palabras clave y el copy que ya tenemos.

Propón 15 titulares (máximo 30 caracteres) y 4 descripciones (máximo 90).
Dime el recuento de caracteres de cada línea.
Al final, arma un CSV listo para subir a Google Ads, con las columnas de campaña y grupo de anuncios.

No lo des por cerrado: señálame lo que no te queda claro. Yo reviso todo antes de subir nada.
```

4. Cuando el ida y vuelta te funcione, pide a Claude Code que deje ese flujo guardado como un **comando slash** (por ejemplo `/rsa`) y, si usas Skills, como una skill de tono de marca. Así no lo vuelves a explicar cada vez.
5. **Revisa el CSV a mano.** Comprueba caracteres, promesas, oferta, URL y que no se haya colado un beneficio que tú no diste. Sube tú el archivo a Google Ads.

## El plugin de Figma, si lo necesitas

No hay un plugin oficial de Anthropic para descargar. Austin le pidió a Claude Code que le armara uno, apuntando a la documentación de la API de Figma, y lo instaló en su cuenta. Si tu cuello de botella son las variantes visuales, abre Claude Code y descríbele el mismo problema: un frame, una lista de titulares (por ejemplo desde una hoja), y que genere las permutaciones con un clic. Reserva una hora para el primer prototipo, como cuenta él, y pruébalo en un archivo de Figma de prueba, no en la librería en vivo.

## Límites honestos

- La cifra de 30 minutos a 30 segundos la cuenta Anthropic de su propio marketer. No promete el mismo ahorro en tu cuenta.
- El artículo no da resultados de ventas ni de conversión. Un anuncio más rápido de producir no es un anuncio que convierte más.
- Sin tus ejemplos y tu tono, el copy sale genérico.
- Esto no mueve presupuestos, no publica solo y no “maneja” tu cuenta de Google Ads.

## Fuentes

Consultadas el 16-nov-2026, America/Caracas:

- Caso y cifra, Austin Lau, plugin de Figma, `/rsa`, CSV y revisión manual: https://claude.com/blog/how-anthropic-uses-claude-marketing (26-ene-2026)
- Respaldo del equipo de marketing con Claude Code: https://claude.com/blog/how-anthropic-teams-use-claude-code (24-jul-2025)
- Límites oficiales de anuncios de búsqueda responsivos (hasta 15 titulares de 30 caracteres y 4 descripciones de 90): https://support.google.com/google-ads/answer/17092074
- Precios de Claude: https://claude.com/pricing

---
¿Quieres que armemos este flujo con el tono de tu marca? Escríbeme por DM **@briananderson.ai**.
