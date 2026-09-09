# Figma Documentation Page Example

## Page
04 Components

## Frame
Component / Button

## Sections

### Header
- Component name
- Status: draft / ready / stable
- Owner
- Last updated

### Purpose
Button triggers an action or navigates the user to the next step.

### Anatomy
- Container
- Label
- Optional leading icon
- Optional trailing icon
- Loading indicator

### Variants
| Variant | Purpose | Example source |
|---|---|---|
| Primary | Main action | Checkout / Payment |
| Secondary | Alternative action | Onboarding / Step 2 |
| Destructive | Risky action | Settings / Delete account |

### States
| State | Required | Notes |
|---|---|---|
| Default | Yes | Base state |
| Hover | Yes | Pointer platforms |
| Pressed | Yes | Active feedback |
| Focus-visible | Yes | Keyboard navigation |
| Disabled | Yes | Non-interactive |
| Loading | Conditional | Async actions |

### Tokens
| Part | Token | Role |
|---|---|---|
| Container | component.button.container.bg.primary.default | Primary bg |
| Label | component.button.label.color.primary.default | Primary label |
| Radius | component.button.container.radius.md | Container radius |

### Usage rules
- Use one primary button per decision area.
- Do not use destructive and primary styles for the same action hierarchy.
- Do not rely on color alone to communicate destructive actions.
