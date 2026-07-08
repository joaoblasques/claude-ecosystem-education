---
name: curriculum-review
description: Use ONLY for the weekly curriculum maintenance pass. Triggers: "/curriculum-review", "weekly review", "check the curriculum for drift". Do NOT use for writing daily log entries.
---

# Weekly curriculum review (the self-improving loop)

Check the curriculum against reality and propose fixes. Propose, don't silently land:
a loop running unattended is a loop making mistakes unattended.

1. **Link rot:** extract every external URL from `docs/**/*.md`
   (`grep -rhoE 'https?://[^) ]+' docs | sort -u`), HEAD-check each
   (`curl -s -o /dev/null -w '%{http_code}' -m 10 <url>`), list non-200s.
2. **Ecosystem drift:** WebFetch the Claude release notes / changelog pages
   (docs.claude.com release notes, claude.com/blog) for changes since the last review
   that contradict any curriculum claim (UI paths, feature names, plans/limits).
   Check the pages that hedge with "as of mid-2026" first.
3. **Participant feedback:** if the GitHub repo is live, `gh issue list --label
   curriculum` and fold actionable reports in.
4. **Propose:** write the findings + proposed edits to `docs/log/review-YYYY-MM-DD.md`
   (not in nav), apply the uncontroversial fixes (dead link swaps, renamed features)
   directly in the working tree, and leave judgment calls as a checklist in the
   review file.
5. Run `mkdocs build --strict`. Show a diff summary and stop — the human reviews and
   commits.
