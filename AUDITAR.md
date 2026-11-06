# AUDITAR — 5 cosas que reviso antes de conectar un agente
*Recurso del video GPT-6 Cyber — Brian Anderson / CashFunnel*

OpenAI lanzó GPT-6 Cyber (5 nov 2026): 81 vulnerabilidades high-severity en Firefox y 948 exploits de privilege escalation en Linux. Fuentes: https://openai.com/index/introducing-gpt-6-cyber y https://openai.com/index/a-thousand-fewer-paths-to-root/

## Lista (márcalo tú)

1. **Correo de códigos y 2FA** — nunca darle al agente la bandeja donde llegan los códigos de acceso (banco, Google, WhatsApp Business).
2. **Dinero sin techo** — si el agente puede pagar, transferir o emitir facturas, pon un límite bajo y aprobación humana para cualquier monto por encima.
3. **Chatbot / WhatsApp del negocio** — revisa qué datos del cliente puede leer y escribir; bloquea borrar conversaciones y exportar la base completa.
4. **Web y panel admin** — actualizaciones al día (CMS, PHP, plugins); un panel admin expuesto es una puerta, con o sin IA.
5. **Logs y “quién hizo qué”** — cada acción del agente debe quedar registrada (qué tocó, cuándo, con qué resultado) para poder deshacer y auditar.

## Extra
Un agente con acceso a todo es una puerta. Dale solo el acceso de la tarea. Lee también **PERMISOS** y **SEGURO** en el índice de recursos.
