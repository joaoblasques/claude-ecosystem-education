# Day 2 — Artifacts: Build Your First Interactive App

**Goal:** Ship a working interactive tool — built entirely in chat, no code knowledge required — and learn the iteration pattern that makes Artifacts reliable.

## Why this matters

The overwhelming majority of Claude users only ever *ask for answers*; a small minority *build things*. Artifacts are the lowest-friction crossing point: describe a tool, and Claude renders a live, working version in a side panel next to the chat. The same request that would once have meant a spreadsheet, a diagramming app, or a designer's time becomes a two-minute prompt — if you know how to specify it.

## Concepts

### What an Artifact is

An Artifact is a self-contained piece of content Claude renders live beside the conversation, so you can see and use the result without leaving the chat. Six types cover most needs:

1. **Markdown documents** — formatted docs, reports, templates.
2. **SVG graphics** — logos, icons, simple illustrations.
3. **Data visualizations** — charts from data you paste.
4. **Mermaid diagrams** — flowcharts, sequence diagrams, org charts.
5. **HTML pages** — landing pages, email layouts, styled reports.
6. **React components** — interactive apps: calculators, forms, dashboards.

As of mid-2026, you can start from the chat (just ask) or from the dedicated Artifacts area in the claude.ai sidebar.

### Specificity beats everything

"Make a calculator" produces something generic. A prompt that works names four things:

- **Inputs** — every field, dropdown, and slider, with ranges and defaults.
- **Outputs** — exactly what is computed and how it's formatted.
- **Layout** — e.g., "inputs on the left, results on the right."
- **Style** — e.g., "clean and minimal, no gridlines, one accent color."

### Mini-version-first iteration

The single biggest Artifact failure mode is over-specifying the first version. The reliable loop:

1. Ask for a **mini version** with the core logic only.
2. Test it. Actually click things.
3. Iterate: "add one more feature only" — one change per message.
4. Repeat until done.

A stripped-down first build that works is a foundation; a maximal first build that half-works is a debugging session.

!!! tip "Diagrams and copy-paste"
    For Mermaid diagrams, add "no code, just the rendered diagram." When you want output to reuse elsewhere, say "copy-paste ready" explicitly.

## Resources

- [Claude Help Center — Artifacts](https://support.claude.com) — official overview of creating and sharing Artifacts (Anthropic)
- Based in part on [How to Build an App with Claude Artifacts](https://www.aiinpublic.com/p/how-to-build-an-app-with-claude-artifacts) from the AI in public newsletter — includes a 7-prompt starter kit (time-savings calculator, chart builder, flowchart, content-brief generator, landing page, table formatter, ROI calculator).

## Build — ship something today

Build a **calculator that answers a question you actually have** — an ROI calculator, a time-savings estimator, a pricing model, a habit tracker. Steps:

1. In your Level 1 Project, write the spec *before prompting*: list inputs (with ranges), outputs (with formatting), layout, and style. Four short lines is enough.
2. Ask for the mini version: core calculation, two or three inputs, one output.
3. Test it with real numbers from your life or work. Note anything wrong.
4. Iterate in single steps: fix the logic, then add one feature, then styling. Three to five rounds.
5. Publish/share the Artifact (share button on the artifact panel, as of mid-2026) and put the link in your log.

Timebox: 45 minutes. If you're not done, ship the last working version — that's the lesson.

## Log it

> **Level 1, Day 2 — First Artifact shipped.**
> What I built: [tool name + share link]
> The spec I wrote before prompting: [inputs / outputs / layout / style]
> What broke: [which iteration went wrong and how "one change per message" fixed it]
> What surprised me: [e.g., how much the mini-version-first rule mattered]
