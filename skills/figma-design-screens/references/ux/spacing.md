# Spacing — the scale, the grid, and when to leave it

Reached from `references/ux-rules.md`. Read whenever a number is about to be typed into a padding,
a gap, a margin or a position.

### Every distance comes from the named scale, not from a number

XS / S / M / L / XL — or whatever the product calls its steps. The designer picks a step, not a
value, because a step survives a change to the scale and a value does not. A screen assembled from
raw numbers cannot be retuned later without touching every node on it.

**Read:** each padding and gap is bound to a spacing token; raw numbers are findings
(`figma-plugin-api-rules/references/variables-and-tokens.md` for the binding mechanics).

### The step is 8, and that is not arbitrary

An 8-based step divides cleanly into the great majority of real screen widths, which makes fitting
a layout to a device arithmetic rather than negotiation. It also survives fractional scaling: at
1.5× an odd number lands on a half pixel — 5 becomes 7.5 — and the renderer rounds it somewhere you
did not choose. And a step of 8 is far enough apart to be told apart by eye, so whoever builds the
screen measures less and guesses right more often.

Why not 4 or 6: too many options, and the difference between neighbouring steps stops being
visible, so the scale stops constraining anything. Why not 10: too few, and the layout gets coarse.

**Read:** the distinct spacing values on the screen, each divisible by 8.

### 4 is the exception, and it is written down

Half a step exists for the cases that genuinely need it — an icon against its label, a badge on an
avatar, optical alignment of two shapes with different weights. It is not the general-purpose
escape hatch, and a screen where half-steps outnumber steps has no scale at all.

**Read:** count the 4s; each one should have a reason you can name.

### Align to the grid on both axes, including the text

Vertical rhythm and horizontal alignment come from the same grid, and left-aligned text starts on
it. An element placed by eye between two grid positions is the thing that makes a careful screen
look slightly wrong in a way nobody can point at.

**Look:** the frame with the layout grid visible.
**Read:** integer coordinates — a node at `x=132.5` splits its edges across two pixels
(`references/checks.md`, Accuracy).

### Density is a decision, not a leftover

The same scale can be applied tightly or loosely, and which one this product uses is a product
decision — a data-dense admin table and a marketing page cannot share a density and both be right.
Where the product has more than one, the screen says which it is using rather than mixing them.

**Read:** the step choices on this screen against the density recorded in `design.md`.
