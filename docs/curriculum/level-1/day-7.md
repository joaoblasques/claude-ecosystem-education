# Day 7 — Capstone: Stop Prompting, Build Loops

**Goal:** Assemble everything from Days 1–6 into one installed, reusable loop — and run it three times on real work.

## Why this matters

A week of features is worthless if you go back to one-off prompting on Monday. The graduation move of Level 1 is the **loop**: a permanent system with memory, a trigger, and verification, where Claude is the engine and you are the editor. Loops are also the honest answer to a real problem — a single Claude session left to its own devices fails in predictable ways, and loop architecture is what corrects for them.

## Concepts

### Why solo prompting fails

Three documented failure modes of relying on one session, one prompt at a time:

- **Agentic laziness** — the model does the minimum plausible version of the task and declares victory.
- **Self-preferential bias** — asked to judge its own output, it grades generously. The author's short version: a session "marking its own homework."
- **Goal drift** — over a long session, the original objective erodes into whatever the recent messages emphasize.

None of these are fixed by better prompting *within* the session. They're fixed by structure *around* it.

### Loop architecture: five components

1. **Memory file** — a markdown file holding standing context and gold-standard examples, so every run starts warm (your Day 6 pattern, generalized).
2. **Trigger prompt** — one short, fixed activation phrase mapped to the full workflow, so invocation is consistent: `Brief: [input]`, not a fresh essay each time.
3. **Adversarial verification** — a *separate* session or skill whose only job is to attack the output. This is the structural antidote to self-preferential bias.
4. **Prompt library** — your proven prompts stored (Project Knowledge, a doc), versioned as they improve.
5. **Weekly review** — a scheduled pass over the week's outputs: what worked, what drifted, what the memory file should learn.

### The six loop patterns

Ways to wire multiple Claude passes together: **Fan-Out/Synthesize** (parallel drafts, then merge), **Adversarial Verification** (generator vs critic), **Tournament** (many candidates, scored, cut), **Loop-Until-Done** (iterate against a fixed bar), **Generate/Filter** (volume then triage), and **Deep Verification** (multi-pass checking for high-stakes output). You only need one pattern today; knowing the menu keeps you from reinventing it later.

### Seven ready-made loops

Proven no-code loops built as Skills inside a Project — each one input → process → scored/structured output → fixed trigger phrase: an AI news brief (signal/noise filtering), an SEO content editor, a viral hook factory (generate–score–cut), a second-brain capture formatter, a personal finance reviewer, a business idea validator (GO/WAIT/DROP), and a freelance proposal writer. The build mechanics are exactly your Day 3 skill plus a Day 1 Project plus a gold-standard context file — the "double-layer" of instructions + trigger + exemplar.

!!! warning "The standing rule"
    "A loop running unattended is a loop making mistakes unattended." The finance loop in the source post once recommended canceling a subscription tied to active client work. Loops handle the repetitive parts; you remain the editor of every output. Always.

### How Days 1–6 become the loop

Nothing today is new machinery. The Project (Day 1) is the container; the Skill (Day 3) is the trigger; connected data (Day 4) and agentic tools (Day 5) are optional inputs; the memory-file discipline (Day 6) is the persistence layer. The only genuinely new idea is the adversarial pass — and that exists because of the failure modes above.

## Resources

- [Claude Help Center — Projects and Skills](https://support.claude.com) — the primitives loops are built from (Anthropic)
- Based in part on [Stop Prompting Claude. Build Loops Instead.](https://www.aiinpublic.com/p/stop-prompting-claude-build-loops) from the AI in public newsletter — failure modes, architecture, the six patterns, five templates.
- Based in part on [7 Advanced Claude Loops That Run Your Work Autonomously](https://www.aiinpublic.com/p/7-advanced-claude-loops-that-run) from the AI in public newsletter — full markdown templates for all seven loops.

## Build — ship your first loop

Pick **one** loop matching your most painful recurring task — adapt a ready-made one or design your own. Then:

1. **Memory file:** create a `.md` context file with your best past example of the output ("this is the gold standard"). Upload it to your Level 1 Project's knowledge.
2. **Trigger:** build the workflow as a Skill (Day 3 mechanics) with a short fixed trigger phrase and a precise description with exclusions.
3. **Verification:** create a second, adversarial prompt — "attack this output: what's wrong, missing, or lazy about it?" — and make running it part of the loop.
4. **Run it three times** on three real inputs. After the best run, save that output as the new gold-standard in the memory file, and run once more to confirm it improved.
5. **Schedule the weekly review:** a recurring 10-minute calendar block (you have Calendar connected from Day 4 — have Claude propose it).
6. **Write the operating note:** one line in the memory file stating what the loop must never do without your review.

Ship: the loop's name, trigger phrase, and one before/after output pair.

## Log it

> **Level 1, Day 7 — First loop shipped. Capstone done.**
> My loop: [name] — trigger: `[phrase]`
> Three runs: [what improved between run 1 and run 3]
> What the adversarial pass caught: [one concrete catch]
> What broke / surprised me: [e.g., the gold-standard file changing output quality]
> Level 1 complete — next: Level 2, where these same ideas move into the terminal.
