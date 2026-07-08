# Level 3 — Builder (Days 22–30+)

**Goal:** stop being only a consumer of the ecosystem — contribute a working piece to
it, and run one loop that improves itself without you.

Level 3 is project-shaped, not day-shaped. Pick the projects in any order; ship all
four to "graduate". Expect roughly two weeks at 1–2 h/day.

## Project A — Build with the Agent SDK

The Agent SDK is the Claude Code harness — the agent loop, tools, permissions,
subagents — exposed as a library, generalized beyond coding.

- Build a small non-coding agent: a triager, a report generator, a file organizer.
- It must use at least one custom tool and one permission boundary.
- **Ship:** a repo with a README that a stranger could run.
- Resources: [Agent SDK docs](https://docs.claude.com/en/api/agent-sdk/overview) (as of mid-2026).

## Project B — Publish a skill (or an MCP server)

Take the best skill you authored in Level 2, harden it, and make it installable by
someone who isn't you: clear `description` triggers, no phantom file references, an
example transcript in the README.

- **Ship:** a public repo/gist + one person other than you having tried it (a
  participant here counts — trade installs on the [Participants](../../participants.md) page).
- Alternative: a minimal MCP server exposing one genuinely useful tool ("one thing
  done well" beats a kitchen sink).

## Project C — A production loop

Wire a loop that runs on a schedule against something you actually care about
(your inbox, your notes, your project's issues), with the three non-negotiables from
Day 7 and Module 8: a verification step, a human review gate, and a weekly
self-review that updates its own instructions.

- **Ship:** the loop's config + two weeks of its output linked in your log.
- The honest test: did you keep it running? A loop you turned off is a finding too —
  log why.

## Project D — Teach it back (graduation)

Write one lesson-quality page: the thing you wish this program had explained better,
in the day-page format (Goal / Why / Concepts / Resources / Build / Log it).

- **Ship:** a PR to this site (new page or a rewrite of an existing one), or the page
  published on your own fork with a cross-link.
- Teaching back is the real test of Level 2's mental models — and it's how this
  program compounds instead of rotting.

## Log it

Same as always: one entry per working session. For Level 3, each entry should link
the project's current state — half-finished counts, invisible doesn't.
