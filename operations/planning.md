# Planning

How to plan a new feature or implementation slice. Follow this order exactly.

## Step 1 — Listen

Ask the user to describe what they want to build. Read existing docs and code first so any questions are specific. Do not ask generic questions.

If the user references an existing feature doc or prior discussion, read those first and summarise the current understanding. Ask only for decisions that materially affect scope or task creation.

For broad or exploratory ideas: do not jump to models or implementation. Ask how the feature fits the overall product, what the user wants to achieve, and what future workflows might be affected. Be proactive — infer likely needs from context and propose options for the user to decide between.

## Step 2 — Propose scope

Propose:
- The system shape if the idea points beyond one simple change
- What the feature does (one paragraph)
- The first implementation slice, labelled as a slice when narrower than the full capability
- Which repos are affected

Wait for the user to approve or adjust. Never write feature docs or create tasks before scope is confirmed.

## Step 3 — Write or update the feature doc

Only after scope is confirmed, create or update the owning doc in `features/`. Use `features/_template.md` as the starting point for new docs.

If the feature doc already exists, update it only if the approved behaviour changes. Do not create a duplicate doc for a slice.

## Step 4 — Propose task breakdown

Present the task breakdown to the user. Wait for explicit approval before creating anything.

- One repo touched: one task, no parent.
- Multiple repos: one parent task (container only) with one subtask per repo. If an API repo is involved, it always comes first as it defines the contract.
- Each task must be completable in a single session with clear, verifiable acceptance criteria.
- Follow the task format in `tasks.md`.

## Step 5 — Create tasks

Only after the user approves, create tasks using the system in `tasks.md`.

For multi-repo features:
1. Create the parent task first and note its ID.
2. Create each subtask linked to that parent ID — never create them as flat top-level tasks.
3. Verify the parent-child relationship is set before proceeding.

Task title rules:
- Title is plain text only — e.g. `Add search to task list`.
- Never prepend type prefixes to the title (`[FEAT]`, `[FIX]`, etc.). The change type is captured as a tag or label per the system defined in `tasks.md`, not in the title.

Report back with created task IDs and confirm whether feature docs were created, updated, or unchanged.
