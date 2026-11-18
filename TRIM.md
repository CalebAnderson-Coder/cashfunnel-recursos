# TRIM: RTK, the free tool that trims what Claude Code reads after every command

Keyword: **TRIM**

> Resource for the video "A free tool cuts up to 90% of what Claude Code reads after every command." Jonathan / Ai.SystemsByJon, 18 Nov 2026.

**RTK** is the tool at [github.com/rtk-ai/rtk](https://github.com/rtk-ai/rtk). The README's line this video uses is: «Install & forget: up to 90% less command output.» It also says: «Production use is free, engine and daemon included.» The code is public on GitHub. Do not call it "open source" or "MIT": the default edition is **Apache-2.0** for the `rtk` CLI and **BUSL-1.1** (source-available) for `rtk-engine`.

The figures and commands in this page come from the README cited in the 18 Nov 2026 package (America/Caracas). If a new version changes a command or a warning, the repo wins.

## What it does

Your agent reads the output of every command it runs. Those tokens count against you. The README is careful: «Bash output is one contributor to input tokens, alongside your prompt, the system prompt and conversation history.» It is not claiming that command output is most of your bill.

**This is not "90% fewer tokens" and not "90% off your bill."** The maker's own warning: «a 90% cut in command output is not a 90% cut in cost.»

## The setup (three steps)

**1. Install it.** One command, but the command depends on your system (from the README):

```bash
brew install rtk
# or: winget install rtk-ai.rtk
# or: curl -fsSL … install.sh | sh
```

Use the install line that matches your machine. It is not the same command on every system.

**2. Run `rtk init -g`.** That installs a hook in Claude Code. The README's table lists Claude Code as `rtk init -g` (hook). «With a hook or plugin, `rtk init` installs it and compression is automatic.» Other tools may use a plugin, not a hook.

**3. Restart Claude Code.** The README: «Restart your agent. That's it: when it runs `git status`, RTK runs `rtk git status`.»

After that, according to the command table:

- Test runners (`cargo test` / `npm test` / `pytest` / `go test`): «Failures only, with their assertion; passing tests collapsed to a count.» That is not a claim about every test runner.
- `git status` / `git diff` / `git log`: «Compact status, reduced diff context, one line per commit.»

## The fine print

- **The hook only covers shell commands.** «The hook rewrites shell commands. Built-in tools such as `Read`, `Grep` and `Glob` pass through untouched out of the box.»
- **90% less command output is not 90% off your bill.**
- **My rule:** after a week, run `rtk gain`. That "after a week" is my rule, not a repo claim. The README says: «Every command RTK touches is counted on your machine.» «`rtk gain` shows what you saved.» And: «Token counts are estimated as `bytes / 4`, so the percentages are reliable and the absolute numbers are approximate.» Don't treat the count as exact. Keep it if the number holds up on your machine.

## Honest limits

- Not "90% fewer tokens," not "free forever," not "everything Claude reads."
- File reads and searches skip the hook by default.
- The license is Apache-2.0 + BUSL-1.1, not MIT.
- `rtk gain` estimates tokens as bytes / 4.

## Sources

Checked in the 18 Nov 2026 package, America/Caracas:

- https://github.com/rtk-ai/rtk
- https://raw.githubusercontent.com/rtk-ai/rtk/refs/heads/master/README.md

---
Want help installing RTK and reading your first `rtk gain` report? DM **@ai.systemsbyjon**.
