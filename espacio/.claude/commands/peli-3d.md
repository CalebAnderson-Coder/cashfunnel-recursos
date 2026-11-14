---
description: Corto 3D cinematográfico de una sola escena sobre la idea que escribas
---
Crea un corto 3D vertical sobre: $ARGUMENTS

Archivo de salida: `luna.html`. DURATION = 2.8 s.

Escena: una persona astronauta en la Luna.
- Fondo negro con estrellas finas (puntos pequeños, algunos titilan). Arriba a la derecha la Tierra estilo caricatura: esfera de ~240px de diámetro centrada en (x≈885, y≈545) del encuadre, océano azul, continentes verdes, nubes blancas, contorno oscuro fino, rota despacio.
- Suelo lunar gris claro (#c9c9cc→#8d8d92) desde y≈1295 hasta abajo, con relieve suave y cráteres poco profundos, luz rasante desde la izquierda; sombra de contacto suave bajo el astronauta (solo sombra de contacto, sin sombras largas proyectadas).
- Astronauta blanco mate hecho con primitivas suavizadas (cápsulas, esferas): casco esférico con visor dorado reflectante (MeshPhysical, metalness alto) con un brillo especular, panel en el pecho con 3 luces pequeñas (rojo, azul, verde pastel), mochila, guantes y botas redondeadas. Centrado en x=540; de pie sus botas tocan el suelo en y≈1290 y la parte superior del casco queda en y≈730 (altura total ≈560 px en pantalla; NO más grande).
- Animación (t en s): 0–0.85 de pie con respiración leve; 0.85–1.05 se agacha un poco; 1.05 salta con los brazos abiertos hacia arriba; sube MUY lento (gravedad 1/6: curva parabólica suave) hasta un apogeo en t≈2.2 con las botas ~300 px sobre el suelo (el casco nunca sube por encima de y≈420, siempre por debajo del headline) con las piernas un poco recogidas y los brazos ondulando; 2.2–2.8 empieza a bajar despacio. La sombra se achica y se aclara al subir. Polvo lunar fino al despegar.
- Cámara: plano fijo con un dolly-in suave del 5 % a lo largo de la duración.
- Headline (tipeo de 0.40 a 1.00 s): `Gravedad: 1/6 de la terrestre.` con `1/6` en la caja azul (pop cuando aparece).
- Etiqueta inferior: `salto en la Luna` / `con Claude Code`.
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
