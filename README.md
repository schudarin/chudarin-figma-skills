# chudarin-figma-skills

Skills for agents that design in Figma — Claude Code and Codex. Five skills, one per stage
of the work, built and refined on real product files.

| Stage | Skill | What it does |
|---|---|---|
| Plan | `figma-plan-user-flows` | Maps screens, states, entry/exit points and a Figma file structure before any design starts |
| Understand | `figma-audit-design-system` | Read-only audit of an existing design system: components, tokens, patterns, debt, documentation pages |
| Design | `figma-design-screens` | The process for designing or changing product screens: style source, briefs, checks, editing approved work one element at a time |
| Execute | `figma-plugin-api-rules` | 390+ field-tested Figma Plugin API pitfalls and verification recipes — load before any `use_figma` call |
| Repair | `figma-fix-variable-bindings` | Scan → resolve → rebind detached, orphaned and hardcoded variable bindings |

Every skill is plain Markdown: `SKILL.md` + `references/` + `agents/openai.yaml` for Codex.

## Install

**Claude Code, as a plugin** — two commands, and `/plugin update` picks up new versions:

```
/plugin marketplace add schudarin/chudarin-figma-skills
/plugin install chudarin@chudarin
```

The skills then load as `chudarin:figma-design-screens`, `chudarin:figma-plugin-api-rules`, and so on.

**Claude Code, by hand** — symlink or copy each skill into `~/.claude/skills/` (all projects) or
`<project>/.claude/skills/` (one project):

```bash
git clone https://github.com/schudarin/chudarin-figma-skills ~/chudarin-figma-skills
mkdir -p ~/.claude/skills
for s in ~/chudarin-figma-skills/skills/*; do ln -sfn "$s" ~/.claude/skills/; done
```

**Codex** — the same into `~/.agents/skills/` (all projects) or `<repo>/.agents/skills/`.
Invoke explicitly with `$skill-name`; implicit invocation is enabled on every skill.

```bash
mkdir -p ~/.agents/skills
for s in ~/chudarin-figma-skills/skills/*; do ln -sfn "$s" ~/.agents/skills/; done
```

Re-run either loop after `git pull` to pick up updates.

**Prerequisite:** the Figma MCP server. `figma-plugin-api-rules` and `figma-design-screens` also expect
Figma's own `figma-use` instructions loaded before the first `use_figma` call — the plugin
skill in Claude Code, or the MCP resource `skill://figma/figma-use/SKILL.md` elsewhere.

## Recommended alongside

These skills decide *how* to work in Figma once the task is clear. They don't decide *what*
the task is. In practice the best runs pair them with a process skill that gates the first
action — asks which project and which Figma file before anything is touched. With Claude
Code we use Anthropic's `superpowers` plugin (`brainstorming` fires first on "add a button",
asks for the project and the file link, then hands over). Any equivalent "clarify before
acting" skill works; without one, expect the agent to start from the wrong page.

Also worth having: a copy/voice skill of your own for button labels and UI text — these
skills place the text, they don't write it.

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
