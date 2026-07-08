# Module 5 — Agent Skills, Author Side (Days 14–15)

**Goal:** Author, test, and publish one working skill of your own — and be able to say precisely why skills are token-cheap when a big CLAUDE.md is not.

## Why this matters

Anything you've asked Claude to do three or more times, the same way, is a skill waiting to be written. Skills turn your recurring instructions into an installable, shareable capability — and unlike stuffing procedures into `CLAUDE.md`, they cost almost nothing until the moment they're needed. This is Module 3's context economy, weaponized.

## Concepts

### Anatomy of a skill

A skill is a folder containing a `SKILL.md` file (plus any supporting files or scripts), placed in `.claude/skills/<name>/` for a project or `~/.claude/skills/<name>/` for everywhere. `SKILL.md` has YAML frontmatter and a markdown body:

```markdown
---
name: changelog-writer
description: Draft a changelog entry from recent git commits. Use when the
  user asks to update the changelog, write release notes, or summarize
  what changed since the last release.
---

# Changelog writer

1. Run `git log --oneline` since the last version tag.
2. Group commits: Added / Changed / Fixed. Ignore chores and merges.
3. Write entries as user-visible outcomes, not commit messages.
4. Append to CHANGELOG.md under a new dated heading; show the diff first.
```

The body is instructions to Claude, written like you'd brief a competent colleague. Plain English is enough — no code required.

### The description field is the trigger

Claude sees only skill **names and descriptions** up front; it loads a skill's body when a request seems to match. So the description does double duty: *what this does* + *when to use it*, including the phrases a user would actually say. A vague description ("Helps with changelogs") means a skill that never fires. Description-writing is the actual craft of skill authoring; the body is mostly transcription.

### Progressive disclosure: why skills are token-cheap

The economics: with dozens of skills installed, your session pays only a line or two each (name + description) until one triggers — *then* the body loads, and any referenced files load only if consulted. Compare: the same procedures inlined in `CLAUDE.md` bill every session, every task, relevant or not. Metadata always; body on trigger; resources on demand.

### One skill = one problem

"Writing-helper" that formats, edits, and translates will half-fire on everything and load three procedures to use one. Split it. Small skills also compose — Claude can chain two focused skills in one task.

### Security: third-party skills

A skill is instructions your agent will *follow*, with your permissions — treat installing one like installing software, not like saving a note.

!!! warning
    Before installing any third-party skill: read the whole `SKILL.md` (it's short), inspect any bundled scripts, and be suspicious of skills that curl remote URLs, touch credentials, or ask to run outside the project directory. If you can't read it, don't run it.

## Resources

- [Agent Skills](https://code.claude.com/docs/en/skills) — official Claude Code docs; format, locations, discovery.
- [Agent Skills overview](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) — official; skills across the Claude platform, plus authoring best practices.
- [anthropics/skills](https://github.com/anthropics/skills) — Anthropic's open-source skill collection; read a few before writing yours.

## Build — ship something

**Day 14 — Author your skill.**

1. Pick the task you've repeated most often with Claude (from your Day 10 cheat sheet or your log). One problem only.
2. Write the body first — the steps you actually want followed, with your quality bar spelled out. Then write the description *last*, including trigger phrasing.
3. Install at `.claude/skills/<name>/SKILL.md` and confirm it's listed (as of mid-2026, `/skills` or asking "what skills do you have" both work).

**Day 15 — Test, harden, publish.**

1. Trigger test: in fresh sessions, phrase the request three different ways. Note which fired the skill; tune the description until 3/3.
2. Negative test: make a *near-miss* request that should NOT trigger it; verify it stays cold.
3. Quality test: compare the skill's output to a no-skill session on the same task. If it's not clearly better, sharpen the body.
4. Publish the skill folder to your learning repo with a three-line README (what, when, one example) — written like something a stranger could install after reading it.

## Log it

```markdown
## Days 14–15 — Module 5: My first skill
- Skill: <name> (<link>) — solves: <one line>
- Trigger tuning: <n> description rewrites to hit 3/3; near-miss stayed cold: yes/no
- Skill vs no-skill on same task: <one-line verdict>
- Token logic in my own words: <why this is cheaper than CLAUDE.md inlining>
```
