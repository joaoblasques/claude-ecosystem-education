---
name: log
description: Use ONLY when asked to write today's learning-log entry for the site. Triggers: "/log", "write today's log", "log today". Do NOT use for editing curriculum pages or the weekly review.
---

# Daily log entry

Draft today's public learning-log page. The human reviews and commits — never commit
from this skill.

1. Determine today's date (`date +%F`) and the next Day number (count existing
   `docs/log/*.md` entries, excluding `index.md`).
2. Gather what actually happened: `git -C . log --oneline -10`, `git diff --stat HEAD`,
   plus whatever the session did today. If nothing happened, the entry says so — never
   invent work.
3. Write `docs/log/YYYY-MM-DD.md` in the exact format from `docs/log/index.md`
   (Shipped / What I did / What broke / Tomorrow). Facts only; link every artifact.
4. Add the entry to the list in `docs/log/index.md` (newest first) and to the
   `nav:` Learning Log section in `mkdocs.yml`.
5. Run `mkdocs build --strict`; fix what it flags.
6. Show the drafted entry and stop — the human edits and commits.
