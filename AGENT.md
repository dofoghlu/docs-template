# Agent Guide

Entry point for all AI agents working in this project. Read this before doing any planning, implementation, or documentation work.

## Reading Order

1. `product/overview.md` — what this project is and why it exists
2. `tasks.md` — task system: which backend, how to create and update tasks
3. `operations/workflow.md` — git, branch, commit, and PR conventions
4. `operations/planning.md` — how to plan a feature
5. `operations/implementing.md` — how to implement a task
6. `docs-guide.md` — how to maintain documentation
7. Relevant `features/*.md` when working on a specific feature

## Always-On Rules

These apply at all times without being asked:

- Never commit or push directly to the default branch. Always work on a feature branch.
- Never start implementation without explicit user approval.
- Never create a branch or write code before a task exists in the task system.
- A question or observation from the user is not permission to implement. Explain the approach and wait for explicit approval before changing any files.
- Never make decisions about field names, data models, architecture, or behaviour unilaterally — propose and wait for confirmation.
- Update `features/` when feature behaviour changes.
- Keep docs current. Do not preserve outdated structure or planning history.

## Environment Variables

The following variables must be available in your agent's local config. Never print their values in responses, logs, docs, or task output.

| Variable | Purpose |
|---|---|
| `TASK_API_URL` | Base URL for the task system (if using own API) |
| `TASK_API_KEY` | Auth key for the task system (if using own API) |

Add project-specific variables here as needed.

## Documentation Ownership

| File / Folder | Owns |
|---|---|
| `AGENT.md` | Agent governance (this file) |
| `tasks.md` | Task system configuration |
| `docs-guide.md` | Documentation maintenance rules |
| `product/` | Product understanding and architecture |
| `features/` | Durable feature behaviour |
| `operations/` | Repeatable workflows and procedures |
