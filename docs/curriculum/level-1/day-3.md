# Day 3 — Skills: Teach Claude Your Standards

**Goal:** Build and test one Skill for your most-repeated task, and learn the five silent setup mistakes that make Skills fail.

## Why this matters

Without Skills, every session starts from zero: you re-explain your tone, your format rules, your constraints, and you fix the same mistakes in every output. A Skill stores those constraints once, permanently, so quality jumps on the *first* run instead of the fifth. It is the difference between prompting Claude and having onboarded it.

## Concepts

### What a Skill is

A Skill is a plain markdown briefing document that Claude consults before doing a matching task. No code — just structured instructions: a name, a description (which doubles as the trigger), what to do, what *not* to do, constraints, and examples.

Three categories, and a skill should live in exactly one:

- **Output skills** — file-type and format constraints (how your docs, decks, or spreadsheets must look).
- **Workflow skills** — standards for recurring tasks (newsletters, code reviews, proposals).
- **Context skills** — background Claude can't infer (brand voice, tech stack, audience).

One skill = one problem. Mixing categories in a single skill blurs all of them.

### Building one with "Create with Claude"

As of mid-2026, the path on claude.ai is roughly: new chat → "+" → Skills → Manage Skills → "+" Create Skill → **Create with Claude**. Claude interviews you about the task, and — critically — asks you to upload sample files. Real samples labeled "this is good" carry far more weight than any description of what good looks like. Show it, don't tell it. To edit later, invoke the skill by name with `/` and describe the change.

### The five silent setup mistakes

Skills rarely fail loudly; they fail *silently* — firing on the wrong tasks or not at all. Five configuration gaps cause most of it:

1. **Vague description.** The description line in the skill's frontmatter is the *trigger*, not a label. If it's broad ("helps with writing"), the skill fires inconsistently. Fix: name the ONE task, list exact phrases that should trigger it, and list similar tasks that should *not*.
2. **File bloat.** Overlong skills get skimmed; Claude ignores half the content and burns tokens on the rest.
3. **Phantom file references.** Pointing at files that don't exist in the skill breaks it quietly.
4. **Multi-purpose skills.** Two jobs in one skill produce blurred output on both.
5. **Skipping diagnostics.** Test trigger phrases *before* relying on the skill, or you'll debug in production forever.

!!! warning "Inconsistent output is a configuration problem"
    When a skill misbehaves, the reflex is to blame the model. Almost always it's one of the five gaps above — fixable in minutes once you look at the description line.

!!! tip "The 15-minute rule"
    A skill doesn't need to be perfect to be worth having. Fifteen focused minutes on one specific, well-triggered skill compounds every time the task recurs — and you can edit it any time by invoking it with `/` and describing the change.

## Resources

- [Claude Help Center — Skills](https://support.claude.com) — official guide to creating and managing Skills (Anthropic)
- [Anthropic docs — Agent Skills](https://docs.claude.com) — the underlying skill format, useful even at the app layer (Anthropic)
- Based in part on [How to Build Claude Skills](https://www.aiinpublic.com/p/how-to-build-claude-skills) from the AI in public newsletter.
- Based in part on [Stop building Claude Skills like this](https://www.aiinpublic.com/p/stop-building-claude-skills-like) from the AI in public newsletter — the full five-mistake repair checklist (partly paid).

## Build — ship something today

Build **one Skill for your single most-repeated task** — not three skills, one.

1. Pick the task you do most often with Claude (weekly report, client email, meeting summary, content draft).
2. Gather 3–5 *real* examples of good past output. This is the highest-leverage step.
3. Run "Create with Claude," answer its interview honestly, upload the samples.
4. Harden the description: "Use ONLY when [task]. Triggers: [3 exact phrases]. Do NOT use for: [2–3 near-miss tasks]."
5. Test: run one trigger phrase and one near-miss phrase. The skill should fire on the first and stay silent on the second.
6. Run the real task once and compare the output against your last manual attempt.
7. If the output missed a constraint, add it to the skill — not to your prompt. Fixing the skill is the point.

Ship: the before/after comparison.

## Log it

> **Level 1, Day 3 — First Skill.**
> What I built: a [category] skill for [task].
> Trigger design: fires on [phrases], excluded [near-misses].
> Before/after: [one concrete difference in first-run quality]
> What broke / surprised me: [e.g., the near-miss test failing until I added exclusions]
