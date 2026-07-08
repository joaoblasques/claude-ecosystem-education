# Claude Ecosystem Education — repo context

Public learn-in-public education site (MkDocs Material → GitHub Pages, domain
claudeecosystemeducation.com). Jonas is Learner #0; his daily log seeds the content.
Vault brain (private): `~/Dev/second-brain/01_Projects/Claude-Ecosystem-Education/`
— read-only from here; never commit the vault from this session.

## Rules
- **Original prose only.** Credit + link community sources (esp. the "AI in public"
  newsletter, aiinpublic.com). NEVER reproduce paywalled content or full prompt kits.
- **Not affiliated with Anthropic** — keep the disclaimer in mkdocs.yml copyright and
  never imply endorsement.
- Hedge UI-path claims ("as of mid-2026"); prefer linking official docs
  (docs.claude.com, support.claude.com) over restating them.
- Day/module pages follow the fixed template: Goal / Why this matters / Concepts /
  Resources / Build / Log it.
- Verify before commit: `mkdocs build --strict` must pass.
- Stage explicit paths; never `git add .`.

## Standing loops (the self-improving part)
- `/log` — create today's learning-log page from what was actually done + update nav.
- `/curriculum-review` — weekly: check ecosystem changes + participant feedback,
  propose curriculum edits (edits land as a reviewed commit, never silent).
