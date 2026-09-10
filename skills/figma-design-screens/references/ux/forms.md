# Forms — fields, validation, data entry, flow steps

Reached from `references/ux-rules.md`. Read when the screen has a field, a form, validation, or one
step of a multi-step flow. Message wording itself is in `ux/copy.md`.

## Validation

### The submit button stays enabled, including on an empty form

A disabled button states that something is wrong and refuses to say what; the user is left guessing
which field is the problem. Let them press it and answer with the reason.

**Read:** the submit button's state in the empty-form frame is not `Disabled`.

### Then the answer has to be words

On press, every unfilled field takes an error outline *and its own message* — never a bare red
border. WCAG 3.3.1 requires the error to be identified in text. Group fields that form one logical
value (a date entered as day / month / year) take one message between them, not three.

**Read:** each field in the error frame has a text message; grouped fields have exactly one.

### Never build a disabled state out of opacity

Keep the disabled variant in the component for the states that genuinely have no cause to explain —
loading, no permission. A translucent black button dims its background and its label at the same
time, so the label disappears and the state still doesn't read as inactive. Use dedicated tokens.

**Read:** the disabled variant's fill and label are bound to disabled tokens; `opacity` is 1.

## Data entry

### Prefer typing to picking for values with a wide range

A date of birth behind a modal calendar that opens on the current month costs 20+ years of paging,
and the read-only field forbids the faster route. Three fields — day, a month select, year — remove
the modal, and with it every defect the modal had.

**Look:** count the interactions from the resting state to a value at the far end of the range.

### A label that vanishes on input takes the context with it

Turn the floating label on as soon as the field holds a value: reviewing a filled form otherwise
shows "Vietnam", "Sarah", "14" with no indication of which field is which.

**Read:** in the filled-form frame every field still shows its label.

## Flow steps

### A container that holds one step of a flow gets a minimum height, not a fixed one

The success step of a flow had a third of the content of the form before it, and the card collapsed
— the layout jumped on the last step. A minimum equal to the form's height holds short steps steady
while error states are still free to grow.

**Read:** the step container has `minHeight` set and is not `FIXED` on that axis.
