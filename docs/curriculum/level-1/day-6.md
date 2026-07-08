# Day 6 — Claude for Thinking & Learning

**Goal:** Run the six-step learn-anything system on a real topic, and build a persistent-memory folder that makes Claude a continuous advisor instead of a goldfish.

## Why this matters

Claude's most underrated use isn't producing output — it's improving *you*: forcing active recall instead of passive re-reading, finding the blind spots you can't see from inside your own head, and holding long-running context about your goals so advice compounds across sessions. Today has two halves: a learning system you run in an hour, and a memory pattern you keep forever.

## Concepts

### The six-step learn-anything system

Built on real learning science — the Feynman method, active recall, analogy mapping — the loop goes:

1. **Feed the material.** Paste it with an explicit setup line ("Read this; I'll ask questions in a moment"). Skipping this makes later questions land without context.
2. **Teach-back.** Have Claude tutor you: the five most important concepts, each with a name, a two-sentence explanation, and a real-world example. Pick one to deepen.
3. **Active recall quiz.** Five mixed questions, explicitly "don't make them easy" — and answer **from memory, without scrolling back**. Scrolling kills the retrieval practice that makes this work.
4. **Analogy map.** "I already understand [your domain] — connect the three hardest concepts to it." Then rewrite the analogies in your own words; the rewriting is the encoding.
5. **Compress to a cheat sheet.** Condense the session into a one-page summary or infographic, dated for later review.
6. **Blind-spot check.** "What did I misunderstand? What didn't we cover? What would an expert say I'm missing? Be direct." Don't get defensive — this step is the one most people skip and the one that prevents false confidence.

### Tutor mode and the prompt review loop

Two standing habits from the same family:

- **Tutor mode**: "Teach me [topic]," then make Claude quiz you — and answer even when guessing. Passive tutor mode is worthless; wrong answers followed by "why was I wrong?" are the mechanism.
- **Prompt review loop**: paste any prompt you rely on and have Claude score it on clarity, role, format, and constraints — each out of 10 — then rewrite until everything is 9+. Numeric scores matter: they prevent polite vagueness.

### The persistent-memory pattern (financial-analyst example)

The strongest thinking-partner pattern gives Claude durable, structured context in a folder it reads every session. The canonical example is a personal financial advisor:

- **A one-pager** built via a discovery interview — Claude interviews *you*, one question at a time, about goals, constraints, beliefs in your own words, and past mistakes, pushing back on vague answers.
- **`instructions.md`** — standing rules: read the one-pager and memory before every response; update memory with dated entries; flag when a proposed action contradicts your own stated rules.
- **`memory.md`** — an append-only dated log the system maintains.

Connected through Cowork (Day 5) or a Project, this turns one-off Q&A into an advisor with accountability — it holds you to *your* rules rather than optimizing generically. The same three-file pattern works for career decisions, fitness, or business strategy.

!!! tip "Boundaries the memory pattern needs"
    Give the system an explicit disclaimer in `instructions.md` — for the finance version, something like: your job is to frame decisions, never to make them; you are not a licensed advisor. The pattern's value is accountability and framing, not delegated judgment. The same boundary line belongs in any high-stakes domain you apply it to.

### Claude Design, briefly

Claude Design (claude.ai/design, as of mid-2026) generates visual concepts — wireframes, mood boards, page designs — from described intent. Two rules: plan your brief in a regular chat *first* (Design sessions share your usage budget and burn it fast on discovery questions), and treat output as concept-grade, not production assets. Iterate with inline comments on the canvas rather than full re-prompts.

## Resources

- [Claude Help Center](https://support.claude.com) — Projects and Cowork setup used by the memory pattern (Anthropic)
- Based in part on [Learn Anything Faster With Claude](https://www.aiinpublic.com/p/learn-anything-faster-with-claude) from the AI in public newsletter — the full six-step system with prompts.
- Based in part on [How to Use Claude as a Financial Analyst](https://www.aiinpublic.com/p/how-to-use-claude-as-a-financial) from the AI in public newsletter — the one-pager interview and six monthly prompt kits.
- Based in part on [How to Use Claude Design like an Anthropic Engineer](https://www.aiinpublic.com/p/how-to-use-claude-design-like-anthropic) from the AI in public newsletter (partly paid).

## Build — ship something today

1. **Run the six-step system** on one real learning target — something you actually need this month (a tool at work, an interview topic, an industry you're entering). All six steps, including the blind-spot check. Budget: 45–60 minutes.
2. **Start a persistent-memory folder** for one domain of your life (money, career, health — your call):
    - Run the discovery interview; save the resulting one-pager as a markdown file.
    - Create `instructions.md` (read one-pager and memory first; log dated entries; flag rule violations; no preamble).
    - Create `memory.md` seeded with a dated "initial setup complete" line.
    - Connect the folder via Cowork or a Project and run one first check-in question about where you stand.

Ship: your dated cheat sheet from step 5, plus the blind-spot check's most uncomfortable finding.

## Log it

> **Level 1, Day 6 — Learning system + memory folder.**
> Topic I learned: [X] — quiz score from memory: [n/5]
> Blind spot found: [the one that stung]
> Memory folder started for: [domain] — first check-in result: [one line]
> What surprised me: [e.g., how much the no-scrolling rule changed the quiz]
