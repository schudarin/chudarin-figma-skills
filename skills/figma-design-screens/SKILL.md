---
name: figma-design-screens
description: Use when designing, building, or changing a product screen, flow, or component in Figma — new screens, states, redesigns, or edits to already-approved work. Use when a design result was rejected, when a screen must match an existing product, or when starting design on a product with no visual direction yet. Not for auditing or documenting an existing design system without changing screens — that is figma-audit-design-system.
---

# Figma Design Screens

## Overview

The process is universal. Everything product-specific is discovered in the project, never assumed.

First action, every time: check `<project>/.claude/design.md`. No file → follow `references/setup.md`.

Second action, before any read or write in Figma: make sure you have a link to the frame or page the
task is about. No link in the request and none recorded in `design.md` → ask for one in a single
line and wait. Guessing which file and page the user means is the most expensive mistake available
here: everything after it is built in the wrong place.

| Project state | Where style comes from | Skipped |
|---|---|---|
| Design system exists | the design system is law | direction, typography, palette phases |
| No design system, screens exist | existing screens in Figma | same |
| Neither | external references, curated by the user | nothing |

## Improving a product that already ships

When the task is to fix a live product rather than add screens to it, the current interface is captured and audited **before** anything is redrawn — `references/audit-existing.md`. That audit is what every later claim of "this is better" gets measured against, so a wrong note there becomes a wrong screen two phases on: on a 64-note audit one note in four was wrong on the first pass, and the errors were in the retelling, not in the observation.

Skipping the audit doesn't remove the phase, it relocates it — without a recorded defect you end up arguing whether the old screen was broken at all, with no evidence on either side.

## Default: one screen

Default deliverable: **one screen, done right.** Variants are produced only when (1) the user asked in words, (2) the product has no chosen direction yet and this is discovery, or (3) you see a genuine fork — then you ask in one line and do not decide for the user.

When there is one screen, uncertainty cannot be absorbed by quantity. If the brief contains a fork you would have to resolve on the user's behalf, name it to the user in one line **before** building.

## Minimum skill stack

| Task type | Visual skill to load |
|---|---|
| Mobile screens | a mobile-UI skill |
| Web, landing pages | a web / visual-design skill |
| Motion, transitions | a motion skill |
| Charts, stats | a dataviz skill |

Visual skills come from outside this pack, so their names differ from shelf to shelf. Read the list
of skills actually available in this host and pick **one**, matched to the task type. If the shelf
has none, say so and work without one — never invent a skill name or load a plausible-sounding
substitute.

Every designer agent also loads `figma-use` (mandatory before any `use_figma` call — the Figma plugin skill in Claude Code, or the MCP resource `skill://figma/figma-use/SKILL.md` in other agents) and `figma-plugin-api-rules`. Load one visual skill, not the whole shelf — more lenses on one task dilute focus rather than adding rigour.

## Working a screen

| Step | What happens |
|---|---|
| 1 | Gather the style source: `design.md`, the design system, existing screens, or references |
| 2 | Write the brief, check it against `references/briefs.md` |
| 3 | Agent builds: intent in words, then Figma, then self-critique and a revision pass |
| 4 | Three checks from `references/checks.md`, before the user sees it — the Accuracy pass includes the copy and control rules in `references/ux-rules.md` |
| 5 | Show the user |
| 6 | User hand-finishes it; the resulting screenshot becomes the saved one |

Step 6 is the norm, not an exception — expect the user to finish the screen by hand.

A brief must point to a source to clone, not describe anatomy: a cloned node guarantees identical spacing, styles, and bindings; a text description invites the agent to author from scratch, and that drifts.

## Editing an approved screen

Edit **one element at a time** — never a batch of fixes applied together.

A visual difference from grid, alignment, or component convention can look exactly like "an identifiable defect against an existing standard" and still be the product's own signature trait, not a lag behind one. Without the signature-traits list and the saved screenshot in `design.md` (format: `references/state.md`) in front of you, you cannot tell which — and it isn't your call to make from the visual alone.

