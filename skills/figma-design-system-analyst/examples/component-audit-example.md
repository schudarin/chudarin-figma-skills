# Component Audit Example

## Component candidate
Button

## Evidence
- Page: Checkout
- Frame: Payment / Desktop
- Nodes: Button / Primary, Button / Secondary, local button groups
- Usage count: 24 observed button-like elements
- Variables: partial use of `color/action/primary/bg/default`
- Raw values: multiple radius values observed

## Classification
Component with variants and design debt.

## Variants observed
- Primary
- Secondary
- Tertiary/link-like
- Destructive

## States observed
- Default
- Disabled
- Loading in checkout only

## Missing states
- Hover
- Pressed
- Focus-visible

## Causal relationship
Primary buttons appear where the user needs to complete the main step in a decision area. Secondary buttons appear for reversible or lower-priority actions.

## Recommendation
Normalize into a Button component set with variants for hierarchy, size, icon placement, loading, and disabled state.

## Proposed tokens
- color.action.primary.bg.default
- color.action.primary.bg.hover
- color.action.primary.text
- component.button.container.radius.md
- component.button.container.padding.x.md

## Confidence
High
