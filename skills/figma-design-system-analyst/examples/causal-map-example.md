# Causal Map Example

## Element
Card / Interactive

## Observed in
- Dashboard / Summary
- Product list / Item
- Account / Subscription

## Product scenario
The product needs to group related content and allow the user to open more detail.

## User intent
Scan a collection of items and choose the relevant one.

## Interface decision
A bordered surface container separates each item from the page background. Consistent padding and title/body hierarchy make comparison easier.

## System implication
Create a Card component with variants:

- Default
- Interactive
- Selected
- Warning

## Tokens
- color.bg.surface
- color.border.default
- color.border.focus
- component.card.container.radius.default
- component.card.container.padding.md
- component.card.title.typography
- component.card.body.typography

## Rule
Use Card for grouped, related content. If the card is clickable, the whole interactive area must have hover, pressed, and focus-visible states.

## Evidence
- Page: Dashboard
- Frame: Summary / Desktop
- Page: Product list
- Frame: Catalog / Desktop
- Usage count: 12 card-like containers

## Confidence
High
