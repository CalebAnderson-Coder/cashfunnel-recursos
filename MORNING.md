# MORNING — Stanford’s free AI assistant: the morning briefing

Keyword: **MORNING**

> A setup for business owners who want a local morning briefing from their own inbox and calendar. The software is free and open source. This is not a Stanford product sold to you, and it is not legal advice about connecting your mail.

**OpenJarvis** is a local-first assistant framework (“Personal AI, On Personal Devices”) developed at [Hazy Research](https://hazyresearch.stanford.edu/) and the [Scaling Intelligence Lab](https://scalingintelligence.stanford.edu/) at [Stanford SAIL](https://ai.stanford.edu/). License: [Apache 2.0](https://github.com/open-jarvis/OpenJarvis). Project site: [openjarvis.stanford.edu](https://openjarvis.stanford.edu/).

This page is the **morning briefing** setup. If you commented **JARVIS** on a Brian Anderson video, that Spanish guide is the general install; this one is the digest.

**Sources (checked 16 Nov 2026, America/Caracas):**

- Repo: [github.com/open-jarvis/OpenJarvis](https://github.com/open-jarvis/OpenJarvis) (15,935 stars on 16 Nov 2026, GitHub API)
- Official installer: [Installation](https://open-jarvis.github.io/OpenJarvis/getting-started/install/)
- Morning digest: [user-guide/morning-digest](https://open-jarvis.github.io/OpenJarvis/user-guide/morning-digest/)
- Presets: [Quick Start](https://open-jarvis.github.io/OpenJarvis/getting-started/quickstart/) and the repo README

## What it costs

- **The software is free** (Apache 2.0). You pay for your computer, disk, and electricity.
- **Text-only briefing: no paid voice API.** Run `jarvis digest --text-only`, or type “good morning” in the chat and read the text.
- **Spoken audio needs a Cartesia or OpenAI API key.** You pay their usage. The official digest page says: ensure `CARTESIA_API_KEY` or `OPENAI_API_KEY` is set. It does not publish a price; check those providers before you turn audio on.
- **Google needs your own developer credentials.** `jarvis connect gdrive` asks you to paste `<client_id>:<client_secret>`. The docs do **not** walk you through creating that OAuth client in Google Cloud. That is the hard part. After you paste it, the browser opens for sign-in. Official wording: one flow covers **Gmail, Calendar, Tasks, Contacts, and Drive**. Read the scopes before you accept.
- Optional extras (OpenWeatherMap, GitHub notifications, and so on) have their own keys. News RSS needs no auth.

## Setup

### 1. Run the official installer (one command)

It installs uv, a Python 3.11 venv, **Ollama**, and a starter model (`qwen3.5:2b`, about 1.5 GB). About three minutes on broadband; larger models keep downloading in the background. Review the script before you pipe it to a shell. You can decline telemetry (`--no-analytics`).

Do **not** use the older domain `openjarvis.ai/install.sh` (the docs warn about TLS issues). Use the GitHub Pages URL:

```bash
# macOS, Linux, or WSL2
curl -fsSL https://open-jarvis.github.io/OpenJarvis/install.sh | bash
```

```powershell
# Native Windows
irm https://open-jarvis.github.io/OpenJarvis/install.ps1 | iex
```

A desktop build is also on [GitHub Releases](https://github.com/open-jarvis/OpenJarvis/releases/latest). Then type `jarvis` to start, and `jarvis doctor` if something looks off.

Your computer has to run the model. The docs do not publish a RAM/GPU minimum. The official digest guide uses **`qwen3.5:9b`** (or any model you prefer), which is heavier than the 2b starter. If the briefing is weak, pull a larger model (`ollama pull qwen3.5:9b`) and set it in `~/.openjarvis/config.toml`.

### 2. Load a morning-digest preset and connect Google

After install:

```bash
# Gmail + Calendar only — best for week one
jarvis init --preset morning-digest-minimal --force
```

Other official presets: `morning-digest-mac` (Apple Silicon; email, calendar, health, news) and `morning-digest-linux`. You can also copy `configs/openjarvis/examples/morning-digest-minimal.toml` into `~/.openjarvis/config.toml`, or run `jarvis init --digest`. `--force` overwrites an existing config; skip it if you have already customized one and want to edit by hand.

Then:

```bash
jarvis connect gdrive
# Paste: <client_id>:<client_secret> — the browser opens
```

### 3. Run the first briefing as text

```bash
jarvis digest --text-only --fresh
```

Or open the chat (CLI, desktop, or browser) and type **good morning** or **morning digest**. That triggers the digest; you do not have to use the `digest` command.

## My rule for week one

Start with **text only**. Read it for a week before you rely on it, and before you add a paid voice key or more connectors (Slack, health, weather). You are pointing a local model at your inbox and calendar. If a section comes back empty, run `jarvis connect --list` and check that tokens have not expired.

Useful commands, from the official page:

```bash
jarvis digest --fresh          # new digest now (audio if a key is set)
jarvis digest                  # today's cached digest
jarvis digest --text-only      # print text, no audio
jarvis digest --history        # past digests
jarvis digest --schedule off   # disable the daily schedule
```

## Limits

- This is not a cloud assistant with a monthly “Jarvis” fee, and it is not a guaranteed substitute for ChatGPT Plus or Claude Pro.
- Connecting Google is your decision and your Google Cloud project. Start with the minimum scopes you need.
- A spoken digest will fail with no audio if neither `CARTESIA_API_KEY` nor `OPENAI_API_KEY` is set — use `--text-only` until you want that.
- Models and installers change. Re-read the official install and digest pages if a command fails.

---
For Ai.SystemsByJon. Not merged until Brian approves. Do not activate a nurture row until this page is live on `main`.
