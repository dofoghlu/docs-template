# Implementing

How to implement an approved task. Follow these steps in order. Never skip or reorder.

## Before starting

State: "This is ready to implement because..." backed by the approved task details. If you cannot honestly say that, route back to planning.

Require an implementation design before starting if any of these are true:
- The task touches infrastructure, auth, data models, shared middleware, background jobs, or multiple repos
- The task could touch more than five files
- Endpoint shape, storage decisions, auth behaviour, or failure behaviour are unresolved

The implementation design must cover: files touched, API contract, data model, auth behaviour, side effects, failure modes, test plan, and what is out of scope. Get user approval before proceeding.

**Exception — planning just concluded:** If implementation follows directly from a completed planning session in the same conversation, the design and approval are already satisfied. Do not re-request approval or re-present the design. Proceed to Step 1.

## Step 1 — Fetch the task

Read the full task from the task system (`tasks.md`). It must be self-contained.

## Step 2 — Repo state check

Before creating a branch or editing any files:

1. Run `git status --short --branch`.
2. If there are dirty files unrelated to this task, stop and show the user.
3. If on a clean but unrelated branch, switching to the default branch is safe — state what you are doing and proceed. Do not treat a clean branch switch as a blocker.
4. If the repo state is ambiguous or risky, stop and wait for explicit user approval before taking any action.

## Step 3 — Existing pattern check

Before writing code:

1. Read the repo's agent entry file.
2. Inspect existing files that implement the same kind of change.
3. State the exact pattern being followed.
4. If a new pattern is needed, stop and get user confirmation first.

## Step 4 — Mark task in-progress

Update the task status to `in-progress` using the system in `tasks.md`. Do this before creating a branch or touching any files — not after.

If the task has a parent task, mark the parent `in-progress` at the same time. Never leave a parent at `todo` while a subtask is being worked on.

## Step 5 — Create a branch

```bash
git checkout <default-branch> && git pull
git checkout -b feat/<slug>
```

Naming: `feat/<slug>` | `fix/<slug>` | `chore/<slug>` | `refactor/<slug>`

## Step 6 — Establish a baseline

1. Typecheck or build.
2. Run existing tests covering the files or feature being changed.

If this task depends on changes in another repo that are not yet merged, verify that the dependency repo is running from the correct branch — not just that its port is alive. A port liveness check cannot catch a branch mismatch. Check the running server's branch and restart from the correct location if it is wrong.

If baseline fails, stop and tell the user.

## Step 7 — Implement

Work through the task acceptance criteria — these are the definition of done.

Commit rules:
- Run typecheck and focused tests before every commit.
- Never commit with failing tests or type errors.
- One logical change per commit.
- Format: `<type>: <short description>`

## Step 8 — Open a PR

When all acceptance criteria are met, create a PR. Body must include: summary, test results line, test plan checklist, attribution line. Use CI as the authority for the full test suite.

## Step 9 — Review

Review the PR. Address all flagged issues before proceeding.

## Step 10 — Update feature doc

If this task changes behaviour in `features/`, update that doc. Describe current functionality only — no migration history.

## Step 11 — Mark task done

After the PR is merged and the user approves, update the task status to `done` using the system in `tasks.md`.

If the task has a parent, check whether all sibling subtasks are now done. If they are, mark the parent `done` as well.

## Step 12 — Return to default branch

```bash
git checkout <default-branch> && git pull
```
