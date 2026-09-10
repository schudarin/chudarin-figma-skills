# Accessibility — while drawing, not afterwards

Reached from `references/ux-rules.md`, with no exemption: every screen has text, targets and
states. These are the design-time rules — what to do while the screen is being built.

**The audit-time twin** is `figma-audit-design-system/references/accessibility-checklist.md`: the
same ground as yes/no questions for auditing a file someone else drew. When a rule here changes,
change the question there too — two copies that drift are worse than one.

### Tap targets: 44pt for buttons and fields

Buttons, fields, icon buttons, rows that act as controls. **Inline text links are excluded** — see
`ux/controls.md`; enlarging them is a defect this checklist itself causes when applied blindly.

**Read:** height of every control node against 44; links exempt.

### Contrast covers non-text too

Text contrast, and also borders, icons, focus rings and selected states. A selected state carried
only by a 1px border of low contrast is not a state anyone can see.

**Read:** foreground and background token values through the same contrast formula. **Look:** the
selected and focused states next to their neutral neighbours.

### Focus-visible exists and isn't styled away

Every interactive element has a focus state in the component, and it survives whatever custom
styling the product applies. A design that ships without one hands keyboard users a screen with no
cursor.

**Read:** the component has a focus variant; it is not identical to the default.

### Keyboard order follows visual order

The order fields and controls appear in the layout is the order they will be reached. A field
placed out of flow (absolute positioning, a column reordered visually) creates a tab sequence that
jumps around the screen.

**Look:** walk the layout top to bottom and say the order out loud; compare with the DOM-ish order
the layout implies.

### Colour is never the only carrier of meaning

Status, errors, selection, required-ness: each needs a second channel — text, an icon, a shape, a
position. A red border with no message fails this and `ux/forms.md` at once.

**Look:** desaturate the frame mentally and ask what is still distinguishable.

### Disabled content stays legible

Disabled is not invisible. The user has to be able to read what they cannot use, or they can't tell
what to do to unlock it. See `ux/forms.md` on never building this from opacity.

**Read:** the disabled label's contrast is still above the text threshold.

### Icon-only controls carry a name

An icon button with no visible label needs its accessible name documented — in the component's
description or an annotation, so the developer has something to implement.

**Read:** the icon-only component's `description` names the action.

### Motion is reducible

Any animation the screen depends on has a still equivalent. If the mockup specifies motion, it also
specifies what happens under a reduced-motion preference.

**Look:** the frame as a still — does it still communicate the same thing?
