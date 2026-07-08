# Module 2 — Claude Code Core Workflow (Days 9–10)

**Goal:** Run Claude Code as a daily tool — installed, permission-configured, plan-mode-first — inside a project scaffold you built deliberately instead of by accident.

## Why this matters

Most people run Claude Code with zero setup, then blame the model when it forgets their rules ten minutes in. The fix is configuration, not prompting. This module gives you the everyday workflow plus the five-layer setup that the rest of Level 2 fills in, one layer per module.

## Concepts

### Install and first contact

Install via the official instructions at [code.claude.com](https://code.claude.com/docs/en/quickstart), then run `claude` inside a project folder. Claude Code always operates *in a directory* — that directory's files, git history, and config are its world.

### Permission modes

Claude Code asks before running commands or editing files. As of mid-2026 the practical spectrum is:

- **Default (ask):** every consequential action needs your approval. Start here.
- **Auto-accept edits:** file edits proceed; commands still ask. Fine once you trust a workflow.
- **Plan mode (Shift+Tab):** Claude may read and think but not change anything. It produces a plan you approve before execution.
- **Skip-all-permissions:** exists; don't use it until you have hooks (Module 8) as a backstop.

The rule of thumb: **Shift+Tab before anything major.** Reviewing a plan costs a minute; reviewing a mess costs an afternoon. And `Esc Esc` rewinds when something goes sideways.

### The five-layer harness model

Your setup is five layers, from softest to hardest enforcement:

1. **CLAUDE.md** — the instruction manual read at session start: what the project is, your rules, your preferences (Module 4).
2. **Skills** — reusable mini-specialists auto-invoked for specific tasks (Module 5).
3. **Subagents & plugins** — fresh instances for isolated work, e.g. read-only reviewers (Module 7).
4. **MCP connectors** — external tools and data sources (Module 6).
5. **Hooks** — rules attached to events that *cannot* be ignored, unlike prose (Module 8).

A folder structure that houses all five:

```text
your-project/
├── CLAUDE.md
├── .claude/
│   ├── settings.json         # shared config: permissions, hooks
│   ├── settings.local.json   # personal overrides (gitignored)
│   ├── skills/
│   └── agents/
├── hooks/
└── src/                      # or docs/, content/ — your actual work
```

### The everyday workflow recipe

Open project folder → `claude` → **Shift+Tab** into plan mode → describe the task → approve/adjust the plan → let it execute → verify the result yourself → commit → **start a fresh session for the next task**. Two habits to install now, explained fully in Module 3: compact proactively on long sessions, and never let one session run forever.

## Resources

- [Quickstart](https://code.claude.com/docs/en/quickstart) and [common workflows](https://code.claude.com/docs/en/common-workflows) — official docs.
- [Settings & permissions](https://code.claude.com/docs/en/settings) — official reference for `settings.json` and permission modes.
- [Claude Code best practices](https://www.anthropic.com/engineering/claude-code-best-practices) — Anthropic engineering; the plan-first workflow in depth.
- Based in part on [Your Claude Code Is Broken. Here's the 5-Minute Fix](https://www.aiinpublic.com/p/your-claude-code-is-broken-heres) from the AI in public newsletter — source of the five-layer framing and folder scaffold above.

## Build — ship something

**Day 9 — Scaffold a real project.** Pick something you actually work on (code, a blog, a research folder — anything).

1. Create the folder structure above (empty `skills/` and `agents/` are fine — they're reservations for Modules 5 and 7).
2. Write a first `CLAUDE.md`: one sentence on what the project is, then **five real rules** — rules you'd give a new assistant, e.g. "Never delete a file without asking" and "Show me the plan before you act." Specific beats clever.
3. Run one small task through Claude Code in this project, plan mode first.
4. Push the scaffold (minus `settings.local.json`) to your learning repo.

**Day 10 — Write your workflow cheat sheet.** Run two more tasks end-to-end, then document what *you* actually did.

1. Task A: something read-only (e.g. "summarize this folder's structure and biggest risks").
2. Task B: something that edits files, run through plan mode with at least one plan correction from you.
3. Write `workflow.md`: your keyboard shortcuts, your permission-mode choices and why, your task recipe as a numbered list. Publish it.

## Log it

```markdown
## Days 9–10 — Module 2: Core workflow
- Project scaffolded: <link>
- My five rules: <link to CLAUDE.md>
- Plan mode saved me from: <one concrete thing, or "nothing yet — here's what I'd expect it to catch">
- Cheat sheet: <link to workflow.md>
```
