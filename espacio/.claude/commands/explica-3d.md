---
description: Explicador 3D animado de cualquier tema
---
Crea un explicador 3D vertical sobre: $ARGUMENTS

Archivo de salida: `sistema_solar.html`. DURATION = 2.7 s.

Escena: el sistema solar visto en 3/4 desde arriba (cámara inclinada ~62° respecto al plano orbital).
- Fondo casi negro (#020203) con estrellas tenues.
- Sol en el centro de la pantalla (x=540, y≈965), esfera ~180px de diámetro, superficie naranja/amarilla con granulado animado por shader y un halo/glow naranja amplio y suave alrededor (bloom falso con sprite aditivo).
- 8 órbitas elípticas concéntricas como líneas finas blancas al 22 % de opacidad; la más externa casi toca los bordes laterales de la pantalla (ancho ≈1100px) y ocupa en vertical aprox. y 560–1400.
- 8 planetas a escala estilizada (no real) y GRANDES, con estos diámetros en pantalla: Mercurio 30px, Venus 50px, Tierra 56px, Marte 44px, Júpiter 120px, Saturno 86px con anillo de 190px de diámetro exterior, Urano 70px, Neptuno 66px, con materiales distintos y luz del Sol (lado oscuro opuesto al Sol): Mercurio gris, Venus crema, Tierra azul, Marte rojo, Júpiter grande beige con bandas, Saturno con anillo grueso gris claro, Urano celeste pálido, Neptuno azul. Cada uno con su nombre en español encima (Inter 600, 26px, blanco, sombra suave, 10px por encima del planeta): Mercurio, Venus, Tierra, Marte, Júpiter, Saturno, Urano, Neptuno. Posiciones iniciales repartidas para que se lean todos los nombres sin solaparse (Neptuno arriba-derecha, Urano derecha, Saturno abajo-derecha, Júpiter abajo-izquierda, Marte/Tierra/Venus a la izquierda del Sol).
- Animación: los planetas avanzan en sus órbitas (interiores más rápido; Mercurio ~40°, Neptuno ~6° en toda la duración) y toda la cámara orbita lentamente ~8°.
- Headline (tipeo de 0.25 a 0.75 s): `8 planetas, un solo Sol.` con `Sol.` en la caja azul.
- Etiqueta inferior: `explicador del sistema solar` / `con Claude Code`.
## Reglas técnicas comunes (todas las escenas)
- Entrega UN solo archivo HTML en la carpeta actual (nombre indicado abajo). Sin otros archivos: texturas procedurales (canvas 2D o shaders), nada de imágenes externas.
- three.js por importmap fijado: `"three": "https://cdn.jsdelivr.net/npm/three@0.170.0/build/three.module.js"` (y `three/addons/` → `https://cdn.jsdelivr.net/npm/three@0.170.0/examples/jsm/` si hace falta). Fuentes: Google Fonts `Inter:wght@500;600;700;800`, `JetBrains Mono:wght@400;500` y `Cormorant Garamond:ital,wght@1,500`.
- Lienzo vertical FIJO 1080x1920 CSS px (`html,body{margin:0;width:1080px;height:1920px;overflow:hidden;background:#020202}`), WebGL renderer 1080x1920 con `setPixelRatio(1)`, `antialias:true`, `preserveDrawingBuffer:true`, `toneMapping=ACESFilmic`, `outputColorSpace=SRGB`.
- Tiempo determinista: NADA de Date.now/performance.now/Math.random para la animación. Usa un PRNG con semilla fija. Expón `window.DURATION` (segundos), `window.setTime(t)` que deja la escena EXACTAMENTE en el instante t (3D + overlays DOM) y renderiza ese frame de forma síncrona, y `window.sceneReady=true` cuando todo (incluidas fuentes: `await document.fonts.ready`) esté listo. Si la URL NO trae `?capture`, reproduce sola en bucle con requestAnimationFrame llamando a setTime((ms/1000)%DURATION).
- Overlays en DOM por encima del canvas:
  - Headline: centrado, Inter 700, 64px, blanco, letter-spacing -0.5px, línea con la parte superior de las mayúsculas en y≈261 (contenedor top:236px). Se TIPEA letra a letra (se revela carácter a carácter, sin cursor). La palabra clave va en una caja azul #2B5BE6 con radio 8px, padding 0 10px, alto 69px (y 250–319), texto blanco; la caja aparece con un pop (scale 0.85→1, 120 ms) cuando el tipeo llega a esa palabra.
  - Etiqueta inferior centrada: título Inter 700 40px blanco con su caps-top en y≈1452; debajo `con Claude Code` en Cormorant Garamond itálica 40px color #b9b9b9, caps-top y≈1500. Detrás, una banda horizontal de 0 a 1080 de ancho, y 1420–1560, negro al 55% con bordes difuminados (gradiente vertical). Deja libre la franja y 1590–1700 (espacio para tu marca de agua).
  - Deja libre la esquina superior izquierda (x<440, y<190): espacio para tu logo o chip.
- Estética: premium, 3D real con luces y sombras suaves, look «juguete / Pixar mate» limpio; nada de emojis ni íconos planos. Todo el texto en español.
- Al terminar, abre mentalmente el archivo y revisa que no haya errores de consola y que setTime(0), setTime(DURATION/2) y setTime(DURATION) se vean bien.
