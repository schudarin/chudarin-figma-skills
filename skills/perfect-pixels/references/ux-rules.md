# Copy and control rules

Product-agnostic rules earned by having a specific screen rejected for each one. They are checkable
by reading the file, so they belong to the Accuracy pass in `references/checks.md` — not to taste.

## Copy

**One sentence takes no full stop; two or more take one after each.** "Enter a valid email address"
— no stop. "Invalid code. Please try again." — a stop after each. A single label ending in a full
stop reads as a fragment of prose rather than a piece of interface. Checkable by script: find text
nodes with exactly one sentence and a trailing stop.

**A placeholder is not a value.** Bind it to the muted text token, never the primary one. A country
placeholder left on the primary token read as an already-selected country, and the field looked
filled when it was empty.

## Controls

**Text links get no enlarged tap zone.** The 44pt rule is for buttons and fields. Applied to an
inline link it inflates the wrapper, detaches the underline from the text, and breaks the vertical
rhythm — set no `minHeight` on link wrappers. Note the trap: an accessibility checklist that says
"tap zones ≥ 44" is itself what causes this defect, because the agent applies it to everything
interactive. Exclude inline links explicitly when running that check.

**Search over a long list is typed into the field itself** — combobox — not into a separate search
input inside the dropdown. Two inputs for one task make the focus jump, and the typed text ends up
somewhere other than the field being filled. Symptom to look for: the panel has an input while the
trigger field is empty.

**Which way a panel opens is arithmetic, not preference.** Measure the space below the field to the
edge of its container: if it is smaller than the panel, the panel opens upward, because that is what
the browser does. A dropdown drawn downward through the bottom of a card is a drawing, not a state.

**A container that holds one step of a flow gets a minimum height, not a fixed one.** The success
step of a flow had a third of the content of the form before it, and the card collapsed — the layout
jumped on the last step. A minimum equal to the form's height holds short steps steady while error
states are still free to grow.

## Validation

**The submit button stays enabled, including on an empty form.** A disabled button states that
something is wrong and refuses to say what; the user is left guessing which field is the problem. Let
them press it and answer with the reason.

**Then the answer has to be words.** On press, every unfilled field takes an error outline *and its
own message* — "Enter your first name", not a bare red border. WCAG 3.3.1 requires the error to be
identified in text. Group fields that form one logical value (a date entered as day / month / year)
take one message between them, not three.

Keep the disabled variant in the component for the states that genuinely have no cause to explain —
loading, no permission — and never build that state out of opacity: a translucent black button dims
its background and its label at the same time, so the label disappears and the state still doesn't
read as inactive. Use dedicated tokens.

## Data entry

**Prefer typing to picking for values with a wide range.** A date of birth behind a modal calendar
that opens on the current month costs 20+ years of paging, and the read-only field forbids the
faster route. Three fields — day, a month select, year — remove the modal, and with it every defect
the modal had.

**A label that vanishes on input takes the context with it.** Turn the floating label on as soon as
the field holds a value: reviewing a filled form otherwise shows "Vietnam", "Sarah", "14" with no
indication of which field is which.
