# Documentation Guide

How to maintain these docs. Read before creating, moving, or deleting any file.

## Structure

```
{project}-docs/
├── AGENT.md          — agent entry point and governance
├── tasks.md          — task system configuration
├── docs-guide.md     — this file
├── product/          — what the project is and how it works
├── features/         — what each feature does
└── operations/       — how to do specific things
```

## Where Things Belong

- **`product/`** — product-level concepts, architecture, and system understanding. Stable. Changes only when the product fundamentally shifts.
- **`features/`** — one file per durable user-facing feature. Describes current behaviour only.
- **`operations/`** — repeatable procedures: how to plan, how to implement, how to release.

## Rules

- Update the owning doc instead of creating a new one.
- Merge small additions into the relevant parent doc.
- Do not create separate docs for screens, platforms, implementation tasks, or small extensions of an existing feature.
- Create a new feature doc only when the capability is stable, durable, and has its own behaviour or lifecycle.
- Do not split feature docs by repo, platform, or implementation phase — one feature, one doc.
- Keep root files short. They point to the right source of truth; they do not duplicate it.
- Do not create new folders without explicit approval.

## Feature Doc Format

```markdown
---
status: in-progress | done
---

# Feature Name

## What
What this feature does (current state only — no migration history).

## Why
The reason this feature exists and the value it provides.

## Examples
Concrete real-world examples that make the feature easy to understand.

## Scope
The product behaviours this capability includes.

## Out of scope
Adjacent behaviours explicitly not included yet.
```

Feature docs describe product behaviour only. Do not include repo names, file paths, endpoint shapes, data schemas, UI layout detail, or migration history.

## Updating This Guide

Update `docs-guide.md` only when the documentation system itself changes — not for normal feature additions or content changes.