If `design.md` is missing, has no signature-traits section, or has no saved screenshot of this screen, that absence **blocks** changing the screen's visual properties — it does not clear you to change them. An empty or missing list means the constraints are unknown, not that there are none. Ask the user about the specific property in one line, or fill the list first.

You already refuse to silently rewrite approved copy under cover of a UI fix. Extend that same caution to geometry, radii, and control shape: treat them as product decisions until the signature-traits list says otherwise.

A property the user didn't name is not part of the request. "Make active elements distinguishable" is not a mandate to touch radius, control shape, spacing, or alignment — solve it with a change that leaves unnamed properties alone. If you believe an unnamed property genuinely has to change to solve the task, that belief is the trigger to ask in one line before touching it, not a reason to treat it as already in scope.

"Confirming element by element burns the window" undercounts the other side: a batch that turns out wrong can't be partly kept — it all reverts to the saved screenshot, costing the window plus the rework. Check each change against the screenshot and the signature-traits list before applying it, one element at a time.

## Models

| Task type | Model tier |
|---|---|
| Composition, critique, synthesis | the strongest reasoning model available to the host |
| Mechanics: variables, text styles, clones, renames, moves | a cheaper, faster model — no design judgment is involved |

Model names differ per host (Claude Code, Codex, others); pick by tier, not by name.

If the model you need is unavailable — limit, outage, missing access — stop and ask before switching, not after. Disclosing a swap once it's done isn't the same as asking first: by the time there's something to disclose, the hour is already spent on the wrong tool.

The output of a mismatched model is not a reversible draft. It isn't low-stakes because it "can be regenerated or touched up later" — regenerating is redoing the work, and a touch-up can't fix a composition built against the wrong design system.

"The user said to keep going" authorised the work, not the downgrade. Someone stepping away for an hour approved continued progress on the task, not on a weaker tool — the moment the model becomes unavailable is exactly when to interrupt, not push through.

The same rule covers any other condition swapped mid-task — a hung Figma bridge, an agent cut off by a limit, a missing tool: say so immediately, before the result comes back rejected.

## Common Mistakes

| Situation | What happened | Why it failed |
|---|---|---|
| Editing an approved screen | Six textbook-correct fixes classified as "defects against an existing standard," applied in one pass | One was a signature trait, not a defect; the batch was rejected and reverted from the saved screenshot |
| Model unavailable | Switched to a weaker model silently, calling it "low-stakes and reversible... touched up later" | Nothing was touched up; every result of that phase was rejected outright |
| Redesigning an audited flow | Three frames documented defects of a modal date picker; the fix replaced the picker entirely, and the frames were about to be filled with the calendar anyway | The defect's object no longer existed — the frames had to be reassigned to the new states, not populated with a control nobody would build |
| Writing a value list | Country list written from memory into the mockup | Two of the countries had no flag in the design system and one was named differently — invisible in the mockup, a missing asset at build time |
| A decision was reversed | The screen was changed, the note under it was not | A mockup whose own caption praises the state it no longer has is worse than an uncaptioned one — search the notes for the decision's keywords whenever it flips |

## Red Flags — stop

- "These are identifiable defects against an existing standard" — you don't have the signature-traits list open, so you can't actually judge that.
- "Confirming element by element burns the window" — a reverted batch costs more than asking would have.
- "It's low-stakes and reversible, can be regenerated or touched up later" — that's the sentence that precedes a full rejected day.
- "The user already said to proceed" — proceeding was authorised, the downgrade wasn't.
- "There's no signature-traits list, so nothing's off-limits" or "this property is basically part of what they asked for" — empty means unknown, not unrestricted, and unnamed means not requested.
- "The note says so" — a quarter of the audit notes were wrong on the first pass, and they were written by you. Re-read the note against the screen before designing to it.
- "Nothing found on the re-read" — on a set over ~20 notes the observed rate is one defect in four, so an empty result is a claim about your re-read, not about the notes.
- "The defect is recorded, so this frame needs that control drawn" — check whether your fix removed the object the defect lived on. If it did, the frame is reassigned, not filled.
