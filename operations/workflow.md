# Workflow

Git, branch, commit, and PR conventions.

## Branches

- Never commit or push directly to the default branch.
- Naming: `feat/<slug>` | `fix/<slug>` | `chore/<slug>` | `refactor/<slug>`
- One concern per branch. Keep PRs small and focused.

## Starting Work

1. `git status --short --branch` — confirm you are on the default branch or approved task branch.
2. If there are dirty files unrelated to the current task, stop.
3. `git pull origin master`
4. `git checkout -b feat/<slug>`

## Commits

- Typecheck and run focused tests before every commit.
- Never commit with failing tests or type errors.
- One logical change per commit.
- Format: `<type>: <short description>` — e.g. `feat: add task filtering by status`

## Pull Requests

Body must include:
- Summary of what changed and why
- Test results: command and output summary line
- Test plan checklist
- Agent attribution line

Use CI as the authority for the full test suite.

## Merging

- Merge only after the user explicitly approves the PR.
- `{{MERGE_STRATEGY}}`: squash for `fix/` and `chore/`; merge commit for `feat/`.
- After merging: `git checkout master && git pull`

## Questions vs Instructions

A question from the user is not permission to implement. Explain the approach and wait for explicit approval before changing any files.
