# figma-plugin-api-rules

A field-tested knowledge base of Figma Plugin API gotchas and patterns, written for
agents that drive Figma through `use_figma`-style programmatic calls — nodes, auto-layout,
components and variants, instances, text and fonts, variables and modes, connectors,
annotations, FigJam, and the MCP tool layer. Every entry is a real case that broke
exactly this way, written up as Principle / Symptom / Pattern — not a reading of the docs.

## What's inside

- `SKILL.md` — the core: hard rules, the most frequently recurring universal API
  principles, a routing table by topic, a quick-scan table of common mistakes, and the
  protocol for adding to the pack.
- `references/*.md` — gotchas by topic (components and variants, instances, layout and
  geometry, text and styles, variables, connectors, annotations, publishing hygiene,
  FigJam, the tool layer / environment, building a screen from code).

## How to use

The format is an agent skill (`SKILL.md` + `references/`). It works with Claude Code
and with Codex (via `agents/openai.yaml`).

- **Claude Code:** put the folder in `~/.claude/skills/figma-plugin-api-rules/` (available in
  every project) or in `<project>/.claude/skills/figma-plugin-api-rules/` (that project only).
- **Codex:** put it in `~/.agents/skills/figma-plugin-api-rules/` or `<repo>/.agents/skills/`.
  Invoke explicitly with `$figma-plugin-api-rules`; implicit invocation is on.

Load `SKILL.md` before the first programmatic Figma call in a session — in addition to
your tool's own instructions for calling the Figma API (`figma-use` in Claude Code, or the
MCP resource `skill://figma/figma-use/SKILL.md` elsewhere). Load the specific
`references/*.md` by the routing table inside `SKILL.md` when the task touches that topic.

If you use a different agent, this is plain Markdown with a clear structure — it works as
an ordinary context file you hand to the agent before Figma work.

## How to add to it

See "Protocol for recording a new insight" at the end of `SKILL.md`. In short: a new
gotcha is a `### slug` section at the end of the relevant topic file; facts about one
specific Figma file (Set IDs, Page IDs, local quirks) go into your own
`references/files/<file>.md`, which is not part of this shared pack and shouldn't travel
with it.
