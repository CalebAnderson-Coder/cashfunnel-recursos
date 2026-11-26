# TUTORIAL: los 9 capítulos del tutorial de prompts de Anthropic, resumidos en español

Pediste la palabra TUTORIAL. Aquí va el resumen.

Anthropic, la empresa que hace Claude, tiene un tutorial interactivo para aprender a escribir prompts, es decir, las instrucciones que le das al modelo. Es público en GitHub y trae nueve capítulos con ejercicios, ordenados en tres niveles, más un apéndice.

Esta guía te cuenta qué enseña cada capítulo, con un ejemplo corto de negocio en cada uno. Los ejemplos son nuestros, no del tutorial.

## Antes de empezar: tres avisos

- **Se escribió para Claude 3.** Los modelos actuales son más nuevos. Anthropic pide que, donde el tutorial y su documentación actual no coincidan, sigas la documentación actual. Las ideas de fondo siguen sirviendo; algunos detalles cambiaron.
- **Está en inglés.** No hay traducción oficial al español.
- **Los ejercicios piden una clave de API.** Es una credencial para usar Claude desde código, distinta de tu cuenta del chat. Si no programas, igual puedes practicar: lee cada capítulo y prueba la idea escribiéndole a Claude en el chat.

El repositorio menciona también una versión en Google Sheets, que Anthropic describe como más amigable. No comprobamos qué pide para funcionar.

## Nivel principiante

### Capítulo 1 · Estructura básica de un prompt
Enseña cómo se arma una conversación con Claude: tu mensaje, su respuesta y una instrucción general que fija el contexto para toda la charla.

*Ejemplo:* contexto general: «Atiendes consultas de una panadería». Mensaje: «¿Abren los domingos?».

### Capítulo 2 · Ser claro y directo
Claude no sabe nada de tu negocio salvo lo que le escribes. Hay que hablarle como a alguien que empezó hoy a trabajar contigo: qué quieres, para quién y de qué largo.

*Ejemplo:* en vez de «hazme un correo», escribe «redacta un correo de tres líneas para avisar a un cliente que su pedido sale mañana».

### Capítulo 3 · Asignarle un rol
Decirle qué papel ocupa cambia el tono y el enfoque de la respuesta.

*Ejemplo:* «Eres un contador que le explica impuestos a alguien que abre su primera tienda. Usa palabras simples».

## Nivel intermedio

### Capítulo 4 · Separar los datos de las instrucciones
Cuando pegas un texto para que lo trabaje, hay que marcar dónde empieza y dónde termina, para que no confunda el material con la orden. Así también puedes reutilizar la misma instrucción con datos distintos.

*Ejemplo:* «Resume en dos frases la reseña que está entre las etiquetas. `<reseña>` …texto del cliente… `</reseña>`».

### Capítulo 5 · Dar formato a la respuesta
Puedes pedir la forma exacta de la salida: una lista, una tabla, un texto entre etiquetas. El capítulo enseña además a escribir tú el comienzo de la respuesta para guiarla; esa técnica es de las que conviene confirmar en la documentación actual antes de usarla.

*Ejemplo:* «Devuelve solo una tabla con dos columnas: producto y precio. Sin texto antes ni después».

### Capítulo 6 · Pensar paso a paso
Si la tarea tiene varias partes, pídele que razone antes de dar la respuesta final. Cuando ordena primero sus ideas, se equivoca menos.

*Ejemplo:* «Antes de recomendar un plan, escribe los pros y los contras de cada uno. Después da tu recomendación».

### Capítulo 7 · Usar ejemplos
Mostrarle uno o varios ejemplos de lo que esperas suele funcionar mejor que describirlo con adjetivos.

*Ejemplo:* pega dos respuestas tuyas a clientes y agrega «responde este mensaje nuevo con el mismo tono».

## Nivel avanzado

### Capítulo 8 · Hacer que invente menos
Los modelos a veces afirman cosas que no son ciertas. El capítulo enseña a reducirlo: darle permiso para decir que no sabe y pedirle que primero busque en el texto la parte que sostiene su respuesta. Reduce el problema; no lo elimina.

*Ejemplo:* «Responde solo con lo que diga el contrato adjunto. Cita la cláusula. Si no aparece, escribe "no está en el contrato"».

### Capítulo 9 · Prompts complejos por industria
Junta todo lo anterior en un solo prompt largo y ordenado: rol, contexto, datos separados, ejemplos, pasos y formato. Lo practica con casos de distintos sectores.

*Ejemplo:* un asistente para una clínica dental con su rol, la lista de servicios entre etiquetas, dos respuestas modelo y la regla de derivar a una persona cuando alguien pregunta por un diagnóstico.

## Apéndice
Va más allá del prompt suelto: encadenar varios prompts, darle herramientas al modelo y hacer que busque información. Es material técnico; déjalo para el final.

## Por dónde empezar si no programas

1. Lee los capítulos 1 a 3 y aplícalos hoy en el chat de Claude, con una tarea real de tu negocio.
2. Suma el capítulo 4 cuando empieces a pegar textos largos.
3. Suma el 7 cuando quieras que escriba con tu tono.
4. Usa el 8 siempre que la respuesta dependa de un documento.

## Enlaces

- Tutorial interactivo de Anthropic: https://github.com/anthropics/prompt-eng-interactive-tutorial
- Documentación actual de prompting de Anthropic: https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/overview
- Buenas prácticas actuales: https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-prompting-best-practices

---

Guía de Brian Anderson / CashFunnel, noviembre de 2026. Resumen propio en español; los nombres, comandos y enlaces salen de las páginas oficiales. Este material no es de los autores originales ni está patrocinado por ellos.

Si quieres aprender a hacer reels con IA paso a paso, la comunidad «Contenido en Sistema» en Skool es gratis: https://www.skool.com/primer-empleado-ia-6500
