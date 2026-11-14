# JARVIS: OpenJarvis, un asistente local y gratis

Recurso del video sobre OpenJarvis. Brian Anderson / CashFunnel, noviembre de 2026.

**OpenJarvis** es un framework **open source (Apache 2.0)** de [Hazy Research](https://openjarvis.stanford.edu/) y el Scaling Intelligence Lab (Stanford SAIL) para un asistente **local-first**: “Personal AI, On Personal Devices.” El software es gratis. Pagas tu máquina, el disco y, si activas nube, esas APIs.

No es un Jarvis de película, ni un sustituto garantizado de ChatGPT Plus o Claude Pro (ambos, en sus planes de pago de entrada, se presentan a **20 USD al mes**; revisa las páginas oficiales el día que compares), ni algo que se instale pegando el repo en Claude Code.

La palabra clave del video es **JARVIS**, no OPENJARVIS.

## Enlaces oficiales

- **Repo:** https://github.com/open-jarvis/OpenJarvis
- **Instalación:** https://open-jarvis.github.io/OpenJarvis/getting-started/install/
- **Sitio del proyecto:** https://openjarvis.stanford.edu/
- **Paper:** https://arxiv.org/abs/2605.17172

No uses el dominio viejo `openjarvis.ai/install.sh`: las propias docs avisan problemas de TLS.

## Instalación oficial

El método canónico es el one-liner de la guía de instalación, o el instalador de escritorio en Releases. Luego `jarvis` para empezar y `jarvis doctor` para ver el estado. La GUI (`jarvis gui`) pide Node.js 22+ o el paquete de escritorio.

```bash
# macOS, Linux, WSL2
curl -fsSL https://open-jarvis.github.io/OpenJarvis/install.sh | bash
```

```powershell
# Windows nativo
irm https://open-jarvis.github.io/OpenJarvis/install.ps1 | iex
```

El instalador oficial estima unos **3 minutos** en banda ancha; los modelos grandes siguen bajando en segundo plano. Revisa el script o el instalador antes de ejecutarlo. Puedes rechazar la telemetría (`--no-analytics`).

## Hardware (sin prometer que corre en cualquier PC)

- El servidor no exige un hardware especial; el cuello de botella es el modelo.
- `jarvis init` detecta GPU, CPU y RAM y recomienda el motor (llama.cpp si no hay GPU; MLX en Apple; Ollama, vLLM, etc. según el caso).
- El instalador baja un modelo de arranque `qwen3.5:2b` (~1,5 GB) y, en segundo plano, modelos del tramo de tu hardware.
- Sin GPU funciona por CPU, más lento. No es “en 3 minutos estás igual que ChatGPT”.

## Permisos y seguridad

- Es local por defecto. Si hay claves como `ANTHROPIC_API_KEY` u `OPENAI_API_KEY` en el entorno, el init puede proponer nube.
- Presets como morning-digest pueden pedir conectar correo, calendario o Drive: revisa el alcance y los permisos antes de aceptar.
- Hay agentes con shell o ejecución de código: no los instales a ciegas.
- Alinea esto con las guías [PERMISOS](PERMISOS.md) y [SEGURO](SEGURO.md).

## Costo real

El software es gratis (Apache 2.0). La electricidad, el disco y un eventual uso de APIs en la nube no lo son. El contraste útil es “gratis, sin suscripción” frente a un asistente en la nube de 20 USD al mes, no una equivalencia de calidad.

## Fuentes

Consultadas el 14-nov-2026, America/Caracas (HTTP 200, salvo donde se indica):

- Repo y licencia Apache 2.0: https://github.com/open-jarvis/OpenJarvis
- Instalación: https://open-jarvis.github.io/OpenJarvis/getting-started/install/
- Sitio: https://openjarvis.stanford.edu/
- Paper: https://arxiv.org/abs/2605.17172
- Planes de Claude: https://claude.com/pricing (HTTP 200)

Guía educativa de Brian Anderson. No es un producto de Stanford, de Hazy Research ni de Anthropic, ni una promesa de que reemplace a un asistente en la nube.
