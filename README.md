# Claude Ecosystem Education

A free, public, learn-in-public program to become productive across the whole Claude
ecosystem — from the consumer apps (Projects, Artifacts, Skills, Connectors, Chrome, Excel)
to the agentic harness (Claude Code, CLAUDE.md, hooks, subagents, MCP, Agent SDK).

**Site:** https://claudeecosystemeducation.com (MkDocs Material, deployed via GitHub Pages)

## The idea

1. **Learn by shipping.** Every day of the curriculum ends with a shippable artifact.
2. **Accountability by default.** Progress is a public log committed to git — the commit
   history *is* the streak. No claims, just receipts.
3. **One path, two audiences.** Level 1 needs no code; the path continues into Claude Code
   and agent-building without a wall.
4. **Self-improving.** The program maintains itself with Claude loops (see
   `.claude/skills/`): a daily log skill and a weekly curriculum-review skill that checks
   the ecosystem for changes and proposes updates. The maintenance loop is itself a lesson.

## Curriculum

| Level | Scope | Duration |
|---|---|---|
| 1 — The Claude Apps | claude.ai, Projects, Memory, Artifacts, Skills, Connectors/MCP, Chrome, Excel, loops | Days 1–7 |
| 2 — Claude Code & the Harness | agent loop, core workflow, context economy, CLAUDE.md, skills authoring, MCP, subagents, hooks | Days 8–21 |
| 3 — Builder | Agent SDK, publish a skill/MCP server, run a production loop, teach-back | Days 22–30+ |

## Run locally

```bash
pip install -r requirements.txt   # or: uv pip install -r requirements.txt
mkdocs serve                      # http://127.0.0.1:8000
```

## Join (fork-to-learn)

1. Fork this repo.
2. Delete `docs/log/*`, start your own Day 1 log page.
3. Commit a log entry per day — your fork's Pages site is your public record.
4. PR one line to `docs/participants.md` on the main site to be listed.

## Content rules

- Original prose. Community sources are credited and linked, never reproduced.
- Paywalled material is described and linked, never copied.
- UI paths are hedged ("as of mid-2026") — the ecosystem moves fast; the weekly
  curriculum-review loop exists to catch drift.

## Legal

Independent community project. Not affiliated with, endorsed by, or sponsored by
Anthropic. "Claude" is a trademark of Anthropic, PBC. Content licensed CC BY-SA 4.0
unless noted.
