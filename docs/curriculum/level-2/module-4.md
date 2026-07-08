# Module 4 — CLAUDE.md & Instruction-File Design (Day 13)

**Goal:** Ship a global + project `CLAUDE.md` pair that fits an attention budget, layers correctly, and actually changes Claude's behavior — portable to other tools via `AGENTS.md`.

## Why this matters

`CLAUDE.md` is the highest-leverage file in your harness: it loads into *every* session of a project, which means every line pays rent — or charges it. A great one makes Claude feel pre-briefed; a bloated one is pure context-rot tax (Module 3) plus instructions that get ignored because they drowned each other out.

## Concepts

### The attention budget

Instructions compete for attention with the actual task. Practical ceilings that experienced users converge on: keep a `CLAUDE.md` roughly in the **80–300 line** range, and treat anything past that as a signal to cut or to move content into on-demand files. The test for every line: *would I pay for this line in every single session?* Reference material fails that test — link it ("Full schema: see `docs/schema.md`") and let agentic search fetch it when needed. That's progressive disclosure, the same principle skills are built on (Module 5).

### The file hierarchy

Instruction files layer, general to specific (as of mid-2026):

| File | Scope | Belongs there |
|---|---|---|
| `~/.claude/CLAUDE.md` | Every session, all projects | You: tone, universal habits, cross-project rules. Keep leanest of all. |
| `<project>/CLAUDE.md` | Sessions in this project (check it in) | What the project is, conventions, commands, project rules. |
| `<project>/CLAUDE.local.md` | This project, your machine only (gitignore) | Personal paths, private notes. |

Subdirectory `CLAUDE.md` files also load when Claude works in that subtree — useful in large repos, overkill in small ones.

### Writing rules that stick

- **Imperative and specific.** "Never delete files without asking" sticks; "be careful with files" doesn't.
- **Few and prioritized.** Five rules followed beat thirty diluted. If everything is IMPORTANT, nothing is.
- **Structured.** Short sections with headers (`# What this is`, `# Rules`, `# Commands`) — the model navigates structure better than prose walls.
- **Maintained by deletion.** When Claude repeats a mistake, add one line; when a line stops earning attention, cut it. Prose rules remain *suggestions* under pressure — a rule that must never break belongs in a hook (Module 8).

A shape that works, at any project size:

```markdown
# What this is
One paragraph. What the project does, for whom, current phase.

# Rules — read every session
1. Never delete or move files without asking first.
2. Show me the plan before any multi-file change.
3. Ask when unsure; don't invent conventions.

# Commands
- Preview: `make serve` · Test: `make test`

# Deeper docs (load on demand)
- Architecture: docs/architecture.md · Style guide: docs/style.md
```

### Cross-tool portability: AGENTS.md

`AGENTS.md` is the emerging vendor-neutral convention for the same idea, read by multiple coding agents. Claude Code reads `AGENTS.md` as an instruction file too (as of mid-2026), so the lazy, robust setup is one canonical file and a symlink:

```bash
ln -s CLAUDE.md AGENTS.md   # one source of truth, every tool finds it
```

Write instructions tool-agnostically (about the *project*, not about Claude) and they survive tool changes.

## Resources

- [Manage Claude's memory](https://code.claude.com/docs/en/memory) — official docs on the CLAUDE.md hierarchy and `#` quick-add.
- [Claude Code best practices](https://www.anthropic.com/engineering/claude-code-best-practices) — Anthropic engineering; see the CLAUDE.md tuning section.
- [agents.md](https://agents.md) — the open AGENTS.md convention.

## Build — ship something

**Day 13 — The instruction-file pair.**

1. **Global:** write `~/.claude/CLAUDE.md`, max ~40 lines: who you are, how you like answers, 3–5 universal rules. Copy it (secrets scrubbed) into your learning repo as `global-claude-md.md`.
2. **Project:** rewrite your Module 2 project `CLAUDE.md` against the budget: what-this-is, rules (your five, revised), key commands, links to deeper docs instead of inlined content. Target under 100 lines; count them.
3. **Portability:** add the `AGENTS.md` symlink (or a copy on filesystems without symlinks).
4. **Prove one rule sticks:** add a testable rule (e.g. "End every response with a one-line summary marked SUMMARY:"), start a fresh session, confirm behavior. Then remove the rule and note the line-count discipline: something had to justify its seat.
5. Push both files + a short `instruction-design-notes.md` on what you cut and why.

## Log it

```markdown
## Day 13 — Module 4: Instruction files
- Global CLAUDE.md: <n> lines · Project CLAUDE.md: <n> lines (<link>)
- Rule I proved sticks: <rule> — verified in fresh session: yes/no
- Biggest cut: <what I removed and where it lives now>
- AGENTS.md portability: done / n.a. because <reason>
```
