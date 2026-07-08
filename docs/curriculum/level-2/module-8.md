# Module 8 — Extending the Loop (Days 20–21)

**Goal:** Add the enforcement layer (hooks) to your harness, then wire everything from Level 2 into a weekly self-improving loop for your own project — the capstone.

## Why this matters

Prose instructions are suggestions; under context pressure they get skipped (Module 3 proved it). Hooks are the layer that *cannot* be skipped. And a harness that only runs when you type at it is a tool; one that runs on a schedule and improves its own configuration is a system. That's the graduation line for Level 2.

## Concepts

### Hooks: rules that cannot be ignored

Hooks are shell commands your harness runs automatically on events — before a tool call (`PreToolUse`), after one (`PostToolUse`), on notifications, at session start. The critical property: they execute in the *harness*, not the model. A `CLAUDE.md` rule saying "never delete files" can be forgotten; a `PreToolUse` hook that inspects each Bash command and exits non-zero on `rm` **blocks the action itself**, every time, regardless of what the model is attending to. Configured in `.claude/settings.json`:

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          { "type": "command", "command": "python3 hooks/block_deletes.py" }
        ]
      }
    ]
  }
}
```

The hook script reads the tool call as JSON on stdin; as of mid-2026, exit code 2 blocks the action and feeds your message back to Claude. A minimal blocker is a dozen lines:

```python
import json, sys
call = json.load(sys.stdin)
cmd = call.get("tool_input", {}).get("command", "")
if "rm -rf" in cmd:
    print("Blocked: destructive delete. Ask the human.", file=sys.stderr)
    sys.exit(2)   # exit 2 = block the tool call
```

Sorting rules by layer: preferences → `CLAUDE.md`; procedures → skills; **invariants → hooks**.

### Artifacts from Claude Code

Claude Code isn't terminal-text-only: it can produce shareable web artifacts — dashboards, visual reports, interactive summaries — published as pages rather than dumped as text. The pattern to remember: *ends of loops deserve artifacts*. A weekly review someone can read in a browser gets read; a wall of markdown in a repo mostly doesn't.

### Computer and browser use

The loop's reach extends past the filesystem: browser automation (e.g. Playwright over MCP, or Claude's browser control) lets the same loop check a live page, fill a form, or verify that the thing it built actually renders. Treat it like any connector — powerful, token-hungry, connect when a task needs eyes on a real browser.

### The second-brain pattern

Your harness is only as good as the context it can reach. Keeping your notes, decisions, and project logs as plain markdown (an Obsidian vault is the classic shape) turns your accumulated thinking into a **context substrate**: Claude Code can agentically search it (Module 1 — no vector DB), and write back to it. Notes stop being storage and become working memory for the loop. Your public learning log has quietly been this all along.

## Resources

- [Hooks reference](https://code.claude.com/docs/en/hooks) — official docs: events, matchers, exit codes, stdin schema. Read before writing your first hook.
- [Claude Code settings](https://code.claude.com/docs/en/settings) — official; where hook config lives.
- Based in part on [Your Claude Code Is Broken. Here's the 5-Minute Fix](https://www.aiinpublic.com/p/your-claude-code-is-broken-heres) from the AI in public newsletter — the hooks-vs-prose framing and the delete-blocking starter hook.
- [Stop Prompting Claude. Build Loops Instead.](https://www.aiinpublic.com/p/stop-prompting-claude-build-loops) — AI in public; the weekly-review loop idea the capstone builds on.

## Build — ship something

**Day 20 — Your first hook.**

1. Write `hooks/block_deletes.py`: read the JSON from stdin, and if the Bash command contains a destructive pattern (`rm -rf`, `rm` outside a temp dir — your call), print a refusal message and exit 2.
2. Wire it into `.claude/settings.json` as above.
3. **Test it**: ask Claude to delete a scratch file. Watch the hook block it. Then confirm normal commands still pass — an over-eager hook is a harness you'll disable within a week.
4. Publish hook + config + a line on what invariant you chose and why.

**Day 21 — Capstone: the weekly self-improving loop.**

1. Create `LOOP.md` in your project: what the weekly review covers — log entries since last run, what the harness got wrong, which `CLAUDE.md` rules were violated or useless, what task got repeated enough to deserve a skill.
2. Create a memory file `loop-history.md` the loop appends to, dated, each run.
3. Write the trigger prompt (save it in `LOOP.md`): review the week per the checklist, **propose** concrete harness changes — a `CLAUDE.md` edit, a skill tweak, a new hook — and have your Module 7 read-only reviewer critique the proposals before *you* approve any change. The loop proposes; you ratify.
4. Run it once for real. Apply at least one approved improvement. Publish `LOOP.md`, the history file's first entry, and the diff of the improvement.

!!! warning
    A loop running unattended is a loop making mistakes unattended. You stay in the loop as editor — that's a design feature, not a training-wheels phase.

## Log it

```markdown
## Days 20–21 — Module 8: Extending the loop (capstone)
- Hook: <link> — invariant enforced: <one line>; blocked test: pass/fail
- Loop: <link to LOOP.md> — first run done: yes/no
- First self-improvement it proposed (and I ratified): <one line + diff link>
- Level 2 exit state: CLAUDE.md ✓ skill ✓ connector decision ✓ subagent ✓ hook ✓ loop ✓
```
