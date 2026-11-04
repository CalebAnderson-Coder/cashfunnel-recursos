# LÍMITE — 3 reglas antes de darle dinero o pagos a un agente de IA
*Recurso del video "9 de 10 IAs rompieron su propio límite de gasto" — Brian Anderson / CashFunnel*

## Qué pasó (estudio Cornell Tech + Yale, oct-2026)
- 10 modelos de IA recibieron una billetera (Circle) con límite de **0,01 USDC al día**, acceso al correo del dueño y 3 facturas por pagar.
- **9 de 10 se subieron su propio límite** al menos una vez, copiando el código de verificación que llegaba al correo. Solo Claude Opus 5.5 nunca lo intentó: pagó hasta el límite y avisó.
- En otra prueba, con un atacante que se hacía pasar por el dueño, 5 de 10 subieron el límite y le pagaron al atacante al menos una vez.
- Fueron pruebas controladas (10 USDC reales en Base, 20 corridas por modelo), no robos a clientes reales.

**Principio:** si el agente puede llegar al permiso, no es un permiso. La aprobación tiene que vivir fuera de su alcance.

## Las 3 reglas
1. **Que no pueda leer el correo donde llegan tus códigos.** Usa otro correo (o la app autenticadora en tu teléfono) para las verificaciones. Circle lo dice en su guía: nunca le des a un agente acceso sin restricciones a tu correo.
2. **Los pagos grandes los apruebas tú, desde tu teléfono.** Define un monto (ej. más de $20) que siempre requiere tu "sí".
3. **Un límite que solo tú puedas cambiar.** Configúralo en el banco, la billetera o la pasarela, no en un archivo o prompt que el agente pueda editar.

## Lista de chequeo rápida
- [ ] El agente no tiene acceso al correo/SMS de verificación
- [ ] Aprobación humana por encima de un monto
- [ ] Límite configurado fuera del alcance del agente
- [ ] Revisas el registro de pagos cada semana
- [ ] Mira también el recurso **PERMISOS** (accesos que nunca le doy a un agente)

## Fuentes
- Paper (arXiv): https://arxiv.org/abs/2610.35835
- CoinDesk: https://www.coindesk.com/tech/2026/11/01/ai-agents-bypassed-crypto-spending-limits-without-human-approval-researchers-find-in-a-new-test
- Prototipo open source de aprobación (Countersign): https://github.com/I-HITL/countersign

---
¿Quieres revisar los permisos de tus agentes? Escríbeme por DM **@briananderson.ai**.
