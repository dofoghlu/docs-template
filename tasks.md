# Task System

This file defines the task management system for this project. Agents read this to know how to create, update, and query tasks.

## Configuration

**Backend:** `{{TASK_BACKEND}}`
Replace with one of: `own-api` | `jira` | `linear` | `github-issues` | `none`

**Project:** `{{PROJECT_ID}}`

---

## Own API

> Keep this section if Backend is `own-api`. Delete the others.

**Base URL:** `$TASK_API_URL`
**Auth header:** `X-API-Key: $TASK_API_KEY`

### List tasks

```bash
curl -s "$TASK_API_URL/api/v2/tasks?status=in-progress" \
  -H "X-API-Key: $TASK_API_KEY"
```

### Create a task

```bash
curl -s -X POST "$TASK_API_URL/api/v2/tasks" \
  -H "X-API-Key: $TASK_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Task title",
    "project": "{{PROJECT_ID}}",
    "status": "todo",
    "tags": ["{{REPO_TAG}}"],
    "details": "Full task description"
  }'
```

### Update task status

```bash
curl -s -X PATCH "$TASK_API_URL/api/v2/tasks/{{TASK_ID}}" \
  -H "X-API-Key: $TASK_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"status": "in-progress"}'
```

Valid statuses: `todo` | `in-progress` | `done` | `blocked`

---

## Jira

> Keep this section if Backend is `jira`. Delete the others.

**Base URL:** `$JIRA_URL`
**Auth:** `$JIRA_EMAIL` / `$JIRA_API_TOKEN` (Basic auth, base64 encoded as `$JIRA_AUTH`)
**Project key:** `{{JIRA_PROJECT_KEY}}`

### List tasks

```bash
curl -s "$JIRA_URL/rest/api/3/search?jql=project={{JIRA_PROJECT_KEY}}+AND+status!=Done" \
  -H "Authorization: Basic $JIRA_AUTH" \
  -H "Content-Type: application/json"
```

### Create a task

```bash
curl -s -X POST "$JIRA_URL/rest/api/3/issue" \
  -H "Authorization: Basic $JIRA_AUTH" \
  -H "Content-Type: application/json" \
  -d '{
    "fields": {
      "project": { "key": "{{JIRA_PROJECT_KEY}}" },
      "summary": "Task title",
      "issuetype": { "name": "Task" }
    }
  }'
```

### Update task status

Get available transitions first:

```bash
curl -s "$JIRA_URL/rest/api/3/issue/{{ISSUE_KEY}}/transitions" \
  -H "Authorization: Basic $JIRA_AUTH"
```

Apply a transition:

```bash
curl -s -X POST "$JIRA_URL/rest/api/3/issue/{{ISSUE_KEY}}/transitions" \
  -H "Authorization: Basic $JIRA_AUTH" \
  -H "Content-Type: application/json" \
  -d '{"transition": {"id": "{{TRANSITION_ID}}"}}'
```

---

## Task Format

Task descriptions must be self-contained. Someone picking up a task cold must know exactly what to build, where, and what done looks like.

```
Context: 1-2 sentences explaining what this is and why it exists.

Repo: {{REPO_NAME}}
Type: feat | fix | chore | refactor

What to build:
Specific detail — file paths, field names, endpoint shapes. Not vague goals.

Accepts:
- Explicit, verifiable done criteria.

Refs:
- Actual file paths to follow as patterns.

Depends: task this blocks on, or "none"
```

## Rules

- Create tasks only after the user approves the task breakdown.
- Never create a branch or write code before a task exists.
- Mark a task `in-progress` before creating a branch.
- Mark a task `done` only after the PR is merged and the user approves.
- Never print API key values in responses, logs, or task output.
