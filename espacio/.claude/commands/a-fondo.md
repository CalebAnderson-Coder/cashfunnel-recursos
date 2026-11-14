---
description: Inmersión cinematográfica a fondo en cualquier tema
---
Crea una inmersión cinematográfica vertical sobre: $ARGUMENTS

Archivo de salida: `agujero_negro.html`. DURATION = 2.6 s.

Escena: un agujero negro estilo «Interstellar».
- Fondo negro con estrellas tenues.
- Horizonte de sucesos: esfera negra pura centrada en (x≈520, y≈1000), ~460px de diámetro. COMPOSICIÓN OBLIGATORIA: el círculo negro se ve ENTERO (nunca media esfera ni cúpula): el disco de acreción pasa POR DETRÁS de la esfera (dibuja la esfera encima del disco: renderOrder alto + depthTest false + transparent:true en el material de la esfera; sin transparent:true three.js la pinta en la pasada opaca, ANTES del disco aditivo, y desaparece). El anillo de fotones es concéntrico con la esfera.
- Disco de acreción en perspectiva (inclinación ~78°), muy ancho (se sale por los dos lados de la pantalla), con filamentos de gas estirados en la dirección de la órbita (rayas largas tipo motion blur, NO anillos concéntricos tipo ondas de agua), color naranja saturado #ff5a14 en el exterior → #ffb070 → blanco cálido #fff3dc en el borde interior incandescente, turbulencia animada en shader, más brillante del lado que se acerca (Doppler); gira visiblemente.
- El disco NUNCA debe mostrar bordes rectos ni rectángulos: usa geometría de anillo (RingGeometry o shader) con alpha que se desvanece suavemente a 0 en el radio exterior; el disco brillante ocupa en pantalla aprox. y 760–1330 (por debajo de y 1380 todo oscuro para que la etiqueta inferior se lea sobre negro) y se sale por los dos lados. Debe verse luminoso y saturado (no apagado): emisivo con blending aditivo.
- Lente gravitacional falsa: un anillo de fotones grueso (≈70px) color crema cálido #ffdcae (no blanco puro, opacidad ≈0.85) de ≈330px de radio alrededor del centro de la esfera, un poco desplazado hacia arriba, con glow.
- Animación: el disco rota, el anillo pulsa un poco, la cámara hace un push-in suave del 6 %.
- Headline (tipeo de 0.30 a 0.70 s): `Ni la luz escapa.` con `luz` en la caja azul; las demás palabras se quedan MUY atenuadas (color #1f1f1f) — solo la palabra clave destaca.
- Tres callouts a la derecha (tarjetas blancas radio 10px, sombra; tarjetas de 420×108px con x 600–1020; título Inter 700 34px #111, subtítulo JetBrains Mono 30px #444; el texto no debe tocar el borde de la tarjeta), cada una con una línea guía fina gris claro hacia la izquierda que termina en un punto naranja #FF5A36 con glow sobre la parte señalada:
  1. t=0.75: `Disco de acreción` / `gas que gira y cae` (tarjeta en x≈600–1020, y≈1170–1278), punto sobre el disco a la derecha.
  2. t=1.00: `Horizonte de sucesos` / `punto sin retorno` (y≈810–918), punto sobre el borde superior izquierdo de la esfera.
  3. t=1.25: `Singularidad` / `el centro aplastado` (y≈985–1093), punto en el centro de la esfera.
  Cada callout entra con fade + deslizamiento de 20px desde la derecha en 200 ms.
- Etiqueta inferior: `agujero negro a fondo` / `con Claude Code`.
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
