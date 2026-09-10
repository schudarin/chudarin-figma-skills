# Project State: `<project>/.claude/design.md`

One file per project. It is the only place project-specific style facts live — not a summary of them, the source. Screenshots of approved work live alongside it in `<project>/.claude/design-shots/`.

Both live in the project's own repository, not in this skill and not in agent memory. The reason is mechanical: a subagent doing design work can read a file in the repository it's already working in, but it cannot see the orchestrator's memory. Style that only exists in memory gets re-described from scratch inside every brief, and re-description drifts.

## Format — six sections, in this order

```markdown
# Design — <product>

## Settings
Design system: yes / no; where it's described
References: existing screens / external
Figma file: key, pages
Models: default from the skill; add a line only if this project needs something else

## Signature traits
What looks like an unfinished detail in this product but is actually the style.

## Approved
| Screen | Where in Figma | Screenshot | Date |

## Rejected — do not suggest again
<what was tried> → "<user's own words>", <date>

## In progress
What's being worked on, what's next.

## Project pitfalls
Anything about this specific project's tools or setup that cost time once.
```

## Filled example — xreadr

```markdown
# Design — xreadr

## Settings
Design system: no
References: existing screens (Library, Reader)
Figma file: key abc123, pages "Library", "Reader", "Settings"
Models: default from the skill

## Signature traits
Radius 0 on fields and buttons — this is the style, not an unfinished corner.
Guest sign-in as a table row, not a button — a recognized pattern, not a missing CTA.
Orange only on live/dynamic values, never on buttons.

## Approved
| Screen | Where in Figma | Screenshot | Date |
|---|---|---|---|
| Library — grid view | Library page, frame "Library/Grid" | design-shots/library-grid-2026-08-04.png | 2026-08-04 |

## Rejected — do not suggest again
Rounded 52px controls on Library → "пропал стиль, стало из чужого мира", 2026-08-03
ASCII texture on empty state → "ASCII не наш вариант, дизер точно лучше", 2026-08-02

## In progress
Reader settings sheet — typography controls done, color controls next.

## Project pitfalls
The Figma bridge hangs after long write sessions — work in small calls, not one long batch.
```

The two rejected lines above are real, kept in the user's own language on purpose — see the quoting rule below.

## Rules for keeping the file

- **Append decisions, not actions.** One line per thing that got accepted or rejected. A log of every action taken grows without bound and stops being readable; a log of decisions only grows when something was actually decided.
- **`Rejected` is a verbatim quote from the user, not a paraphrase.** The reason matters more than the fact of rejection: "стало из чужого мира" tells the next agent *why* the same idea can't be tried again with different wording; a paraphrase like "user didn't like it" throws that away.
- **Screenshots of approved work go in the project's repository (`<project>/.claude/design-shots/`), never in a scratchpad.** A scratchpad lives for one session; the question "did this drift?" gets asked a month later, against a screenshot that has to still exist.
- **Project memory gets one line — a pointer to this file — nothing more.** If the file's content is also copied into memory, the two copies diverge the first time either one is edited alone. Memory exists so that after a context compaction the orchestrator knows where to look, not so the content has a second home.

## Who reads which section

| Reader | Sections used |
|---|---|
| Brief to the design agent (`references/briefs.md`) | Settings, Signature traits, Rejected |
| The "everything present" check (`references/checks.md`) | the screen's task list, carried in the brief, not this file |
| The "accuracy" check (`references/checks.md`) | Settings — design system, tokens |
| The "product style" check (`references/checks.md`) | Signature traits + the screenshots under Approved |
| The orchestrator after a context loss | In progress, Project pitfalls |

This is why the six sections don't collapse into fewer: each reader needs a different slice, and a reader that only needs `Signature traits` shouldn't have to load `In progress` to get it.
