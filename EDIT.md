# EDIT — Turn Claude into a video editor with two free tools

Keyword: **EDIT**

> A first rough cut of a talking-head video, on your machine. Claude transcribes your footage, cuts the long pauses, and renders a draft. You watch it and type what to change. You approve the final cut.

This is **not EDITAR**. EDITAR is Brian Anderson’s Spanish guide to a different kit (Herk Edit Kit). This setup is Claude Code plus **FFmpeg** and **faster-whisper**.

**Sources (checked 16 Nov 2026, America/Caracas):**

- Claude Desktop / Code tab: [claude.com/download](https://claude.com/download), [Code tab docs](https://code.claude.com/docs/en/desktop)
- FFmpeg (LGPL 2.1 or later; some optional parts GPL): [ffmpeg.org/about.html](https://ffmpeg.org/about.html), [legal](https://ffmpeg.org/legal.html)
- faster-whisper, MIT, word-level timestamps, Python 3.9+: [github.com/SYSTRAN/faster-whisper](https://github.com/SYSTRAN/faster-whisper)
- Claude pricing: [claude.com/pricing](https://claude.com/pricing)
- Test run (15 Nov 2026, Windows 11, terminal — see limits below)

## What it costs

- **FFmpeg:** free (LGPL 2.1 or later). Not “no license at all”: optional parts can be GPL.
- **faster-whisper:** free (MIT). It is SYSTRAN’s project, not OpenAI’s, though it runs Whisper models.
- **Python 3.9 or newer:** free. This is a third install. The video says “two open-source tools”; Python is the runtime faster-whisper needs.
- **Claude Code is not on the Free plan.** Pro is **$20 a month** if billed monthly, or **$17 a month** if billed yearly ($200 up front). Check [claude.com/pricing](https://claude.com/pricing) before you pay; prices change.

## What you get (and what you don’t)

A draft with long pauses cut. It does **not**, in this setup, add captions, zooms, music, or effects. Those were not tested.

## Setup (three installs, once)

1. Install the Claude desktop app: [claude.com/download](https://claude.com/download). Sign in and open the **Code** tab. Official wording: “In the Claude Desktop app, Claude Code is the Code tab.”
2. Make a folder, for example `video-edit`, with a `raw` folder inside. Put **one short clip** in `raw`. In the Code tab, click the project folder control (next to the environment selector) and pick `video-edit`. Work on a **copy** of your footage, never your only original.
3. Paste this to Claude, and keep it in a mode that **asks before it runs commands**:

> Help me install Python 3.9 or newer, FFmpeg, and faster-whisper on this computer. Check what is already installed first. Ask me before you run each install command.

What we used on **Windows 11**: Python 3.11.9, FFmpeg 8.0.1 (winget package `Gyan.FFmpeg`), faster-whisper 1.2.1 (`pip install faster-whisper`). **We did not test on a Mac**, and we did not test a from-scratch install driven only by Claude.

## First draft

Paste this to Claude:

> Transcribe the clip in `raw` with faster-whisper, with word timestamps (`word_timestamps=True`). Save the transcript. Then cut every pause longer than 0.45 seconds and render a draft to `output/draft.mp4` with FFmpeg. Tell me how many cuts you made and the before and after length.

Watch `output/draft.mp4` all the way through. The transcript can miss words, and a cut can clip the start of a sentence.

## Change the draft

Type what you want, for example:

> Tighter. Cut every pause longer than 0.3 seconds and render `draft_v2.mp4`.

Claude runs the tools. You approve the final cut.

## What happened in our test

Run on 15 Nov 2026, on a laptop CPU, in the **terminal** (not in the Code tab), with clips in **Spanish**:

- Clip: 77 seconds, vertical phone video, one person talking.
- Transcript: 174 words with a timestamp on each, in 28 seconds (small “base” model).
- Draft 1: 13 segments kept, 77.1 s down to 65.3 s.
- Draft 2 after one typed change (pauses longer than 0.30 s): 16 segments, 64.6 s.

One clip is one test, not a promise. Your result depends on your footage. We verified duration, tracks, and that the mp4 files decode; we did not do a formal picture-quality review in the Code tab.

## Your controls

- Keep Claude in the mode that asks before it runs commands.
- Never point it at your only original.
- Watch the whole draft before you post.
- You approve the final cut.

---
For Ai.SystemsByJon. Not merged until Brian approves. Do not activate a nurture row until this page is live on `main`.
