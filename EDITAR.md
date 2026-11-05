# EDITAR — Kit para que Claude edite tus videos (y aprenda de tus notas)
*Recurso del video "Enseñé a Claude a editar mis videos" — Brian Anderson / CashFunnel (5-nov-2026)*

El kit gratis de Nate Herk (**Herk Edit Kit**) para **Claude Code / Codex**. Grabas. El agente corta silencios, captions, B-roll, motion y SFX. Tú das notas en castellano; cada nota queda escrita en un **skill** para no repetirla.

- Repo: https://github.com/nateherkai/herk-edit-kit
- Playbook: https://github.com/nateherkai/herk-edit-kit/blob/main/docs/EDITING-PLAYBOOK.md

## Lo que necesitas
- **Claude Code** o **Codex** (plan de pago; el kit es gratis).
- Node.js **22+**, Git, FFmpeg (+ ffprobe), Chrome/Chromium.
- Tu grabación (MP4/MOV). Transcripción: Whisper local o ElevenLabs Scribe (opcional, de pago).

## Montarlo
```bash
git clone https://github.com/nateherkai/herk-edit-kit.git
cd herk-edit-kit
npm ci
npm run setup
npm test
```
Abre esa carpeta en Claude Code / Codex.

## Primera edición (prompt)
```
Usa edit-video (o short-form-edit) con mi grabación en [ruta].
Corta silencios y errores, captions legibles, B-roll que se mueva (nada fijo),
SFX suaves (taps/clicks/papel, no láseres), y chequea lip-sync contra el crudo.
Entrégame un draft revisado. Cada nota que te dé, escríbela en el skill.
```

## El loop (esto es lo importante)
1. El agente edita y te deja un draft.
2. Tú dices qué no te gusta en plain words ("no se lee ese caption", "ese plano no se mueve", "esos SFX suenan baratos").
3. Él **arregla** y **guarda la regla en un skill**.
4. La próxima vez no lo repites.

## Reglas típicas que el kit aprende (como en el video)
- Captions: medir píxeles detrás del texto → caja oscura legible.
- B-roll: si es still, se rompe el build → video con IA o footage real.
- SFX: taps/clicks/papel; evitar láseres/zaps baratos.
- Sync: chequear cada corte contra el footage crudo antes de que lo veas.
- Cada nota → skill permanente.

## Ojo
- El kit es gratis; **gastas créditos** de tu plan Claude/Codex (y de ElevenLabs/Kie si los usas).
- HyperFrames/render puede tardar; empieza con `npm run demo`.
- No es Premiere: es agente + skills + HTML/GSAP → MP4.

---
¿Quieres que te lo armemos con tus clips? Escríbeme por DM **@briananderson.ai**.
