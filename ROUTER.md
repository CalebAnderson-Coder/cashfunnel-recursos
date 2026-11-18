# ROUTER: FreeLLMAPI, a free router of listed capacity — and the fine print

Keyword: **ROUTER**

> Resource for the video "A free router lists 10.1 billion AI tokens a month." Jonathan / Ai.SystemsByJon, 18 Nov 2026.

**FreeLLMAPI** is the project at [github.com/tashfeenahmed/freellmapi](https://github.com/tashfeenahmed/freellmapi). The README headline used in the video (as of the 18 Nov 2026 package) is: «10.1 billion tokens per month. 87 free LLM providers. 1,313 free model endpoints.»

**That number is listed capacity. Not a promise.** The README says «roughly 10.1 billion tokens per month of listed free-tier capacity.» It is not a guaranteed quota, and it is not the older "7 billion" figure from other videos.

The router itself is **MIT-licensed**. The README says: «The router itself stays MIT-licensed and fully free, forever.» That does not mean everything around it is free: the same project describes a live catalog that is paid («$19/year or $49 once, lifetime» in the README cited for this package). Check the README the day you install it.

## What it does

It routes the **free tiers** of 87 providers through one OpenAI-compatible endpoint. The README's provider list includes Google, Groq, Cerebras, OpenCode Zen, Mistral, OpenRouter, and more. Not "Grok" and not "Cerberus." Not "635 models" or "34 providers" (older figures).

## The setup (three steps)

**1. Run the installer. It needs Docker.**

```bash
curl -fsSL https://freellmapi.co/install.sh | bash
```

Not "no setup" and not "one click."

**2. Add your own key from each provider you want.**  
The README: «Open http://localhost:3001, add your provider keys on the Keys page.» It does not work without accounts and keys.

**3. Set your fallback order.**  
«Reorder the Fallback Chain to taste.» When a model returns 429/5xx, it «cools that key down and retries the next model in your chain.» That is not "never stops" or "never hit a wall."

**Point Claude Code at that pool** (from the README):

```
npx freellmapi setup-claude --url http://localhost:3001 --api-key <unified-key>
```

The project also notes that `/v1/messages` «speaks Anthropic's wire format over the same router.» That is not "free Claude" and not a claim that it uses Claude's models.

## The fine print

- **No frontier models.** The README: «Stacking free tiers has real trade-offs: no frontier models, variable latency, no SLA.»
- **Personal experimentation, not production.** «This project is for personal experimentation and learning, not production.»
- **Your prompts go to the providers you turn on.** «Requests go from your machine to the upstream providers you enabled.» Don't call it private, secure, or "your data stays local."

**My rule:** use it for testing and drafts. Keep client data off it.

## Honest limits

- 10.1 billion is listed free-tier capacity, not a promise to you.
- The router is MIT; the live catalog, in the README we checked, is not free.
- You bring your own provider keys and Docker.
- No frontier models, no SLA, variable latency.
- Not for client work or production.

## Sources

Checked in the 18 Nov 2026 package, America/Caracas:

- https://github.com/tashfeenahmed/freellmapi
- https://raw.githubusercontent.com/tashfeenahmed/freellmapi/main/README.md

---
Want help standing this up for tests and drafts — with client data kept off it? DM **@ai.systemsbyjon**.
