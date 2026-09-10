# Navigation — where the user is, how they leave, what container to use

Reached from `references/ux-rules.md`. Read when the screen sits inside a flow, opens over
something, or is one of several places the user moves between.

### Modal, sheet or page — decided by the task, not by the size of the content

A **modal** interrupts and demands a decision before anything else continues; use it when the
answer really is required now. A **sheet** is for a short task that keeps the context visible
behind it. A **page** is for work with its own address that the user may leave and return to, or
share. The frequent mistake is a modal holding a full form: it cannot be linked to, cannot be
resumed, and traps the user between finishing and losing the input.

**Read:** for each overlay, which of the three it is, and why the task requires that container.

### Every overlay has exactly one obvious way out, and it never destroys work silently

Close, cancel, escape, the backdrop — however many ways there are, they agree on what happens to
the input. A backdrop click that discards a half-filled form is data loss with no confirmation;
either it does not discard, or it asks (the ladder in `ux/actions.md`).

**Read:** what each exit does with unsaved input; all exits agree.
**Blocking:** an exit that silently discards user input.

### Back returns, it does not re-enter

Back from a detail lands on the list at the position the user left, with their filter and scroll
intact. Back after a submit does not re-submit or show a stale form. A back that rebuilds the
previous screen from scratch loses everything the user set up to get there.

**Read:** for each back path, what state is preserved — position, filter, tab, input.
*Mobile: also the system back gesture, which cannot be removed and will be used.*

### The user can always tell where they are

The active item in the navigation is marked in a way that survives the theme and does not rely on
colour alone (`ux/accessibility.md`). One screen, one active marker: two highlighted items means
neither is trusted.

**Read:** the active state exists in the navigation component and is set on exactly one item per
frame.

### A flow says how long it is before it starts

Multi-step means a step count or a progress bar from step one — "Step 2 of 4", not a wizard whose
length is discovered by walking it. And a step the user can leave says whether returning resumes or
restarts.

**Read:** the step indicator is present on the first step, not only on later ones.

### Onboarding is skippable, and skipping is not punished

Anything explanatory has a way past it, and taking that way does not hide the feature it was
explaining. A tour the user cannot dismiss is a tour they will click through blindly, which teaches
them nothing and costs them trust.

**Read:** the onboarding frames carry a skip affordance; the product is usable after skipping.

### Deep entry is a real entry point

Any screen reachable by link, notification or search can be the first screen of the session — so it
cannot depend on state that only the preceding screen would have set. Design what it shows when the
user arrives cold.

**Read:** for each screen, what it shows when opened directly, with no history behind it.

### Breadcrumbs earn their place only below three levels of depth

At two levels they duplicate the back button. Below three they start to carry real orientation
value, and then they need to be truncated from the middle rather than the end, because the current
page and the root are the two parts that matter.

**Read:** the depth of the hierarchy before adding them.
