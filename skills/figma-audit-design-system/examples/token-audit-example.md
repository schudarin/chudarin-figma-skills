# Token Audit Example

## Finding
Multiple blue values are used for primary actions.

## Evidence
| Raw value | Source | Usage | Existing variable | Count |
|---|---|---|---|---:|
| #0057FF | Checkout / Payment | Primary CTA | none | 7 |
| #0062FF | Onboarding / Step 1 | Primary CTA | Blue/500 | 4 |
| #004FE6 | Settings / Save | Primary CTA hover | none | 3 |

## Interpretation
The same semantic role is being expressed by multiple close raw values.

## Proposed tokens
| Layer | Token | Value/reference | Role |
|---|---|---|---|
| Primitive | color.blue.500 | #0057FF | Core brand/action blue |
| Primitive | color.blue.600 | #004FE6 | Darker action blue |
| Semantic | color.action.primary.bg.default | color.blue.500 | Primary action background |
| Semantic | color.action.primary.bg.hover | color.blue.600 | Primary action hover background |
| Component | component.button.container.bg.primary.default | color.action.primary.bg.default | Button primary default |

## Recommendation
Replace raw primary CTA colors with semantic action tokens. Keep component tokens only for Button if variants/states require independent control.

## Confidence
High
