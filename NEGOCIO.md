# NEGOCIO — Claude para pequeñas empresas (plugin oficial de Anthropic)
*Recurso del video "Claude para pequeñas empresas" — Brian Anderson / CashFunnel*

- Repo: https://github.com/anthropics/knowledge-work-plugins/tree/main/small-business
- Página oficial: https://claude.com/marketplace/plugins/small-business
- Qué es: flujos listos para pequeños negocios en Cowork (app de escritorio de Claude) y Claude Code: facturas por cobrar (`invoice-chase`), resumen del lunes/viernes, flujo de caja, márgenes y precios, cierre de mes, campañas y contenido, CRM, quejas de clientes, revisión de contratos, publicar vacantes.
- **Todo empieza en modo aprobación:** Claude prepara el trabajo y nada se envía, publica ni paga sin tu "sí".

## Instalar (Claude Code)
```bash
claude plugin marketplace add anthropics/knowledge-work-plugins
claude plugin install small-business@knowledge-work-plugins
```
Luego ejecuta `/smb-onboard` o dile "configúrame".

## Conectores
Principales: QuickBooks, PayPal, HubSpot. Marketing: Canva, Gmail/Outlook, Calendar, Slack. Opcionales: Stripe, Square, Drive/OneDrive, DocuSign. No necesitas todos; sin conectores puedes subir una hoja o estado de cuenta.
Ojo: los flujos de impuestos están pensados para EE. UU.

## Empieza por una tarea concreta
Ej.: *"Tengo 5 facturas vencidas, prepárame recordatorios con buen tono"*. No intentes automatizar todo el primer día.
