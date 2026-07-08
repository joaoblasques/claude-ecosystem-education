# Day 5 — Agentic Claude: Chrome, Excel, and Cowork

**Goal:** Run one browser or spreadsheet workflow where Claude *acts* — clicks, fills, builds — instead of just answering, with the safety settings that make that sane.

## Why this matters

Everything so far has Claude producing text and apps *for you to use*. Today Claude starts operating tools itself: navigating pages in your browser, building models inside your spreadsheet, producing files on your desktop. This is where the largest time savings live — automating one 45-minute weekly task recovers a working week per year — and also where the sharpest safety edges are.

## Concepts

### Claude in Chrome: an agent, not a sidebar

The Chrome extension (paid plans, as of mid-2026) is a browser **agent**: it clicks, scrolls, fills forms, and extracts data on pages you're logged into — not a chatbot bolted to the side. Ten workflow patterns cover most of its value: page summarization, inbox triage, competitor research, meeting prep, Drive cleanup, LinkedIn content research, job-application research, client onboarding intake, proposal research, and a weekly content-performance debrief.

Two non-negotiable safety settings:

- **"Ask before acting" stays on** until a workflow has earned trust. The agent pauses for approval before acting on new sites.
- **Never run it on financial or banking tabs.** A malicious page can embed instructions the agent might follow — prompt injection — and the blast radius on a banking tab is your money.

Start with read-only summarization on one page before attempting multi-step workflows. Complexity is earned.

### Claude in Excel: dynamic models, not hardcoded answers

The Excel add-in (Home → Add-ins → search "Claude", as of mid-2026) works *inside* your spreadsheet. Two ideas make it work:

- **Prompt with business context, not spreadsheet mechanics.** Structure prompts as **Role / Context / Output / Constraints**: "Act as a finance analyst" → the actual business situation with real metrics → the exact deliverable → what must not be touched.
- **Demand dynamic models**: formulas linked to an assumptions tab, so changing an assumption reflows the model. A single well-structured prompt can produce an assumptions tab, a linked model, and charts with zero manual formula entry.

Known limits: weak VBA support, confusion on very large or messy sheets, and occasional history resets. Never grant blanket "always allow" on a sheet with critical logic, and always review before anyone else sees the file.

### The three-layer pairing

The tools compose: **claude.ai** is the planning layer (strategy, prompts, specs), **Chrome** is the collection layer (data from the live web, behind your logins), and **Cowork** — the desktop agentic mode — is the production layer (turning collected data into formatted Excel/PowerPoint/Word deliverables and doing local file work). A research task might plan in chat, gather via Chrome, and ship as a deck via Cowork. Start Cowork small — file organization, bulk renames — before multi-app automation.

### How to earn complexity

A useful progression for any agentic tool, in order:

1. **Read-only** — summarize, explain, extract. Nothing changes.
2. **Draft-only** — the agent proposes; you approve every action.
3. **Scoped autonomy** — a specific, proven workflow runs with looser approvals.
4. **Never** — some surfaces stay off-limits permanently (financial tabs, production spreadsheets).

Most people either stall at level 1 or jump straight to 3. The middle rung is where trust is actually built.

!!! warning "Review before it counts"
    In every agentic workflow today, a human reviews the output before it touches anything external — an email, a client file, a published post. That habit is the whole trust model.

## Resources

- [Claude Help Center — Claude in Chrome](https://support.claude.com) — official extension setup and safety guidance (Anthropic)
- [Claude Help Center — Claude for Excel](https://support.claude.com) — official add-in documentation (Anthropic)
- Based in part on [Claude for Chrome — automate your workflow](https://www.aiinpublic.com/p/claude-for-chrome) from the AI in public newsletter — the 10 workflow patterns with copy-paste prompts.
- Based in part on [Excel just got a new friend](https://www.aiinpublic.com/p/excel-just-got-a-new-friend) from the AI in public newsletter — the Role/Context/Output/Constraints pattern and four model templates.

## Build — ship something today

Pick **one** track (do the other later, not today):

**Track A — Chrome.** Pick the single workflow from the ten patterns with the biggest time savings for you (inbox triage and meeting prep are common winners). With "Ask before acting" on: run it once end to end, reviewing each approval. Save the working prompt to your Level 1 Project.

**Track B — Excel.** Install the add-in. First prompt on a real (copied!) work spreadsheet: "Explain this spreadsheet to me." Then one Role/Context/Output/Constraints prompt asking for a small dynamic model — e.g., a 12-month forecast with an assumptions tab. Verify every formula links to assumptions, not hardcoded values.

Ship: the workflow output (redacted as needed) + the saved prompt.

## Log it

> **Level 1, Day 5 — Claude acted.**
> Track: [Chrome / Excel] — workflow: [name]
> Time it used to take vs today: [estimate]
> Safety posture: [what stayed on approval, what I reviewed]
> What broke / surprised me: [e.g., where the agent needed correction; the assumptions-tab pattern]
