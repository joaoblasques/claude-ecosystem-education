# Level 2 — Claude Code & the Harness (Days 8–21)

Level 1 taught you to work *with* Claude in a chat window. Level 2 teaches you to work *through* Claude Code in a terminal — and, more importantly, to think in terms of the **harness**: the configuration, memory, rules, and orchestration wrapped around the model. The model is rented; the harness is yours. It compounds.

By the end of Level 2 you will run Claude Code confidently, manage its context like a budget, and have a working personal harness: a tuned `CLAUDE.md`, at least one skill, one hook, one subagent, an MCP decision framework, and a weekly self-improving loop for a real project of yours.

## Prerequisites

- Completed **Level 1** (or equivalent: comfortable prompting Claude, understand tokens and context windows at a conceptual level).
- Willing to use a terminal. You do **not** need to be a programmer — every exercise is doable with plain-English files and copy-paste commands.
- A [Claude subscription](https://claude.com/pricing) that includes Claude Code, plus a free [GitHub](https://github.com) account for publishing your artifacts.

!!! tip "Learn in public"
    Every module ends with a **Build** (a real artifact pushed to your public learning repo) and a **Log it** entry. The artifacts are the curriculum. If you skip the builds, you did not take the course.

## Modules

| Module | Days | Topic | You ship |
|---|---|---|---|
| [Module 1](module-1.md) | 8 | The agent loop & harness thinking | An annotated agent-loop trace from a real session |
| [Module 2](module-2.md) | 9–10 | Claude Code core workflow | A project scaffold: folder structure + first `CLAUDE.md` + workflow cheat sheet |
| [Module 3](module-3.md) | 11–12 | Context economy | A context-rot experiment write-up + a personal context playbook |
| [Module 4](module-4.md) | 13 | CLAUDE.md & instruction-file design | A tuned global + project `CLAUDE.md` pair (with `AGENTS.md` portability) |
| [Module 5](module-5.md) | 14–15 | Agent Skills (author side) | A working skill of your own, tested and published |
| [Module 6](module-6.md) | 16–17 | MCP & connectors | A connector audit + one deliberate MCP decision (connect or script) |
| [Module 7](module-7.md) | 18–19 | Subagents, orchestration & the Agent SDK | A read-only reviewer subagent + a fan-out orchestration run |
| [Module 8](module-8.md) | 20–21 | Extending the loop | A safety hook + the capstone: a weekly self-improving loop |

## How the level is structured

Three threads run through all eight modules:

1. **The loop.** Module 1 gives you the mental model — model + tools + memory + orchestration — and every later module adds one layer to it.
2. **Context economy.** Module 3 introduces context as the scarce resource. Modules 4–7 are, at bottom, all context-economy techniques: instruction files, progressive disclosure, connector budgets, subagent isolation.
3. **The harness you keep.** Each build adds a permanent piece to your own setup. The capstone in Module 8 wires them together into a loop that improves itself weekly.

## Where this leads: Level 3 (Builder)

Level 2 makes you a *power operator* of the harness. Level 3 makes you a **builder**: using the Agent SDK to ship your own agents, building MCP servers others can use, and designing multi-agent systems for problems beyond coding. Module 7's Agent SDK preview and Module 8's capstone loop are the on-ramp — arrive at Level 3 with a working loop and you'll spend it productizing, not orienting.
