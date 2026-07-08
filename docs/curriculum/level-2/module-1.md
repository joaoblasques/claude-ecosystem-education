# Module 1 — Foundations: the Agent Loop & Harness Thinking (Day 8)

**Goal:** Explain, from a real session you ran yourself, how an agent turns a model into a worker — and why the harness around the model matters more than the model inside it.

## Why this matters

Everything in Level 2 is a variation on one loop. If you can see the loop, Claude Code stops being magic and starts being a machine you can tune. If you can't, every later module (skills, hooks, subagents, MCP) will feel like disconnected features instead of what they are: attachment points on the same loop.

## Concepts

### The agent loop

An agent is not a smarter model. It is a plain model run in a loop with four ingredients:

1. **Model** — the reasoning engine. Stateless. Forgets everything between API calls.
2. **Tools** — actions the model can request: read a file, run a command, search the web. The harness executes them and feeds results back.
3. **Memory** — everything re-supplied each turn: the conversation so far, instruction files like `CLAUDE.md`, tool results.
4. **Orchestration** — the code that runs the cycle: send context → model responds (text or a tool call) → execute the tool → append the result → repeat until done.

In pseudocode, the entire architecture fits in a few lines:

```text
context = instructions + task
loop:
    response = model(context)
    if response is an answer:      -> done
    if response is a tool call:    -> run tool, append result to context
```

That cycle — *gather context, take action, verify, repeat* — is the whole trick. Claude Code is a well-built loop around the same model you used in Level 1's chat window.

!!! tip "Chat vs. agent, in one line"
    In chat, *you* are the loop — you run the searches, paste the results, decide the next step. An agent is that job, automated. Nothing about the model changed; your role did.

### The "harness > model" thesis

Two people on the identical model get wildly different results. The difference is the harness: what instructions load at start, which tools are available, what rules are enforced, how work is verified, how context is spent. Model upgrades arrive for everyone at once; a good harness is a private, compounding advantage. This course therefore spends thirteen days on the harness and zero days waiting for a better model.

### Agentic search vs. RAG indexing

Classic RAG pipelines chunk your documents, embed them into a vector database, and retrieve "similar" chunks at question time. Claude Code does none of that. It searches the way a developer does: `grep` for a term, list a directory, open a promising file, follow the trail — deciding *what to look for next* based on what it just found.

- **RAG index:** fast at scale, but needs building and re-syncing, and retrieval is similarity, not reasoning. Stale index = confident wrong answers.
- **Agentic search:** slower per query, but zero setup, always current, and each step is a reasoning step. The model can notice "this config imports from `./legacy/`" and go look — no embedding of `./legacy/` required.

This is why Claude Code needs no vector DB, and it's harness thinking in miniature: better *process* around the model beat better *infrastructure* under it.

### Three misconceptions to drop now

- **"Agents are a different kind of AI."** No — same model, plus a loop. Everything you learned about prompting in Level 1 still applies inside every turn.
- **"More autonomy is always better."** Autonomy is a dial, not a virtue. Modules 2 and 8 are largely about *constraining* the loop so you can trust it.
- **"I need to index my documents first."** For working sets that fit agentic search — a repo, a notes vault, a docs folder — you don't. Start with zero infrastructure and add it only when search demonstrably fails.

## Resources

- [Claude Code overview](https://code.claude.com/docs/en/overview) — official docs; skim the "How it works" section.
- [Building agents with the Claude Agent SDK](https://docs.claude.com/en/api/agent-sdk/overview) — official; the loop described from the builder's side.
- [Claude Code best practices](https://www.anthropic.com/engineering/claude-code-best-practices) — Anthropic engineering blog; you'll return to this all level.
- Anthropic's engineering post on [effective context engineering for AI agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) — background for Module 3's thread, introduced here.

## Build — ship something

**Day 8 — Trace the loop.** Produce an annotated agent-loop trace and publish it.

1. Install Claude Code (full setup is Module 2; today the default install is enough — see the [quickstart](https://code.claude.com/docs/en/quickstart)).
2. Clone any small open-source repo you have **never seen** (a few hundred files max).
3. Start `claude` in it and ask one honest question, e.g. *"Where is user input validated, and what happens on invalid input?"*
4. Watch it work. For each step, note in a file: what tool did it call? why that one? what did the result change about its next move?
5. Write `agent-loop-trace.md` in your learning repo: the question, 5–10 annotated steps mapped to the four ingredients (model / tools / memory / orchestration), and a closing paragraph on why no vector index was needed.
6. Push it public.

!!! tip
    If the session finishes too fast to observe, ask a harder question. The point is to catch the loop *deciding*, not to get the answer.

## Log it

```markdown
## Day 8 — Module 1: The agent loop
- Repo I explored: <link>
- Question I asked: <one line>
- Loop steps observed: <n> (trace: <link to agent-loop-trace.md>)
- Sharpest observation: <one sentence — where the loop surprised me>
- Harness > model, in my own words: <one sentence>
```
