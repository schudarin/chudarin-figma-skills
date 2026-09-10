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
