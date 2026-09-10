# States — empty, loading, error, progress, confirmation

Reached from `references/ux-rules.md`. Read when the screen shows anything that arrives, can be
missing, or can fail — a list, a fetch, a submit, an upload.

`references/checks.md` already requires the error, empty and loading states to be *drawn*. These
rules are about what has to be in them.

### There are three kinds of empty, and they are not interchangeable

**Nothing yet** (first run), **nothing found** (a filter or a search excluded everything), **nothing
left** (the user finished the work). Same list, three different texts and three different actions:
the first teaches, the second offers to widen the filter, the third confirms. One empty state drawn
for all three is the most common defect in this class — and the filter case is the one usually
missing.

**Read:** for each list on the screen, which of the three exist as frames.

### An empty state says what belongs here and offers the one action that fills it

Not "No data". What this place is for, and the single next step. This is the most attentive moment
the user will ever give the screen, and a blank panel spends it on nothing.

**Read:** the empty frame contains a sentence about the purpose and exactly one primary action.

### Loading shows the shape of what is coming

Skeletons that match the real layout — the same rows, the same column widths. A spinner centred in
an empty area throws away everything the layout already knows and makes the jump bigger when the
content lands.

**Look:** put the loading frame and the loaded frame side by side; the blocks should sit in the same
places.

### Reserve the space that arriving content will occupy

Anything asynchronous — an image without fixed dimensions, a count badge, a banner — must have its
space held from the first paint. Content that pushes the layout after the user has already aimed at
something makes them press the wrong thing.

**Read:** every async element has a fixed size or a min-size in the loading frame.
**Blocking:** a layout that shifts under the pointer is a defect, not a rough edge.

### Below a second, no indicator; above ten, a way to leave

Response-time thresholds are old and stable: about 0.1 s reads as instant, about 1 s is where the
user notices a wait, and around 10 s is where attention leaves. So: under a second, showing a
spinner only makes it flash; over a second, show one; over ten, show progress *and* a way to cancel
or leave and come back.

**Read:** for each async action, the expected duration and the indicator chosen for it.

### Progress means a number, not just activity

An indeterminate spinner is honest only when the total is genuinely unknown. Uploads, imports and
multi-step operations know their total — show the step or the count. "Working…" for two minutes is
indistinguishable from a hang.

**Read:** determinate operations show a step or percentage; only unknowable ones spin.

### An error state says what happened, what it means, and what to do next — in place

Three parts, and the retry lives in the same place the failure happened. An error whose only action
is "Go back" strands the user with the work they had already done. Wording is in `ux/copy.md`; this
is about composition.

**Read:** the error frame carries a cause, a consequence and an action; the action is a retry or a
concrete fix, not navigation away.

### A failed action never leaves the screen telling a lie

If a row was removed optimistically and the delete failed, the row comes back — with a message. The
worst outcome is a screen that shows a state the server does not have, because the user will act on
it again.

**Read:** for each optimistic update, what the screen shows when the request fails.
**Blocking:** a screen that displays a state the backend rejected must not ship.

### A toast never carries something the user has to do

It disappears. Anything the user must act on — an error to fix, a decision to make, a conflict to
resolve — lives in the layout. Toasts confirm things that need no response.

**Read:** every toast in the flow is dismissible with no consequence; no toast contains the only
copy of an instruction.

### Success needs its own state only when the result is invisible

A settings screen that saved shows the saved values — that is the confirmation. A form the user is
leaving, a payment, a submission into someone else's queue: there the user cannot see the outcome,
so the screen has to state it.

**Read:** each success state answers "what could the user not otherwise see?" — no answer means the
state is noise.
