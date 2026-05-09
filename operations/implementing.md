# Implementing

How to implement an approved task. Follow these steps in order. Never skip or reorder.

## Before starting

State: "This is ready to implement because..." backed by the approved task details. If you cannot honestly say that, route back to planning.

Require an implementation design before starting if any of these are true:
- The task touches infrastructure, auth, data models, shared middleware, background jobs, or multiple repos
- The task could touch more than five files
- Endpoint shape, storage decisions, auth behaviour, or failure behaviour are unresolved

The implementation design must cover: files touched, API contract, data model, auth behaviour, side effects, failure modes, test plan, and what is out of scope. Get user approval before proceeding.

## Step 1 — Fetch the task

Read the full task from the task system (`tasks.md`). It must be self-contained.

## Step 2 — Repo state check

Before creating a branch or editing any files:

1. Run `git status --short --branch`.
2. If not on the default branch or the approved task branch, stop.
3. If there are dirty files unrelated to this task, stop.
4. Show the user and wait for explicit approval before taking any repo action.

## Step 3 — Existing pattern check

Before writing code:

1. Read the repo's agent entry file.
2. Inspect existing files that implement the same kind of change.
3. State the exact pattern being followed.
4. If a new pattern is needed, stop and get user confirmation first.

## Step 4 — Mark task in-progress

Update the task status to `in-progress` (`tasks.md`).

## Step 5 — Create a branch

```bash
git checkout master && git pull
git checkout -b feat/<slug>
```

Naming: `feat/<slug>` | `fix/<slug>` | `chore/<slug>` | `refactor/<slug>`

## Step 6 — Establish a baseline

1. Typecheck or build.
2. Run existing tests covering the files or feature being changed.

If baseline fails, stop and tell the user.

## Step 7 — Implement

Work through the task acceptance criteria — these are the definition of done.

Commit rules:
- Run typecheck and focused tests before every commit.
- Never commit with failing tests or type errors.
- One logical change per commit.
- Format: `<type>: <short description>`

## Step 8 — Open a PR

When all acceptance criteria are met, create a PR. Body must include: summary, test results line, test plan checklist, agent attribution line. Use CI as the authority for the full test suite.

## Step 9 — Review

Review the PR. Address all flagged issues before proceeding.

## Step 10 — Update feature doc

If this task changes behaviour in `features/`, update that doc. Describe current functionality only — no migration history.

## Step 11 — Mark task done

After the PR is merged and the user approves, update the task status to `done` (`tasks.md`).

## Step 12 — Return to default branch

```bash
git checkout master && git pull
```
