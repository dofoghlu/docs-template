# Documentation Guide

How to maintain these docs. Read before creating, moving, or deleting any file.

## Structure

```
{project}-docs/
├── AGENT.md          — agent entry point and governance
├── tasks.md          — task system configuration
├── docs-guide.md     — this file
├── product/          — what the project is and how it works
│   └── personas.md   — user personas (optional, delete if not needed)
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

Use `features/_template.md` as the starting point for every new feature doc. It contains inline guidance and a review checklist.

Three sections, all required:

- **What** — what the feature does in its current state. No history, no implementation detail.
- **Why** — who needs this and why. Reference a persona from `product/personas.md` if the project defines them.
- **Examples** — 2-3 concrete real-world examples specific enough to picture exactly how the feature works.

Feature docs describe product behaviour only. Never include repo names, file paths, endpoints, schemas, API detail, UI layout, or migration history.

## Updating This Guide

Update `docs-guide.md` only when the documentation system itself changes — not for normal feature additions or content changes.
