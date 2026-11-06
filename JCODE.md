# JCODE — agente de coding open source (harness en Rust)
*Recurso del video sobre JCode — Brian Anderson / CashFunnel*

Guía corta para probar **JCode** (harness de agentes de coding escrito en Rust). **No es nuestro producto**: es open source de terceros. Tú decides si lo instalas y con qué modelos/APIs.

## Qué es
- Repo: https://github.com/1jehuang/jcode  
- Sitio: https://jcode.sh  
- Licencia: **MIT** (revisa el LICENSE del repo).  
- Idea: un *harness* (capa entre tú y el modelo) pensado para muchas sesiones en paralelo, memoria y coordinación tipo swarm, con footprint bajo.

## Antes de instalar (sé honesto contigo)
- [ ] Tienes terminal (macOS/Linux; Windows según docs del repo)
- [ ] Sabes que **el modelo** (Claude, GPT, Gemini, local, etc.) **lo pagas tú** o lo corres local — JCode no incluye tokens infinitos
- [ ] No pegues API keys en chats públicos ni en repos
- [ ] Lee PERMISOS / SEGURO si vas a darle acceso a archivos o red: https://github.com/CalebAnderson-Coder/cashfunnel-recursos/blob/main/PERMISOS.md

## Instalación (punto de partida oficial)
1. Abre https://jcode.sh y/o el README de https://github.com/1jehuang/jcode
2. Sigue el install oficial (ejemplo documentado por el proyecto):
```bash
curl -fsSL https://jcode.sh/install | bash
```
3. Revisa en el README: providers, OAuth, modelos locales (Ollama/LM Studio), MCP y límites.
4. Prueba **una** tarea chica en un repo de prueba (no en producción el día 1).

## Primera prueba (15 minutos)
```
1) Abre un repo de prueba.
2) Pide a JCode un cambio mínimo (typo, test, README).
3) Revisa el diff tú mismo antes de commit.
4) Si usas swarm/multi-agente: un agente coordina, otros ejecutan — vigila conflictos de archivos.
```

## Lo que el video NO promete
- Las cifras de velocidad/memoria del video son las que afirma el marketing del producto/creador; **verifica** en el repo/benchmarks oficiales antes de decidir.
- "Gratis" = el harness open source. Los tokens, GPU cloud y planes de Cursor/Claude/Codex son aparte.
- No garantizamos resultados de negocio ni que reemplace tu stack actual.

## Si solo quieres el link
Repo: https://github.com/1jehuang/jcode · Docs/install: https://jcode.sh

---
¿Quieres que te armemos un flujo seguro con tu stack? DM **@briananderson.ai**.
