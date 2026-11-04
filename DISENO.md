# DISEÑO — Los 5 plugins para que Claude cree webs con mejor diseño
*Recurso del video "Cinco plugins para que Claude cree webs con mejor diseño" — Brian Anderson / CashFunnel*

Claude (o Codex/Cursor) por defecto hace webs genéricas. Estos 5 complementos le dan sistema de diseño, revisión, referencias, ojos y mockup → código. Todos son gratis.

## 1. Awesome DESIGN.md — sistemas de diseño completos
Colección de archivos `DESIGN.md` con el sistema de diseño de sitios conocidos: tipografía, espaciado, colores, botones, layout, componentes, iconografía, accesibilidad.
- Repo: https://github.com/VoltAgent/awesome-design-md
- Uso: copia el `DESIGN.md` que te guste a la raíz de tu proyecto y dile a tu agente: *"Sigue DESIGN.md en todas las páginas"*.

## 2. Web Design Guidelines (Vercel) — revisión antes de publicar
Skill oficial de Vercel que audita tu código de interfaz contra sus reglas (accesibilidad, foco, formularios, carga, rendimiento).
- Repo: https://github.com/vercel-labs/agent-skills · Reglas: https://vercel.com/design/guidelines
- Instalar: `npx skills add https://github.com/vercel-labs/agent-skills --skill web-design-guidelines`
- Uso: después del primer borrador, pide *"Audita los archivos que cambiaste con web-design-guidelines y dame los hallazgos archivo:línea antes de corregir"*.

## 3. Taste Skill — referencias visuales premium
Colección de skills para darle "gusto" al agente y alejarlo del diseño genérico de IA, con galería de ejemplos.
- Repo: https://github.com/Leonxlnx/taste-skill

## 4. Playwright CLI — el agente abre un navegador y se revisa solo
CLI de Microsoft: abre tu web, cambia el tamaño (escritorio/móvil), toma capturas y detecta lo que quedó roto.
- Repo: https://github.com/microsoft/playwright-cli
- Instalar: `npm install -g @playwright/cli@latest` y `playwright-cli install --skills`
- Ejemplo: `playwright-cli -s=mobile open http://localhost:3000 --device="iPhone 15"` → `playwright-cli -s=mobile screenshot --filename=mobile.png`

## 5. Image-to-code — mockup a código sin perder detalles
Skill (dentro de taste-skill) que primero genera/analiza la imagen del diseño y luego implementa la web igual.
- Instalar: `npx skills add https://github.com/Leonxlnx/taste-skill --skill image-to-code`

## Flujo recomendado (el del video)
1. DESIGN.md → 2. el agente construye → 3. Vercel guidelines revisa → 4. Playwright toma capturas y corrige → 5. image-to-code para secciones que tienes en mockup.
Así le pasas la web de un cliente al agente y recibes diseño, revisión y correcciones sin tocar cada pantalla.

---
¿Quieres que te lo armemos para tu negocio? Escríbeme por DM en TikTok/IG **@briananderson.ai**.
