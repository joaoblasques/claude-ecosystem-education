# Module 3 — Context Economy (Days 11–12)

**Goal:** Treat the context window as a budget you spend deliberately — and prove to yourself, with an experiment, that a lean context outperforms a stuffed one.

## Why this matters

This is the thread that ties Level 2 together. Instruction files (Module 4), progressive-disclosure skills (Module 5), connector budgets (Module 6), and subagent isolation (Module 7) are all context-economy techniques. The scarce resource in agentic work is not model intelligence — it's *attention over a finite window*.

## Concepts

### Context rot

Models don't fail at long context by hitting a wall; they degrade gradually. As a session fills with old tool outputs, dead ends, and stale instructions, the model's attention gets diluted: it starts missing rules it followed an hour ago and re-making mistakes you already corrected. That decay is **context rot**. The symptom is familiar to everyone who's run a marathon session: "it got dumber." It didn't — its window got noisier.

Telltale signs, in rough order of appearance:

- It re-asks something you established an hour ago.
- It violates a `CLAUDE.md` rule it followed all morning.
- It confuses the current task with an earlier, abandoned one.
- Responses get slower and vaguer as it drags a bloated window through every turn.

Run `/context` when you see any of these — as of mid-2026 it shows exactly what's occupying the window and how much room is left. Measuring beats guessing.

### Compaction: proactive vs. automatic

Claude Code compacts a full conversation by summarizing it and continuing from the summary.

- **Auto-compact** fires when the window is nearly full. It works, but *it* chooses what survives, at the worst possible moment — mid-task, maximum noise.
- **Proactive `/compact`** is you choosing the moment: at a natural boundary (task done, plan approved), and optionally with instructions — `/compact keep the migration plan and open bugs`. On long sessions, compact at boundaries rather than waiting for the ceiling.

Summaries are lossy either way. Compaction is a tourniquet, not a lifestyle.

!!! tip
    If you reach for `/compact` more than once or twice in a session, the session is too big — the real fix is usually splitting the task, not summarizing harder.

### /clear, fresh sessions, and subagents — three isolation tools

- **`/clear`** wipes the conversation but keeps you in place: same directory, `CLAUDE.md` reloads. Use it between unrelated tasks.
- **Fresh session per task** is the stronger habit: finish, commit, exit, start clean. Each task gets a full, quiet window. One eternal session accumulates rot; ten small sessions don't.
- **Subagents** isolate *within* a task: a subagent burns its own context window on a noisy job (searching, reading a huge log) and returns only its conclusion to your main session. You keep the answer, not the 40,000 tokens of file dumps that produced it. Module 7 goes deep.

| Tool | Kills | Keeps | Use when |
|---|---|---|---|
| `/compact` | Noise (lossily) | Session continuity | Mid-task, long session |
| `/clear` / fresh session | Everything | `CLAUDE.md`, your files | Between tasks |
| Subagent | Nothing of yours | Your whole window | Noisy step inside a task |

### Prompt caching intuition

Why does every session re-read `CLAUDE.md` without ballooning cost? Because providers cache the *unchanging prefix* of the context — system prompt, instruction files, early conversation — and reprocessing a cached prefix costs a fraction of fresh tokens (roughly 10% on Claude's API). Two practical consequences: stable, front-loaded instructions are cheap; and churning your context (editing early content, reordering) invalidates the cache and gets expensive. Yet another argument for a stable `CLAUDE.md` and append-only sessions.

## Resources

- [Manage Claude's context](https://code.claude.com/docs/en/costs) and the `/compact`, `/clear`, `/context` entries in the [CLI reference](https://code.claude.com/docs/en/interactive-mode) — official docs.
- [Effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) — Anthropic engineering; the canonical treatment of context rot and curation.
- [Prompt caching](https://docs.claude.com/en/docs/build-with-claude/prompt-caching) — official API docs; skim for the pricing intuition, skip the implementation detail.

## Build — ship something

**Day 11 — The context-rot experiment.** Produce evidence, not vibes.

1. In your Module 2 project, start a session and deliberately trash the context: paste in two long irrelevant documents, run several broad "read everything" requests, meander for 20+ minutes. Check `/context` as you go.
2. At the end, ask for one precise task that depends on a rule in your `CLAUDE.md`.
3. Start a **fresh** session and ask for the identical task.
4. Compare: instruction adherence, focus, quality. Write `context-rot-experiment.md` with the setup, both outcomes, and `/context` readings. Publish it.

**Day 12 — Your context playbook.** Turn the lesson into policy.

1. Write `context-playbook.md` for your learning repo: when *you* will `/compact` (and with what keep-instructions), when `/clear`, what triggers a fresh session, what gets delegated to a subagent once you have them.
2. Add one distilled line to your project `CLAUDE.md` (e.g. "One task per session; compact at task boundaries").
3. Run one real task under the playbook and note the difference. Publish.

## Log it

```markdown
## Days 11–12 — Module 3: Context economy
- Experiment: <link> — rotted session vs fresh session, verdict in one line
- /context reading at worst point: <n% used>
- My playbook: <link> — compact when <X>, clear when <Y>, fresh session when <Z>
- One thing I'll stop doing: <one line>
```
