# SKILLS — Marketing Skills para tu agente de IA
*Recurso del video "Tu agente puede trabajar con un método de marketing" — Brian Anderson / CashFunnel*

## El repositorio
**Marketing Skills for AI Agents** (gratis, open source): skills para estrategia de contenido, copywriting, CRO, SEO, investigación de clientes, emails, precios y más. Funciona con Claude Code, Codex, Cursor, Windsurf y cualquier agente que soporte Agent Skills.
- Repo: https://github.com/coreyhaines31/marketingskills

Algunos skills que trae: `content-strategy`, `copywriting`, `copy-editing`, `customer-research`, `cro`, `seo-audit`, `emails`, `lead-magnets`, `offers`, `pricing`, `social`, `marketing-plan`, `product-marketing`.

## Cómo instalarlo bien (el error del video)
Descargar un solo archivo **no** instala el skill. Cada skill es una carpeta: necesita su `SKILL.md` (instrucciones) **y** las referencias que usa.
- Opción rápida: `npx skills add https://github.com/coreyhaines31/marketingskills`
- Manual: `git clone https://github.com/coreyhaines31/marketingskills.git` y copia la carpeta completa del skill a `.claude/skills/` (o la carpeta de skills de tu agente).

## Dale contexto de tu negocio primero
Varios skills buscan un archivo de contexto (`product-marketing.md`). Crea uno con:
1. **Negocio:** qué vendes y a quién.
2. **Cliente ideal:** problema, objeciones, palabras que usa.
3. **Oferta:** precio, diferencial, garantía.
4. **Objetivo:** tráfico, leads o ventas.

## Prueba
Pídele: *"Usa content-strategy y dame 4 pilares de contenido y un calendario de 2 semanas para mi negocio"*. Recibirás un borrador con pilares y calendario.
**Tú revisas antes de publicar.** Es marketing asistido, no automático a ciegas.

---
¿Quieres que lo configuremos para tu negocio? Escríbeme por DM **@briananderson.ai**.
