# Module 6 — MCP & Connectors, Builder Side (Days 16–17)

**Goal:** Connect Claude Code to an external tool via MCP, measure what the connection costs in tokens, and make one defensible connect-or-script decision.

## Why this matters

Out of the box, Claude Code touches your files and shell. MCP (Model Context Protocol) is how it reaches everything else — databases, browsers, SaaS APIs, your company's internal tools — through one standard plug instead of bespoke integrations. But every plug you add bills your context. This module is about connecting *deliberately*.

## Concepts

### Host, client, server

MCP is a client-server protocol with three roles:

- **Server** — a small program exposing capabilities: your database, GitHub, a browser. Anyone can write one.
- **Host** — the application the user drives (Claude Code, Claude Desktop, other AI apps).
- **Client** — the connection the host maintains to each server, one per server.

The point of the standard: a server written once works in every MCP host, and a host speaks to every server. USB-C for AI tools.

### The three primitives

Servers can expose three kinds of things:

1. **Tools** — actions the model may call (`query_database`, `create_issue`). The workhorse; most servers are mostly tools.
2. **Resources** — data the host can read into context (a file, a schema, a log stream).
3. **Prompts** — reusable prompt templates the server offers the user.

When evaluating a server, read its tool list first — that's what your agent will actually do with it, and what you'll pay for.

### stdio vs. HTTP transport

- **stdio:** the host launches the server as a local subprocess and talks over stdin/stdout. For local, personal, single-user tools. No network, no auth story needed.
- **HTTP (streamable):** the server runs remotely; the host connects over the network with real auth. For shared, hosted, multi-user services.

Rule of thumb: consuming someone's hosted service → HTTP; running something on your machine → stdio.

Connecting is one command, and scope matters — `--scope project` writes a shareable `.mcp.json` in the repo instead of burdening every project you own:

```bash
claude mcp add --scope project github -- npx -y @modelcontextprotocol/server-github
claude mcp list   # see what's connected, and from which scope
```

### When MCP vs. a plain script

Claude Code can already run scripts — that's often the lazier, better answer. Choose a **script** when the capability is a one-shot transformation, is project-specific, or is something Claude can just run with Bash. Choose **MCP** when you need a persistent connection or session state, auth managed once rather than per-call, the same integration across many projects or hosts, or interactive back-and-forth (e.g. a live browser). If a 30-line script covers it, the script wins: zero context overhead until invoked.

### The over-connection anti-pattern

Every connected server injects its tool definitions into your context — every session, used or not. A dozen servers can quietly eat a five-figure token budget *before your first message*, diluting attention exactly as described in Module 3.

!!! warning
    Connectors are pets, not trophies. Connect what this project uses weekly; disconnect the rest. Project-scoped config beats global config for exactly this reason.

## Resources

- [Connect Claude Code to tools via MCP](https://code.claude.com/docs/en/mcp) — official docs: `claude mcp add`, scopes, transports.
- [modelcontextprotocol.io](https://modelcontextprotocol.io) — the spec, architecture overview, and official SDKs.
- [MCP connector directory](https://docs.claude.com/en/docs/agents-and-tools/mcp-connectors) — official; browse before you build, someone may have shipped your server already.

## Build — ship something

**Day 16 — Connect and measure.**

1. Pick one server that serves your real project (good candidates as of mid-2026: GitHub, a Postgres/SQLite server, Playwright for browser checks). Read its tool list and required permissions first.
2. Check `/context` in a fresh session *before* connecting; note the baseline.
3. Add it project-scoped (`claude mcp add ...`), restart, run one real task through it.
4. Check `/context` again. Write `connector-audit.md`: the server, the token overhead you measured, the task it enabled, verdict — keep or drop.

**Day 17 — The connect-or-script decision.**

1. Pick a second capability you're tempted to connect.
2. Write the decision using the criteria above: state, auth, reuse, interactivity — script or MCP, in writing, *before* building.
3. Build the cheap version: either wire the second server, or write the plain script and let Claude Code call it.
4. Publish `mcp-decision.md` + the script (if that side won) to your learning repo.

## Log it

```markdown
## Days 16–17 — Module 6: MCP & connectors
- Connected: <server> — context cost measured: <n tokens / n%> (audit: <link>)
- Task it enabled: <one line>
- Second capability: <name> → decided: script / MCP, because <one line>
- Connectors now active in this project: <n> (and why each earns its seat)
```
