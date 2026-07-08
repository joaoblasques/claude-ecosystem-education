# Module 7 — Subagents, Orchestration & the Agent SDK (Days 18–19)

**Goal:** Run work through more than one Claude — a read-only reviewer that catches what your main session can't see, and a fan-out pattern with deliberate model routing.

## Why this matters

One session has one context, one bias, and one budget. Subagents break all three limits: they isolate noisy work (Module 3's payoff), they judge work without having authored it, and they let you route cheap tasks to cheap models. This is where "operating a harness" becomes "orchestrating a team."

## Concepts

### Defining subagents

A subagent is a markdown file in `.claude/agents/` (project) or `~/.claude/agents/` (global): YAML frontmatter plus a system prompt. It runs in its **own fresh context** and reports back only its conclusion.

```markdown
---
name: reviewer
description: Read-only quality reviewer. Use after completing any
  substantial piece of work, before delivery.
tools: Read, Grep, Glob
model: haiku
---

You are a skeptical reviewer. You did not write this work and owe it
no loyalty. Check it against the stated requirements. Report: what is
wrong, what is missing, what is unclear — most severe first. Never
propose that you fix anything yourself; you cannot edit files.
```

### Read-only reviewers: zero session bias

Your main session *believes in* its own work — it wrote it, and its context is saturated with its own reasoning. A fresh subagent reading the result cold has none of that. Two design rules make this work:

- **Fresh context is the feature.** The reviewer sees the artifact and the requirements, not the three hours of rationalization behind them.
- **Keep reviewers read-only** — grant `Read`/`Grep`/`Glob`, never `Edit` or `Write`. The community rule of thumb: "if it can edit, it becomes part of the problem." A reviewer that fixes things starts defending its fixes; you've just built a second biased author.

### Model routing economics

Frontier models plan; cheap models grep. The pattern: an expensive **orchestrator** (your main session) does the reasoning and delegates bounded, mechanical work — searching, summarizing, checklist review — to subagents pinned to cheaper models via the `model:` field. You spend premium tokens on judgment and pennies on legwork. Wrong-way routing (cheap orchestrator, expensive workers) fails: orchestration *is* the hard part.

### Three orchestration patterns

1. **Fan-out / synthesize** — split independent questions across parallel subagents; orchestrator merges conclusions. For breadth: audits, research sweeps, multi-file surveys.
2. **Adversarial verification** — one agent produces, a second attacks it against the spec, producer revises. For quality gates before anything ships.
3. **Tournament** — several agents attempt the same task independently; a judge (or you) picks the winner. For high-variance creative work where the first draft is rarely the best draft.

### The Agent SDK: the same harness, generalized

Everything above — the loop, tools, instruction files, subagents, hooks — is exposed programmatically as the **Claude Agent SDK**. Claude Code is one app built on it; you can build others: support triagers, research pipelines, ops bots. Nothing in the harness is coding-specific. That's Level 3's territory; today you just need to recognize that you've been learning a general architecture, not a code tool.

## Resources

- [Subagents](https://code.claude.com/docs/en/sub-agents) — official docs: file format, `tools`/`model` fields, `/agents` command.
- [Claude Agent SDK overview](https://docs.claude.com/en/api/agent-sdk/overview) — official; skim the architecture section.
- [Building agents with the Claude Agent SDK](https://www.anthropic.com/engineering/building-agents-with-the-claude-agent-sdk) — Anthropic engineering; the "beyond coding" argument.
- The fan-out / adversarial / tournament framing is used across the community; see [Stop Prompting Claude. Build Loops Instead.](https://www.aiinpublic.com/p/stop-prompting-claude-build-loops) from the AI in public newsletter for one good treatment.

## Build — ship something

**Day 18 — The read-only reviewer.**

1. Create `.claude/agents/reviewer.md` for your project, adapting the example above to *your* quality bar (pull criteria from your Module 2 rules and Module 5 skill).
2. Restrict tools to read-only; pin a cheap model.
3. Do a real piece of work in your main session, then invoke the reviewer on it. Apply what it catches; note what your own session had missed.
4. Publish the agent file + a before/after note.

**Day 19 — Fan-out with routing.**

1. Pick a breadth question about your project ("audit docs for staleness", "survey error handling across modules").
2. Have your main session fan it out to 2–3 parallel subagents on cheap models, each with a bounded slice, then synthesize their reports.
3. Write `orchestration-notes.md`: the split, what each worker returned, what synthesis added, and roughly what routing saved vs. doing it all in the main session. Publish it.

## Log it

```markdown
## Days 18–19 — Module 7: Subagents & orchestration
- Reviewer agent: <link> — caught: <best catch, one line>
- Why read-only, my words: <one sentence>
- Fan-out run: <n> workers on <model> → synthesis: <link>
- Pattern I'll reuse weekly: fan-out / adversarial / tournament, for <task>
```
