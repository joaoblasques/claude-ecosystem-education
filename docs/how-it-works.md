# How it works

## Learning in public, concretely

The accountability mechanism is deliberately boring:

1. **One log page per day.** Date, what you built, what broke, what surprised you,
   what's next. Five minutes to write. See the [log format](log/index.md).
2. **Committed to git.** Your streak isn't a number in an app — it's `git log`.
   Gaps are visible. That's a feature.
3. **Artifacts linked, not described.** Each day's Build section produces something
   shareable (an Artifact link, a gist, a screenshot, a repo path). Link it from the
   log entry.
4. **Weekly synthesis.** Once a week, one page: what compounded, what you'd tell
   someone a week behind you, and feedback on the curriculum itself.

## Why public?

Private learning plans die silently. Public ones create three pressures that private
ones can't: an audience (even hypothetical), a visible gap when you skip, and a
searchable record you can point to later — for yourself, an employer, or the next
learner. The program asks for the smallest public commitment that still works: a daily
page nobody may ever read, but anybody could.

## Join: fork-to-learn

1. **Fork** the repo (link in the header once the repo is public).
2. **Clear the log**: delete `docs/log/*.md` except `index.md`, write your own Day 1.
3. **Deploy**: enable GitHub Pages on your fork (the included workflow builds the site
   on every push).
4. **Be counted**: open a PR adding one line to [Participants](participants.md) —
   name, fork URL, start date.

Your fork is yours: reorder days, skip modules, add your own. The curriculum is a
spine, not a cage.

## Pace and honesty rules

- The "days" are working sessions (1–2 h), not calendar days. Life happens; the log
  just tells the truth about it. One borrowed rule that works (from
  [#100DaysOfCode](https://github.com/kallaway/100-days-of-code), whose mechanics
  inspired this program's log): **never miss two days in a row.**
- A day isn't done until something shipped. If nothing shipped, the log entry says so
  and why — that entry still counts. Honesty over streaks.
- Don't log what you didn't do. The whole value of the record is that it's real.

## Cost

Level 1 works on a paid Claude plan (some features — Chrome extension, higher limits —
need one; noted per day). Level 2–3 assume Claude Code on a Pro/Max plan or API access.
Know your budget: claude.ai, Claude Code, Desktop, and Cowork all draw from
[one shared usage pool](https://support.claude.com/en/articles/11647753-how-do-usage-and-length-limits-work)
(5-hour rolling window + weekly cap); only API use is billed separately.
The program itself is free and always will be.
