# Accesos que nunca le doy a un agente de IA

*Una página práctica para dueños de negocio que ya usan (o van a usar) agentes de IA.*

**La regla:** un agente recibe el acceso mínimo para *una* tarea, por el tiempo mínimo, y todo lo irreversible pasa por un humano. Si el agente se equivoca o lo engañan, el daño debe quedar pequeño.

## El caso Binance (nov. 2026)
Un ingeniero hizo una "prueba técnica" de una entrevista de trabajo falsa. Era malware. Desde su equipo, los atacantes usaron una herramienta de IA interna que tenía acceso de más y llegaron al sistema que firma transacciones: más de 6.300 millones perdidos. El problema no fue solo la IA. Fue que la IA podía llegar a todo.

## Lo que nunca le doy
1. **Firmar o aprobar pagos.** El agente puede *preparar* la transferencia o la factura; un humano la aprueba en otro canal (app del banco, segunda persona). Nada de tarjetas guardadas sin límite.
2. **Contraseñas maestras o el gestor de contraseñas completo.** Si necesita una cuenta, le creo una propia, con permisos de lectura cuando se pueda.
3. **Cuentas de administrador** (Google Workspace, Shopify, AWS, el dominio). Un usuario limitado para lo que haga falta; el admin queda conmigo.
4. **Claves de API "de todo".** Claves con alcance mínimo (solo lectura, solo un proyecto), con fecha de vencimiento, y las roto si algo huele raro.
5. **Borrar cosas.** Bases de datos, correos, archivos, clientes: el agente puede archivar o proponer; borrar lo confirmo yo.
6. **Enviar a clientes sin revisión** (correos masivos, WhatsApp, publicaciones) hasta que tenga un historial probado. Primero borradores.
7. **Datos sensibles de clientes completos** (cédulas, tarjetas, historiales). Le paso solo los campos que la tarea necesita.
8. **Instalar o ejecutar cosas de desconocidos.** Skills, plugins, "pruebas técnicas", archivos adjuntos: se revisan antes y se corren en un entorno separado.

## Cómo lo aplico en la práctica
- **Una tarea, un acceso:** el agente de facturación no ve el correo de RR. HH.
- **Montos con tope:** si algún día delego pagos, límite diario bajo y alerta en cada movimiento.
- **Doble aprobación** para todo lo irreversible: dinero, borrar, publicar, cambiar permisos.
- **Registro de todo lo que hace**, y lo reviso cada semana.
- **Equipos separados:** lo que pruebo (descargas, entrevistas, demos) no vive en la máquina que tiene acceso a pagos.
- **Botón de apagado:** sé exactamente cómo revocar sus accesos en 5 minutos.

## Pregunta de control
Antes de darle un acceso: *"Si un atacante controlara este agente mañana, ¿cuánto me costaría?"* Si la respuesta te da miedo, el acceso es demasiado grande.

*— Brian Anderson*

---
Recurso del video del caso Binance. ¿Quieres revisar los accesos de tus agentes? Escríbeme por DM **@briananderson.ai**.
