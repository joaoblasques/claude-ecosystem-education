# Day 4 — Connectors & MCP: Plug In Your Real Data

**Goal:** Connect Gmail, Calendar, and Drive to Claude with a deliberate permission map — and understand what MCP is and what over-connecting costs you.

## Why this matters

Until now, everything you've built runs on data you paste in. Connectors flip that: Claude reads your actual inbox, calendar, and documents, so "prep me for tomorrow's call" becomes a real answer instead of a template. This is also the day you start making genuine security decisions — which is why the permission model matters as much as the plumbing.

## Concepts

### MCP, from the user's side

MCP (Model Context Protocol) is the open standard that lets Claude talk to external tools. You don't need to know how it works internally; you need to know that **Connectors are MCP under a one-click skin**, and that anything speaking MCP — including tools Anthropic never built a card for — can be plugged in as a custom connector. That's the difference between a fixed integration list and an ecosystem.

### Connecting the big three

As of mid-2026: new chat → "+" → Connectors → Add connectors → pick the app → OAuth authorize → configure permissions. Two gotchas:

- **Connecting ≠ using.** A connector must be toggled ON in the chat you're using, or Claude ignores it.
- Each service's capabilities differ. Gmail, for instance, can read and draft — not send or delete. Know the actual scope of each connection.

### The permission hierarchy

Every connector tool gets one of three levels: **Always Allow**, **Needs Approval**, or **Blocked**. A sane starting map:

- Reads: Always Allow (low risk, high frequency).
- Writes and drafts: Needs Approval — Claude proposes, an approval card appears, you decide.
- Anything you never want automated (e.g., label/folder restructuring): Blocked.

Approval-first is the default posture. Loosen it per-tool only after the connector has earned trust.

### Auto vs On-Demand, and the context-window tax

Connector tool definitions consume context — potentially many thousands of tokens *per connector*, on every message, whether used or not. Two access modes manage this:

- **Auto** — Claude routes between all active connectors itself. Convenient with 1–4 connectors.
- **On-Demand** — Claude only touches connectors you name. The right choice once you're past ~5, preserving context for actual work.

!!! warning "Over-connecting is a real cost"
    More connectors ≠ more capable. Ten idle connectors can quietly eat a large slice of every conversation's context window. Connect what you use; block what you don't.

### Stretch: a custom connector

To feel the "open standard" point, add one custom connector: Settings → Connectors → Add custom connector → paste the tool's MCP server URL → authorize. A well-documented example is Higgsfield's video-generation MCP, which turns a Claude chat into a video studio. Two silent failure modes: a typo'd URL saves fine but never works, and skipping "Always Allow" during authorization leaves the connection incomplete. Verify with "what tools do you have from [connector]?" before relying on it.

## Resources

- [Claude Help Center — Connectors](https://support.claude.com) — official setup and permission guides (Anthropic)
- [Anthropic docs — MCP](https://docs.claude.com) — what the protocol is, for when you're curious (Anthropic)
- Based in part on [Stop using 7 apps to do just 1 thing](https://www.aiinpublic.com/p/stop-using-7-apps-to-do-just-1-thing) from the AI in public newsletter — includes 7 ready-to-use connector prompts.
- Based in part on [Claude just became a video studio](https://www.aiinpublic.com/p/claude-just-became-a-video-studio) from the AI in public newsletter — the Higgsfield custom-connector walkthrough.

## Build — ship something today

Build your **connected morning briefing**.

1. Connect Gmail, Google Calendar, and Google Drive (or your equivalents).
2. Write down your permission map *before* configuring it: for each service, what's Always Allow, Needs Approval, Blocked — and why. Then set it.
3. Toggle the connectors on in a chat and run a briefing prompt of your own design, e.g.: "From Gmail: everything waiting on a reply from me this week. From Calendar: today's conflicts and the best 45-minute focus slot. Under 150 words, then the single top priority."
4. Have Claude *propose* one calendar event (your focus block) with "don't add until I approve" — inspect the approval card, then approve.
5. Save the briefing prompt into your Level 1 Project for reuse.

Ship: your permission map (the reasoning, not your data) + the briefing prompt.

## Log it

> **Level 1, Day 4 — Connected.**
> What I built: Gmail/Calendar/Drive connected with a deliberate permission map + a reusable briefing prompt.
> My permission reasoning: [one line per service]
> What broke: [e.g., forgot to toggle the connector on; briefing too vague until I tightened the prompt]
> What surprised me: [e.g., the context-window cost argument for On-Demand]
