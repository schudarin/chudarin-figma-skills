# Copy — interface text

Reached from `references/ux-rules.md`. Read when the screen carries any text: labels, messages,
button text, placeholders, headings.

### One sentence takes no full stop; two or more take one after each

"Enter a valid email address" — no stop. "Invalid code. Please try again." — a stop after each. A
single label ending in a full stop reads as a fragment of prose rather than a piece of interface.

**Read:** find TEXT nodes whose content is exactly one sentence and ends in a stop.

### A placeholder is not a value

Bind it to the muted text token, never the primary one. A country placeholder left on the primary
token read as an already-selected country, and the field looked filled when it was empty.

**Read:** the placeholder node's bound colour token — muted, not primary.

### An error message names the action, not the failure

"Enter your first name", not "This field is invalid" and not a bare red border. The user needs the
next move, not a verdict. The behavioural half of this rule — which fields get a message and when —
is in `ux/forms.md`.

**Read:** every error string starts from what to do; WCAG 3.3.1 requires the error to be identified
in text at all.

### A button says what it does: verb plus object

"Save changes", "Delete project", "Send invite" — not "OK", not "Submit", not "Yes". The label has
to make sense read on its own, because that is how it is read: in a confirmation dialog the user's
eye goes to the buttons before the sentence above them.

**Read:** every button label contains a verb; a pair of buttons is distinguishable without the
surrounding text.

### The two buttons in a dialog are never both a form of yes

"Delete" and "Cancel", not "Yes" and "No" on a question that can be misparsed. And the destructive
one is never the one that reads as the default — see the ladder in `ux/actions.md`.

**Read:** the dialog's buttons name their two different outcomes.

### Sentence case in the interface, and one convention throughout

Pick sentence case or title case and hold it across labels, headings and buttons. Mixed casing reads
as several products stitched together, and it is the single most visible inconsistency in an
otherwise clean screen.

**Read:** the casing of every label and heading on the screen, against `design.md`.

### The interface does not blame the user and does not apologise at length

"That code has expired" rather than "You entered an invalid code"; one short sentence rather than a
paragraph of regret. The user wants the next step, not an assignment of fault or a performance of
sympathy.

**Read:** error and empty-state text for second-person accusations and for apologies longer than a
clause.

### A heading names the thing, not the action that got you there

"Payment method" rather than "Add your payment method here" — the screen already is the place; the
heading is a label for it. Long instructional headings push the actual content below the fold and
duplicate what the fields already say.

**Read:** each heading is a noun phrase.
