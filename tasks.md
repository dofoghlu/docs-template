# Task System

## Backend

**System:** `{{TASK_BACKEND}}`
Supported: `own-api` | `jira` | `linear` | `github-issues` | `none`

**Project:** `{{PROJECT_ID}}`

## Connection

How to connect to this task system and how task metadata maps to its fields.

```
Base URL:   {{TASK_API_URL or equivalent}}
Auth:       {{auth mechanism}}

Change type (feat / fix / chore / refactor) → {{label / tag / work type / etc.}}
Repo / area                                 → {{label / tag / component / etc.}}
```

For known systems (Jira, Linear, GitHub Issues) the agent uses its own knowledge of the API. For a custom API, document the relevant endpoints here.

## Task Format

Task descriptions must be self-contained. Someone picking up a task cold must know exactly what to build and what done looks like.

```
Context:
1-2 sentences explaining what this is and why it exists.

What to build:
Specific detail — file paths, field names, endpoint shapes. Not vague goals.

Acceptance Criteria:
- Explicit, verifiable done criteria.

Refs:
- Actual file paths to follow as patterns. (optional)
```

## Environment Variables

Identify the variables required to connect to this task system and add them to the table in `AGENT.md` under Environment Variables. Configure them in your agent's local config and point the user to where the values need to be entered. Never store values in the docs repo.

## Rules

- Create tasks only after the user approves the task breakdown.
- Never create a branch or write code before a task exists.
- Mark a task in-progress before creating a branch.
- Mark a task done only after the PR is merged and the user approves.
- Never print credentials in responses, logs, or task output.
