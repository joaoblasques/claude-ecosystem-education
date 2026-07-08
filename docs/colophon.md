# Colophon — how this site maintains itself

This program eats its own dogfood: it's operated by the same loops it teaches.

## The stack

- [MkDocs Material](https://squidfunk.github.io/mkdocs-material/) → GitHub Pages,
  built on every push by a GitHub Actions workflow.
- Content is plain Markdown in the open repo. The repo's `.claude/` folder holds the
  automation described below.

## The loops (Module 8 and Day 7, applied to this site)

- **`/log` (daily)** — a Claude Code skill that drafts today's log page from what
  actually happened (git diff + session notes), updates the nav, and leaves the entry
  for human review. The human edits and commits — the loop drafts, the person signs.
- **`/curriculum-review` (weekly)** — checks for ecosystem drift (release notes, dead
  links, changed UI paths), reads participant-filed issues, and proposes curriculum
  edits as a reviewed change. Nothing lands silently: *a loop running unattended is a
  loop making mistakes unattended.*

## Sources & credit

The curriculum synthesizes, credits, and links — it does not reproduce:

- **Official:** [Anthropic docs](https://docs.claude.com), [Claude support
  docs](https://support.claude.com), Anthropic release notes and courses.
- **Community:** the [AI in public](https://www.aiinpublic.com) newsletter by Hamza
  Khalid — the "learn Claude in 7 days" roadmap that seeded Level 1 — plus the other
  sources credited on each page.
- Paywalled material is never copied; posts are described and linked so the authors
  keep what's theirs.

## Independence & license

An independent community education project — not affiliated with, endorsed by, or
sponsored by Anthropic. "Claude" is a trademark of Anthropic, PBC; it's used here
nominatively, to refer to the actual products being taught.

Content: CC BY-SA 4.0 unless noted. Code (workflows, skills): MIT.
