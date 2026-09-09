# chudarin-figma-skills

Skills for agents that design in Figma — Claude Code and Codex. Five skills, one per stage
of the work, built and refined on real product files.

| Stage | Skill | What it does |
|---|---|---|
| Plan | `figma-plan-user-flows` | Maps screens, states, entry/exit points and a Figma file structure before any design starts |
| Understand | `figma-audit-design-system` | Read-only audit of an existing design system: components, tokens, patterns, debt, documentation pages |
| Design | `figma-design-screens` | The process for designing or changing product screens: style source, briefs, checks, editing approved work one element at a time |
| Execute | `figma-plugin-api-rules` | 390+ field-tested Figma Plugin API gotchas and verification recipes — load before any `use_figma` call |
| Repair | `figma-fix-variable-bindings` | Scan → resolve → rebind detached, orphaned and hardcoded variable bindings |

Every skill is plain Markdown: `SKILL.md` + `references/` + `agents/openai.yaml` for Codex.

## Install

**Claude Code** — symlink or copy each skill into `~/.claude/skills/` (all projects) or
`<project>/.claude/skills/` (one project):

```bash
git clone https://github.com/schudarin/chudarin-figma-skills ~/DevGIT/chudarin-figma-skills
for s in ~/DevGIT/chudarin-figma-skills/skills/*; do ln -s "$s" ~/.claude/skills/; done
```

**Codex** — the same into `~/.agents/skills/` (all projects) or `<repo>/.agents/skills/`.
Invoke explicitly with `$skill-name`; implicit invocation is enabled on every skill.

**Prerequisite:** the Figma MCP server. `figma-plugin-api-rules` and `figma-design-screens` also expect
Figma's own `figma-use` instructions loaded before the first `use_figma` call — the plugin
skill in Claude Code, or the MCP resource `skill://figma/figma-use/SKILL.md` elsewhere.

## Which skill when

- "What screens do we need for this feature?" → `figma-plan-user-flows`
- "What's in this design system, where is the debt, document it" → `figma-audit-design-system`
- "Design / change / rebuild this screen" → `figma-design-screens` (which pulls in `figma-plugin-api-rules`)
- Any script that writes to Figma → `figma-plugin-api-rules`
- "Variables are detached / hardcoded / 'Variable was deleted'" → `figma-fix-variable-bindings`

## Contributing

Each skill documents its own extension protocol; for `figma-plugin-api-rules` see the end of
its `SKILL.md`. Facts about one specific Figma file (node IDs, local conventions) don't
belong in these skills — keep them in `<project>/.claude/design.md` or your own notes.

## License

MIT — see `LICENSE`.
