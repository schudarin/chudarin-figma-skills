# Copy and control rules — index

Product-agnostic rules, each one earned by having a specific screen rejected for it. This file is
the routing table; the rules themselves live in `ux/*.md`.

**Two moments read this set, and they read it differently.**

- **Writing the brief** (`references/briefs.md`, block 5) — *before* anything is drawn. Take the
  rows that match what this screen will contain and paste the rules themselves into the brief. A
  rule the agent meets for the first time at check time has already cost a rebuild.
- **The Accuracy pass** (`references/checks.md`, check 2) — *after* it is drawn. The same rules,
  read as criteria.

## Routing: what to read when

| The screen contains | Read |
|---|---|
| any interface text — labels, messages, button text, placeholders | `ux/copy.md` |
| a field, a form, validation, one step of a multi-step flow | `ux/forms.md` |
| a link, a button, a dropdown, a picker, a panel that opens | `ux/controls.md` |
| saving, cancelling, deleting, acting on a selection | `ux/actions.md` |
| anything at all | `ux/accessibility.md` |

Load only the rows that match — except the last one, which has no exemption: every screen has
text, targets and states.

## How each rule is written

Principle first, then how to verify it. Verification is one of two kinds, and the Accuracy pass
treats them differently:

- **Read** — verifiable by reading node properties or numbers. A finding names the node and the
  number; no taste is involved.
- **Look** — verifiable only on the render. Say what you looked at and what you saw; "looks fine"
  is not a result.

A rule with no verification line is not finished. Write one before adding it.

## Growing this set

A rule belongs here when it is true **outside** the product it came from. A rule that is true only
for one product is a signature trait: it goes into that project's `design.md`
(`references/state.md`, "Signature traits"), never here — putting it here would push one product's
taste onto every other product this skill touches.

When a topic file outgrows roughly 120 lines, split it and add a row to the table above.
