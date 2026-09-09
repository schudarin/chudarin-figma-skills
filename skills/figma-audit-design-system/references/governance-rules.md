# Governance Rules

Use this reference when the user asks how to maintain, version, approve, or evolve the design system.

## Change types

Classify changes as:

- Patch: typo, documentation clarification, non-breaking variable description.
- Minor: new component, new variant, new semantic token, additive documentation.
- Major: renamed token, removed token, changed semantic meaning, removed component, changed component behavior.

## Approval rules

Require review for:

- New semantic or component tokens.
- New public component variants.
- Any change that affects accessibility.
- Any change that affects product screens across multiple flows.
- Deprecation or migration proposals.

## Component lifecycle

Use statuses:

```txt
proposed
experimental
ready
stable
deprecated
removed
```

## Token lifecycle

Use statuses:

```txt
proposed
active
deprecated
removed
```

Every deprecated token must include:

- Replacement token
- Affected components or screens
- Migration deadline or priority
- Reason for deprecation

## Contribution workflow

1. Identify need from product work.
2. Check existing components, patterns, and tokens.
3. Document evidence and usage count.
4. Propose addition or change.
5. Review with design-system owner and implementation stakeholders.
6. Add documentation and examples.
7. Publish change with changelog.
8. Track adoption and migration.

## Changelog format

```md
## Version x.y.z - YYYY-MM-DD

### Added
- New tokens/components/patterns.

### Changed
- Updated rules, variants, or values.

### Deprecated
- Items that should no longer be used and replacements.

### Removed
- Removed items.

### Migration notes
- Required updates to existing files or screens.
```
