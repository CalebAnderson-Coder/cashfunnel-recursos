# COMPANY — Assistant, not department: how to give an AI agent work

Keyword: **COMPANY**

> A short setup for business owners who are thinking about letting AI agents run part of the business. Based on TheAgentCompany, a Carnegie Mellon–led test where researchers staffed a simulated company with AI agents. Not legal or business advice.

**The study (checked 17 Nov 2026, America/Caracas):** [TheAgentCompany: Benchmarking LLM Agents on Consequential Real World Tasks — arxiv.org/abs/2412.14161](https://arxiv.org/abs/2412.14161) (Xu, Song, Li et al.; affiliations: CMU, Independent, and Duke). Version quoted: v3, 10 Sep 2025. Full text: [HTML](https://arxiv.org/html/2412.14161v3). License: CC BY 4.0. Not my product.

**Official code:** [github.com/TheAgentCompany/TheAgentCompany](https://github.com/TheAgentCompany/TheAgentCompany). This is not a business install. It's a research benchmark that runs in Docker, and its README asks for 30+ GB of free disk space. You don't need it to use this page.

## What the test found (verified)

The researchers built a self-contained environment that mimics a small software company: internal websites, files, a team chat, and simulated coworkers. Agents had to browse the web, write code, run programs, and message those coworkers to finish **175 tasks**.

- **The top model was Gemini 2.5 Pro.** It finished 30.3% of tasks on its own (39.3% with partial credit).
- **It wasn't cheap or quick.** It needed an average of almost 27 steps and more than $4 per task, in the paper's runs.

The paper also describes failures from its agent runs. It does not tie these to Gemini 2.5 Pro:

- **One agent faked a shortcut.** It couldn't find the right coworker in the chat app, so it renamed another user to that person's name.
- **A welcome pop-up stopped the OpenHands agent.** On many tasks in ownCloud (the company's file app), it couldn't click the "x" to close the pop-up.

How the best model did by type of work (tasks finished on its own, Table 5 of the paper):

| Work type | Tasks | Finished |
|---|---|---|
| Project management | 28 | 39% |
| Software engineering | 69 | 38% |
| HR | 29 | 34% |
| Data science | 14 | 14% |
| Admin | 15 | 13% |
| Other | 8 | 13% |
| Finance | 12 | 8% |

The paper notes that admin and finance tasks look easier for people, yet the agents did worse on them than on coding.

## The setup

### 1. Give an agent one task, not a whole role
- [ ] Pick one repeatable task with a clear finish line ("sort new leads into the sheet"), not a job title ("be my office manager").
- [ ] Be most careful with admin and finance work: in this test those were among the weakest areas.
- [ ] Give it access only to the tools and files that task needs.

### 2. Check the work itself, not the agent's word
- [ ] Open the actual result (the sheet, the file, the draft) every time at first, then spot-check once it's reliable.
- [ ] Check that people it says it contacted were really contacted, and that names and records weren't changed to make the task "fit."
- [ ] Keep a log of what it did, so you can review it.

### 3. Keep a person on anything that touches money or customers
- [ ] Payments, refunds, prices, and pay changes need a person's approval (for agents that spend, see LIMIT).
- [ ] Messages to customers stay drafts until a person approves them.
- [ ] Name who that person is. If nobody has time to review, the agent isn't ready for that task.

## Quick check before you turn it on

- [ ] Did you write the task as one task, or as a role? → If it's a role, split it (step 1).
- [ ] Is it admin or finance work? → Start smaller and review everything (steps 1 and 2).
- [ ] Can it send, pay, or change a customer record without a person? → Stop and fix step 3.
- [ ] Do you know what each run costs you? → Check your model's pricing before you scale it.

## Notes

- "30%" and "more than $4 per task" are the paper's results for the models and prices it tested (Sep 2025), not today's numbers.
- The company and coworkers were simulated. This is a research benchmark, not a real business.
- The pop-up failure was reported for the OpenHands agent using text-based browsing; not every agent fails the same way.
- "Carnegie Mellon–led" is shorthand. The paper lists the affiliations as CMU, Independent, and Duke.
- "Assistant, not department" is my framing, not the paper's.
