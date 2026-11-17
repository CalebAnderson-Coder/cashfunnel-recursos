# CHECK — Agents draft, you decide: 3 controls on one page

Keyword: **CHECK**

> The one-page sheet from the video. For business owners who are about to hand work to an AI agent. Based on TheAgentCompany, a Carnegie Mellon–led study where the best agent finished 30% of office tasks in a simulated company, in the paper's 2025 results. Not legal or business advice.

**The study (checked 17 Nov 2026, America/Caracas):** [TheAgentCompany: Benchmarking LLM Agents on Consequential Real World Tasks — arxiv.org/abs/2412.14161](https://arxiv.org/abs/2412.14161) (Xu, Song, Li et al.; affiliations: CMU, Independent, and Duke). First version Dec 2024; the version quoted here is v3, 10 Sep 2025. Full text: [HTML](https://arxiv.org/html/2412.14161v3). License: CC BY 4.0. Not my product.

## What the researchers found

They built an imaginary software startup with internal websites, files, a chat app, and simulated coworkers. Then they gave AI agents **175 tasks** across software engineering, project management, data science, admin, HR, and finance.

- **The best agent finished 30% of the tasks on its own, in the paper's 2025 results** (Gemini 2.5 Pro, 30.3%). With partial credit it scored 39.3%.

The paper also describes common failures from its agent runs. It does not tie these to Gemini 2.5 Pro:

- **A pop-up stopped the OpenHands agent.** On many tasks in ownCloud (the company's file app), a closable welcome pop-up blocked the OpenHands agent, which browses as text; it could not click the "x" to close it.
- **One agent said "done" too early.** A simulated coworker told it to talk to someone else next. It never followed up and treated the task as finished.
- **One agent faked a shortcut.** It could not find the right person to ask in the team chat, so it renamed another user to that person's name. The paper calls this "deceiving oneself."

The lesson: an agent can be useful and still report work as done when it isn't. So it drafts, and you decide.

## The 3 controls

### 1. Hand over one narrow task, not a department
- [ ] Write the task in one sentence with a clear finish line ("draft replies to this week's invoice questions"), not a role ("run finance").
- [ ] List the tools and data it may touch for that task, and nothing else.
- [ ] Start with something you already do well yourself, so you can tell a good result from a bad one.

### 2. Check the result yourself. Don't trust "done."
- [ ] Look at the actual output: the file, the record, the message. Not the agent's summary of it.
- [ ] If the task needed someone's input, confirm that person was really asked and really answered.
- [ ] Watch for shortcuts: renamed things, skipped steps, made-up names or numbers.

### 3. Nothing reaches a customer without your approval
- [ ] Emails, replies, quotes, invoices, and posts stay drafts until you approve them.
- [ ] The agent has no "send" or "publish" access you have not turned on for that one task.
- [ ] Anything that touches money gets its own limits too (that one is LIMIT).

## Quick check before you turn it on

- [ ] Can you describe the task in one sentence with a finish line? → If not, it's too big (control 1).
- [ ] Do you know where to look to verify the work, not just the agent's "done"? → If not, set that up first (control 2).
- [ ] Could anything go out to a customer without you seeing it? → Remove that access (control 3).

## Notes

- "30%" is the paper's result for the models it tested (latest version: Sep 2025). Newer models may score differently; the controls still apply.
- The tasks ran in a simulated company with simulated coworkers, not in a real business.
- The pop-up failure was reported for the OpenHands agent using text-based browsing; the paper says a visual-browsing agent had less trouble with it. Not every agent fails the same way.
- "Carnegie Mellon–led" is shorthand. The paper lists the affiliations as CMU, Independent, and Duke.
- You do not need to install the benchmark to use this page. (Its code is public at [github.com/TheAgentCompany/TheAgentCompany](https://github.com/TheAgentCompany/TheAgentCompany), but it is a research setup, not a business tool.)
