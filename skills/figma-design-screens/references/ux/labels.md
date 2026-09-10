# Labels — naming buttons, actions and links

Reached from `references/ux-rules.md`. Read when the screen has a control the user has to read
before pressing: a button, a menu item, a link, a dialog's two answers.

Sentence-level craft — punctuation, voice, error structure — is in `ux/copy.md`. This file is about
the shortest strings in the product, which are also the most read.

### A button says what it does: verb plus object

"Save changes", "Delete project", "Send invite" — not "OK", not "Submit", not "Yes". The label has
to make sense read on its own, because that is how it is read: in a confirmation dialog the user's
eye goes to the buttons before the sentence above them.

**Read:** every button label contains a verb; a pair of buttons is distinguishable without the
surrounding text.

### The object goes in the label only when it isn't already next to it

"Add" is enough when the thing being added is named right there — the section heading, the adjacent
row, the column. "Add manager" is needed when the button sits away from its subject, on a list page
whose title is at the other end of the screen. Repeating a word the eye already caught costs
attention and makes the label longer than the button.

**Read:** for each add/create button, whether its object is visible within the same block.

### You cannot create a person

"Create" is for things that do not exist until the product makes them — a report, a rule, a
segment. A human being — a manager, a client, a courier — already exists; they are **added** to the
system. "Create a manager" reads as manufacturing a colleague, and users notice.

**Read:** every "create" label against whether its object exists in the world independently of the
product.

### The button's tier follows the weight of what it starts

A primary "New …" that opens a whole page of settings is not the same control as an inline "Add"
that attaches an existing thing to a list, and neither is the tertiary "Add" that makes a trivial
entity right there with no follow-up. Same word, three different weights — and the tier is what
tells the user which one they are about to get.

**Read:** for each add/create control, what happens after the press, against the tier it uses.

### One primary per context; secondaries may repeat

The primary action is singular — if a second action wants the same emphasis, one of them isn't
primary. Secondary and tertiary controls may appear several times in one context; that is what they
are for. See `ux/principles.md` on why two accents cancel each other.

**Read:** the count of primary-tier controls per screen region.

### Cancel is a noun; so is anything that only navigates

An action button carries a verb because it does something. A button that takes you somewhere, or
that means "never mind", is named for the place or the state — "Cancel", "Settings", "Back" — not
"Go to settings". Mixing the two conventions makes the user read every label twice to work out
which kind it is.

**Read:** action buttons are verbs, navigation and dismissal are nouns, consistently.

### The two buttons in a dialog name their two outcomes

"Delete" and "Cancel", not "Yes" and "No" on a question that can be misparsed — and never two
labels that both read as agreement. The destructive one is never the one styled as the default; the
ladder in `ux/actions.md` decides how much friction it needs on top of that.

**Read:** the dialog's buttons name different outcomes and the destructive one is not the default.

### Link text marks exactly the part that opens

Underline the words that describe the destination, not the whole sentence and not a bare "here".
The user's eye uses the link text as the promise of what they will land on, so it has to be the
noun phrase for that thing.

**Read:** each link's text against the title of what it opens.

### In explanatory text, a link opens in a new tab

A hint, a footnote, a help line: the user is in the middle of a task, and following the link must
not take the task away. In flow text that is itself the task, the same-tab link is correct — the
distinction is whether the user was doing something else when they read it.

**Read:** each link in explanatory copy is marked as opening a new tab, with the affordance that
says so.

### Don't put the brand name in the interface when the interface has more than one brand

A product served under several names — white-label, a second brand, a partner edition — cannot call
itself by one of them in its own UI. Write the generic word for what it is ("the system", "the
account", "the app") and keep the brand for the places outside the product where it is true.

**Read:** the screen's text for the product's own name; a hit is a defect wherever a second brand
exists or is planned.
