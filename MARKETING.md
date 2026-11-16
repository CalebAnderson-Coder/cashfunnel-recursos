# MARKETING — Free marketing skills for your AI agent

Keyword: **MARKETING**

> A setup for the open-source Marketing Skills collection: your agent drafts the work, you approve it. This is not a substitute for a marketing agency, and it is not legal, financial, or advertising advice.

**Marketing Skills for AI Agents** is a free, [MIT-licensed](https://github.com/coreyhaines31/marketingskills/blob/main/LICENSE) collection built by [Corey Haines](https://github.com/coreyhaines31). It works with Claude Code, OpenAI Codex, Cursor, Windsurf, and any agent that supports the [Agent Skills](https://agentskills.io) spec.

- Repo: [github.com/coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) (60,783 stars on 16 Nov 2026, GitHub API)
- Official line: “A collection of AI agent skills focused on marketing tasks.”

This is the **same toolkit** as Brian Anderson’s Spanish page **SKILLS**. If you commented SKILLS on one of his videos, use that page. This one is the English setup for this reel.

Do **not** follow the partner or `?ref=` links in the upstream README for this install. Point your agent at the repo above.

## What it costs

- **The skills are free** (MIT: “Use these however you want.”).
- **You need an AI agent to run them**, such as Claude Code. Claude Code is **not** on Anthropic’s Free plan. Pro is **$20 a month** if billed monthly, or **$17 a month** if billed yearly ($200 up front). Check [claude.com/pricing](https://claude.com/pricing); prices change.
- Partner tools mentioned in the upstream README are optional and separate. You do not need them to install or try the skills.

## What you get

It is not one skill. The “Available Skills” table in the README lists **53** skills (counted on 16 Nov 2026). The README itself does not publish an official total, so this guide says **more than fifty**.

The foundation is **`product-marketing`**. It writes down your product, your customer, and your positioning in `.agents/product-marketing.md` (product, ICP, positioning, competitors, customer language, brand voice). Official wording: “every other skill checks it first.”

Then you pick the job, for example:

- `seo-audit` — audit or diagnose SEO
- `copywriting` — write or rewrite page copy (homepage, landing, pricing, feature)
- `cold-email` — write B2B cold outbound (it drafts; it does not send)
- `pricing` — help set pricing and packaging

And **`marketing-council`**: a **simulated** board of famous marketers (the skill names Seth Godin, David Ogilvy, April Dunford, Byron Sharp, and more). They are not those people, and the skill says so. It seats dissenters on purpose (“A council that agrees is a mirror, not a board”) and ends with **one recommendation**. It must not invent quotes.

## Setup

From a folder your agent can see (your site repo, or a new `marketing/` folder):

```bash
npx skills add coreyhaines31/marketingskills -a claude-code
```

The `-a claude-code` flag matters: if you run the installer from inside an agent session without it, the CLI may write only to `.agents/skills/`, which Claude Code does not read.

Other official options, from the README: `npx skills add coreyhaines31/marketingskills` (it asks which agents you have), a Claude Code plugin (`/plugin marketplace add coreyhaines31/marketingskills` then `/plugin install marketing-skills`), Codex plugins, or a manual clone into `.agents/skills/`.

## First run — in this order

1. **Build the context file first.**

> Use the product-marketing skill. Draft `.agents/product-marketing.md` from this repo and from what I tell you about the product, the customer, and our positioning. Ask me about anything you cannot verify. I will correct the draft before we use any other skill.

2. **Then pick one job**, for example:

> Read `.agents/product-marketing.md` first. Then use the copywriting skill to rewrite the homepage. Keep every claim I already made; do not invent proof, prices, or results. Give me a draft I can edit.

Or: `seo-audit` on a URL you own, `cold-email` for a segment you describe, `pricing` as a recommendation — not “the correct price.”

3. **If you want a second opinion on a real decision:**

> Use the marketing-council skill in a council session. This is a simulation, not the real people. Ground every take in what those advisors actually wrote. Show where they disagree, then give me one recommendation. Do not invent quotes.

## My rule

It drafts. You approve. Every time. That rule is mine, not a guarantee from the repo. Nothing should go live — a homepage, an email, a price change, an ad — until you have read it.

## Limits

- The skills will not “kill” an agency, raise your rankings, or send the emails.
- Names like Ogilvy and Godin are a simulation. Do not present the output as their real opinion, and do not use their photos.
- Re-count the skill table if you need an exact number; it can change.
- Models and agent plans change. Re-read the repo README if an install command fails.

---
For Ai.SystemsByJon. Not merged until Brian approves. Do not activate a nurture row until this page is live on `main`.
