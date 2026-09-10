# Controls — links, buttons, panels, pickers

Reached from `references/ux-rules.md`. Read when the screen has a link, a button, a dropdown, a
picker, or any panel that opens.

### Text links get no enlarged tap zone

The 44pt rule is for buttons and fields. Applied to an inline link it inflates the wrapper,
detaches the underline from the text, and breaks the vertical rhythm — set no `minHeight` on link
wrappers.

Note the trap: an accessibility checklist that says "tap zones ≥ 44" is itself what causes this
defect, because the agent applies it to everything interactive. Exclude inline links explicitly when
running that check (`ux/accessibility.md`).

**Read:** link wrappers have no `minHeight`; their height equals the text's.

### Search over a long list is typed into the field itself

A combobox — not a separate search input inside the dropdown. Two inputs for one task make the
focus jump, and the typed text ends up somewhere other than the field being filled.

**Read:** the panel has an input while the trigger field is empty — that combination is the defect.

### Which way a panel opens is arithmetic, not preference

Measure the space below the field to the edge of its container: if it is smaller than the panel, the
panel opens upward, because that is what the browser does. A dropdown drawn downward through the
bottom of a card is a drawing, not a state.

**Read:** container bottom minus field bottom, against the panel's height.

### On touch there is no hover

A control whose meaning is only visible on hover has no meaning on a phone. If a mockup is for
touch, every affordance the user needs must be visible in the resting state; hover styling is an
extra for pointer devices, never the carrier of information.

**Look:** the resting state alone, with no hover layer, and ask what the user can tell from it.
