# CAPTURE — Reverse API Engineer: a website's network requests into working code

Keyword: **CAPTURE**

> The setup from the video. Reverse API Engineer is an open-source tool that records the network requests a website makes while you click through it, then has an AI model write a typed API client from them, so you don't copy requests by hand. Not legal advice; you are responsible for how you use it.

**The tool (checked 17 Nov 2026, America/Caracas):** [github.com/kalil0321/reverse-api-engineer](https://github.com/kalil0321/reverse-api-engineer) · [README](https://github.com/kalil0321/reverse-api-engineer#readme) · PyPI package `reverse-api-engineer` (v0.16.0 on that date). License: MIT. Works with Claude Code, Codex, Cursor and OpenCode. Not my product, and not made by Anthropic.

## What it is

From the README, how it works:

1. You give it a website and a goal (the README's example: fetch all jobs from a company's careers page).
2. A browser visits the site, driven by you or by an AI agent.
3. The network traffic is captured to a HAR file.
4. Your configured model reads that traffic and writes a working API client (Python by default; JavaScript, TypeScript, Go and others are options).

## Cost

- **The tool:** MIT-licensed, free to install.
- **The AI model:** may not be free. The default SDK is `claude` (Claude Code). The README also lists `opencode`, `codex`, `cursor`, `copilot` and `hermes`, and says fresh OpenCode configurations default to the free `opencode/big-pickle` model.
- The README doesn't publish prices. Check your own model plan before running it a lot.

## The setup (manual mode: you drive the browser)

Needs Python 3.11+ on Linux, Apple Silicon macOS, or 64-bit Windows.

### 1. Install it
```bash
uv tool install "reverse-api-engineer[manual]"   # or: pip install "reverse-api-engineer[manual]"
playwright install chromium
```
Manual mode needs the `[manual]` extra and Chromium. Optional: let your coding agent drive it with `npx skills add kalil0321/reverse-api-engineer`.

### 2. Type what you want, then click through the site
```bash
reverse-api-engineer
> fetch all jobs from <company>'s public careers page
```
- [ ] Switch to `manual` mode with **Shift+Tab** (the mode table says: "You drive the browser; AI generates the client from captured traffic.").
- [ ] A browser opens. Navigate, interact, close it when done. The network requests are saved to a HAR file.

### 3. The AI reads the file and writes the client
- [ ] Your client lands in `./scripts/<name>/` (e.g. `api_client.py`, `README.md`, `example_usage.py`), with a permanent copy in `~/.reverse-api/runs/scripts/<run_id>/`.
- [ ] To regenerate from the same capture, use `engineer <run_id>`.

## My rules

- [ ] **Public pages only, no login.** Don't capture pages behind your account or anyone else's. Note: agent mode's default provider (`chrome-mcp`) drives your real Chrome with your existing sessions and cookies; manual mode avoids that.
- [ ] **Read the code before running it.** The README says it too: generated code runs locally, so review before executing.
- [ ] **Only sites whose terms allow it.** The README has no legal or terms-of-service notice; checking is on you.
- [ ] **Keep the HAR file private.** It records the requests your browser made. Don't share or commit it.

## Limits

- Sites with aggressive bot detection may block capture or require manual interaction. The tool does not get around that, and you shouldn't try.
- The client is a first draft. Test it, and expect it to need fixes when the site changes.
- The project changes fast (last update 15 Nov 2026 when checked). Re-read the README before you install.
