# TEAM: a free AI agency inside Claude Code

Keyword: **TEAM**

> Resource for the video "Someone put a full AI agency on GitHub, for free." Jonathan / Ai.SystemsByJon, 16 Nov 2026.

**The Agency** (`agency-agents`) is a **free, open-source** repo ([MIT license](https://github.com/msitarzewski/agency-agents/blob/main/LICENSE)) of ready-made specialist agents: SEO, ads, content, sales, web development, QA, and more. Each agent is one `.md` file with an identity, a personality, a workflow, and the deliverables it produces.

**The sources (checked 16 Nov 2026, America/Caracas):**

- Repo: [github.com/msitarzewski/agency-agents](https://github.com/msitarzewski/agency-agents) (about 169k stars as of 16 Nov 2026). README, `scripts/install.sh`, and the [Claude Code integration notes](https://github.com/msitarzewski/agency-agents/blob/main/integrations/claude-code/README.md).
- Desktop app: [agencyagents.app](https://agencyagents.app) · [downloads (releases)](https://github.com/msitarzewski/agency-agents-app/releases/latest) · [app source](https://github.com/msitarzewski/agency-agents-app) (also MIT).
- Not my product, and I'm not affiliated with the project. If a new version changes something, the site and the repo win.

## How many agents

The video says "200+". The README says "230+". As of 16 Nov 2026, the official installer (`./scripts/install.sh --list teams`) counts **283 agents across 18 divisions**, including engineering (66), specialized (59), marketing (37), game development (21), GIS (13), security (12), design (10), sales (9), testing (9), and paid media (7). The number grows with each release.

## Cost

- **The repo and the app are free** (MIT). The app needs no account and, per its site, has no telemetry.
- **You pay for the AI tool you run them in.** For Claude Code that means a paid Claude plan (Pro or higher) or Anthropic API usage. The agents are instructions; they don't ship their own model.

## Install into Claude Code

### Option 1: the desktop app (no terminal)

1. Download it from [agencyagents.app](https://agencyagents.app) or the [latest release](https://github.com/msitarzewski/agency-agents-app/releases/latest) (v0.3.2 as of 16 Nov 2026):
   - **Mac (Apple Silicon):** the `aarch64` `.dmg`. **Intel Mac:** the `x64` `.dmg`. Both signed and notarized, macOS 13+. Or: `brew install --cask msitarzewski/agency-agents/agency-agents`.
   - **Windows:** `x64-setup.exe` (or `arm64-setup.exe`). It is **not code-signed yet**, so SmartScreen shows "Windows protected your PC." Click **More info → Run anyway**. Only download it from the official links above.
   - **Linux:** `.deb`, `.rpm`, or `.AppImage`.
2. Have Claude Code installed. The app detects your tools in the **Tools** panel.
3. In **Agents**, filter by division, open an agent, and read its persona before you install it.
4. Deploy one agent, several, or a whole preset team (**Teams** panel) to **Claude Code**, globally or scoped to one project (**Projects**).
5. Open Claude Code and run `/agents` to see what got installed.

The app keeps a local ledger of what it wrote, flags files that changed, and lets you update or uninstall. It backs up existing files before it overwrites them.

### Option 2: the terminal

You need `git` and bash (on Windows: Git Bash or WSL).

```bash
git clone https://github.com/msitarzewski/agency-agents.git
cd agency-agents

# Every agent into Claude Code (~/.claude/agents/)
./scripts/install.sh --tool claude-code

# Or only the divisions you need
./scripts/install.sh --tool claude-code --division engineering,testing,sales
```

**Tip:** don't install all 283 unless you'll use them. Start with the divisions that match your work.

## How to use them

In a Claude Code session, name the agent in your request, for example: *"Use the Workflow Architect agent to…"* Claude Code hands the task to that specialist, with its process and its output format.

## 5 specialists to try today (ready prompts)

Copy a prompt, fill in the brackets, paste it into Claude Code.

**1. Workflow Architect** (`specialized/specialized-workflow-architect.md`): maps a workflow end to end, including failures and handoffs.
> Use the Workflow Architect agent. Map my [lead intake / client onboarding] process: [describe the steps today]. Give me every step, branch, failure mode, and handoff, then mark which steps an AI agent can own and which need a human sign-off.

**2. SEO Specialist** (`marketing/marketing-seo-specialist.md`): technical SEO, content, and authority.
> Use the SEO Specialist agent. Audit the technical SEO of [site URL]: titles, meta descriptions, headings, speed, indexing, and internal links. Give me the 10 fixes with the biggest impact, ranked, one line each.

**3. Ad Creative Strategist** (`paid-media/paid-media-creative-strategist.md`): Meta and Google ad copy and creative testing.
> Use the Ad Creative Strategist agent. I sell [offer] to [ideal client]. Write 5 Meta ads (primary text, headline, description) and one Google search ad with 10 headlines and 4 descriptions. Tell me which angle to test first and why.

**4. Reality Checker** (`testing/testing-reality-checker.md`): defaults to "NEEDS WORK" and asks for proof before anything ships.
> Use the Reality Checker agent. Here is the automation/feature I'm about to ship: [describe it or point to the files]. Tell me if it's production-ready. List the evidence you'd need, what's missing, and what could break with a real client.

**5. Reddit Community Builder** (`marketing/marketing-reddit-community-builder.md`): value-first community posts.
> Use the Reddit Community Builder agent. My niche is [niche]. Pick 5 subreddits where my ideal client hangs out, explain each one's rules and culture, and draft 3 value-first posts that don't read like ads.

## Honest limits

- **They're instructions, not employees.** Each agent is a well-built prompt. Quality depends on the model and the context you give it. Review everything before it reaches a client.
- **More agents isn't better.** Every installed agent is one more file Claude Code has to weigh. Install what you'll use.
- **Unsigned on Windows.** The SmartScreen warning is expected; install only from the official links.
- **The app doesn't run agents.** It installs them into your tools (Claude Code, Codex, Cursor, Gemini CLI, and others). Your AI tool does the work.
- **Don't wire them to your accounts blindly.** An agent that can post, spend, or message clients needs your rules first.

## Credits

- The Agency (`agency-agents`): [Michael Sitarzewski](https://github.com/msitarzewski) and contributors, MIT license.
- Agency Agents app: [msitarzewski/agency-agents-app](https://github.com/msitarzewski/agency-agents-app), MIT license.

---
Want help setting this up for your business? DM **@ai.systemsbyjon**.
