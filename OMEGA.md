# OMEGA: Opus planea y Haiku ejecuta en Claude Code

Recurso del video sobre el patrón OMEGA. Brian Anderson / CashFunnel, noviembre de 2026.

**OMEGA no es un plugin ni un producto con ese nombre.** Es un patrón de [Claude Code](https://code.claude.com/docs): la sesión principal corre en **Claude Opus 5.5** (planea, parte el trabajo y revisa) y delega la carga repetida a **subagentes en Claude Haiku 5.5**. Al final, un subagente de verificación entra con contexto fresco. No lo confundas con **EGM**, el plugin de Google (Elephant/Goldfish): ahí un agente planea y otros revisan el plan.

En prompts de hasta 100 mil tokens, Haiku 5.5 cuesta **exactamente 1/40** de Opus 5.5. Si el prompt se pasa de 100 mil tokens, la diferencia cae a **8 veces**. El total del flujo no es siempre 40 veces más barato, porque Opus sigue planeando y revisando a su tarifa, y los subagentes cuentan para el mismo cupo del plan.

## Enlaces oficiales

- **Subagentes en Claude Code:** https://code.claude.com/docs/en/sub-agents
- **Artículo de Anthropic (subagentes y mirada nueva):** https://claude.com/resources/articles/subagents-in-claude-code
- **Precios de la API:** https://platform.claude.com/docs/en/about-claude/pricing
- **Skills de Claude Code:** https://code.claude.com/docs/en/skills
- **Planes de Claude:** https://claude.com/pricing

## Cómo armarlo (docs oficiales)

1. Deja la sesión principal en **Opus 5.5**.
2. Crea subagentes con el campo `model: haiku` o el ID `claude-haiku-5-5`. La documentación lo describe así: *“Control costs by routing tasks to faster, lower-cost models like Haiku.”*
3. Usa descripciones cortas (cuentan para el contexto). El detalle va en el system prompt del subagente, que solo carga al ejecutarse.
4. Añade un subagente de revisión o verificación, sin el historial de la conversación, para una mirada nueva.
5. Opcional, a nivel de entorno: `CLAUDE_CODE_SUBAGENT_MODEL=haiku` para rutar subagentes a Haiku. Entiende el efecto antes de copiar configs ajenas.

## Precios oficiales (consultados el 14-nov-2026, America/Caracas)

Fuente: https://platform.claude.com/docs/en/about-claude/pricing

| Modelo | Entrada | Salida | Notas |
|---|---|---|---|
| Opus 5.5 | 4 USD / MTok | 20 USD / MTok | La sesión principal planea y revisa a esta tarifa |
| Haiku 5.5, prompt ≤ 100 mil tokens | 0,10 USD / MTok | 0,50 USD / MTok | Exactamente 1/40 de Opus 5.5 |
| Haiku 5.5, prompt > 100 mil tokens | 0,50 USD / MTok | 2,50 USD / MTok | 1/8 de Opus 5.5, no 1/40 |

Revisa la página el día que lo uses: las tarifas pueden cambiar.

## Límites honestos

- Opus sigue cobrando sus tokens de plan y de revisión: el total del flujo no es siempre 40 veces más barato.
- Los subagentes cuentan para el mismo cupo del plan de Claude Code.
- No sirve igual en trabajo estrictamente secuencial, ni cuando dos agentes editan el mismo archivo, ni en tareas chicas (lo dice Anthropic).
- Distinto de EGM: ahí un agente planea y otros revisan el plan, con el plugin de Google. Aquí el ahorro viene de rutar la ejecución a Haiku.
- Auto-compacción de contexto y skills (un sistema de carpetas que se puede mejorar) son piezas oficiales de Claude Code; úsalas con la documentación, no con un “vault” de terceros.

## Fuentes

Consultadas el 14-nov-2026, America/Caracas (HTTP 200):

- Subagentes: https://code.claude.com/docs/en/sub-agents
- Artículo: https://claude.com/resources/articles/subagents-in-claude-code
- Precios: https://platform.claude.com/docs/en/about-claude/pricing
- Skills: https://code.claude.com/docs/en/skills
- Planes: https://claude.com/pricing

Guía educativa de Brian Anderson. No es un producto de Anthropic ni una promesa de un ahorro fijo en la factura. El recurso es esta guía; no un embudo de terceros.
