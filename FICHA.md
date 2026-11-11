# FICHA: cómo reclamar tu negocio en ChatGPT

Recurso del video sobre Businesses in ChatGPT. Brian Anderson / CashFunnel, noviembre de 2026.

**Businesses in ChatGPT** es una función en beta que OpenAI anunció el **10 de noviembre de 2026**. Desde el **Business Hub** puedes reclamar tu negocio, mantener al día su información y ver cómo la gente interactúa contigo dentro de ChatGPT. OpenAI dice que ChatGPT lo usan **1.200 millones de personas cada semana**.

- Anuncio oficial: https://openai.com/index/introducing-businesses-chatgpt
- Página del producto: https://openai.com/business/businesses-in-chatgpt/
- Ayuda oficial (paso a paso): https://help.openai.com/en/articles/20001635-setting-up-your-business-on-chatgpt
- Esto no es un producto mío; te paso las fuentes oficiales y los límites que publica OpenAI.

## Qué hace (y qué no)

- Puedes **reclamar** un negocio si lo tienes o estás autorizado a representarlo. No hace falta una cuenta de anuncios ni un acuerdo Enterprise de ChatGPT.
- La disponibilidad **depende del país y del tipo de negocio**. La página del producto añade que, al inicio, reclamar está disponible para negocios elegibles **con sitio web**. Tiendas locales y restaurantes, según la ayuda oficial, por ahora solo pueden reclamar un listado **ya existente en Estados Unidos**. Si no aparece el tuyo y tienes un negocio online elegible, puede salir la opción de **añadirlo**.
- Reclamar **no garantiza más visibilidad** ni te da control directo sobre las recomendaciones independientes de ChatGPT. Lo dice OpenAI en la ayuda y en la página del producto. La publicidad tampoco influye en esas respuestas independientes.
- El **check azul** (insignia verificada): la ayuda oficial aclara que **solo reclamar no basta**. La insignia aparece cuando se aprueba la verificación de identidad con **Persona**. La página de producto resume que el check azul indica que el perfil fue reclamado; el detalle operativo está en la ayuda.
- Después de que aprueben el reclamo y la verificación con Persona, puedes actualizar datos (sitio, descripción, categoría, logo, políticas de entrega o devolución, foto de portada y otros campos opcionales) y, si vendes productos, conectar un **feed de catálogo** con precios y disponibilidad.
- OpenAI **revisa y publica** los cambios. Pueden tardar en verse en el listado o en una respuesta, y ChatGPT **también puede usar otras fuentes** al hablar de tu negocio. Guardar un cambio no significa que cada respuesta lo refleje al momento.
- Los **Business Agents** (un agente que responde a clientes dentro de ChatGPT) son otra cosa, y hoy están disponibles para negocios elegibles de **ecommerce y servicios online en Estados Unidos**, con sitio web, y deben cumplir la [política de Business Agents](https://openai.com/policies/business-agents-policy/). Verificar el negocio no garantiza que puedas tener agente.

## Cómo reclamarlo

1. Entra a ChatGPT, abre **Business Hub** en la barra lateral y busca tu negocio por nombre.
2. Elige el listado que coincide y confirma la cuenta de ChatGPT con la que lo vas a administrar.
3. Completa uno de los métodos de verificación que te ofrezcan:
   - **Teléfono del negocio:** código por SMS o llamada automática.
   - **Correo del negocio:** código enviado a ese email.
   - **Dominio del sitio:** un registro TXT en el DNS (copia tipo, host y valor tal cual; los cambios de DNS pueden tardar).
   - **Shopify:** conecta la tienda e inicia sesión en la tienda de ese negocio.
4. OpenAI revisa el reclamo y te escribe con la decisión o para pedir más datos. Mientras está en revisión puedes cancelarlo.
5. Cuando el reclamo esté aprobado, completa la **verificación de identidad con Persona**. Puede pedirte un documento oficial, datos de registro del negocio y prueba de que estás autorizado a representarlo. Hasta que eso se apruebe, no puedes publicar cambios, conectar un feed, ver insights ni crear un agente (si eres elegible).

Si te llegó una invitación para reclamar: abre el enlace personal del correo e inicia sesión con esa misma dirección. Si ves **Contact support**, el listado está bloqueado y hay que pedir ayuda. Si el perfil ya lo reclamó otra persona, la ayuda indica la vía de **Dispute ownership** (también con Persona). Reclamar o disputar la propiedad, según OpenAI, **no cambia su visibilidad** en ChatGPT.

## Actualizar datos y el feed de productos

Con el reclamo y Persona aprobados, abre el perfil en Business Hub y actualiza la información. Lo que subas debe cumplir la [política de Businesses in ChatGPT](https://openai.com/policies/businesses-in-chatgpt/).

Si vendes productos, puedes conectar un feed (incluido un feed de Shopify) o subir un **CSV** que siga la [especificación oficial](https://developers.openai.com/commerce/specs/file-upload/products), con sus campos obligatorios. Si das una URL, tiene que apuntar al archivo del feed. Los productos deben cumplir las políticas de Commerce. **Conectar un feed no publica un agente ni garantiza que ChatGPT recomiende tus productos.**

Campos básicos que pide la especificación de discovery (todos obligatorios): `item_id`, `title`, `description`, `url`, `brand`, `seller_name`, `image_url`, `availability` y `price`. Índice de feeds: https://developers.openai.com/commerce/specs

## Insights (menciones y clics)

Con el reclamo y Persona aprobados, en Business Hub → **Insights** ves actividad agregada de los **últimos 28 días**: menciones y clics al sitio, más temas de descubrimiento.

- En un negocio **online**, una mención cuenta cuando ChatGPT **cita su sitio web**. Solo nombrar la marca no cuenta.
- En un negocio **local**, cuenta cuando ChatGPT muestra un resultado de esa ubicación, aunque la persona no abra el listado ni entre al sitio.
- OpenAI no comparte conversaciones individuales ni chats del agente. Un indicador en blanco puede significar que no se llegó al umbral de reporte, que los datos todavía se están juntando o que el reporte no está disponible: **no significa necesariamente cero actividad**.

## Si eres elegible para un agente

Después del reclamo y de Persona, si te aparece la opción, revisa la información que va a usar el agente (productos, política de devoluciones, instrucciones), pruébalo con una pregunta habitual y **publícalo** cuando esté listo. Los clientes solo pueden hablar con un agente publicado. Publicar el agente es un paso aparte y opcional: puedes administrar el perfil y ver insights sin tener agente ni anuncios.

El agente actual, según la ayuda de OpenAI, **no completa compras, reservas ni consultas de pedidos**. Explica productos y políticas y enlaza a tu sitio, donde el cliente termina esas acciones.

## Límites honestos

- Es una función en **beta**. OpenAI dice que con el tiempo planea llevar perfiles y agentes a más mercados y categorías; hoy el agente está limitado a ecommerce y servicios online elegibles en EE. UU.
- Reclamarlo **no te sube automáticamente** en las recomendaciones. Lo dice OpenAI.
- El check azul llega con la verificación de **Persona**, no con el solo hecho de enviar el reclamo.
- ChatGPT puede seguir usando **otras fuentes** al hablar de tu negocio.
- Un feed de productos no garantiza recomendaciones ni publica un agente.
- Cumple las políticas vigentes: [Businesses in ChatGPT](https://openai.com/policies/businesses-in-chatgpt/), [Business Agents](https://openai.com/policies/business-agents-policy/) y los [términos](https://openai.com/policies/businesses-in-chatgpt-terms/).
- Si la verificación queda pendiente o falla, espera la decisión o la solicitud por correo antes de reintentar. Enviar datos a Persona no equivale a estar aprobado.

Fuente: anuncio del 10-nov-2026, página de producto, artículo de ayuda «Setting up your business on ChatGPT» y especificación de product feeds (revisados el 11-nov-2026, America/Caracas).

Guía educativa de Brian Anderson. No es un producto oficial de OpenAI ni una promesa de más visibilidad o ventas.
