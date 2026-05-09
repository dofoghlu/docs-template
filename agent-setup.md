# Agent Setup

Instructions for creating a new project docs repo from this template.

## What to create

A project docs repo is a standalone git repository. Its root contains everything in this template, filled in for the specific project. There is no subfolder nesting — all content lives at the root.

## Steps

### 1. Create the repo structure

Copy the structure of this template:

```
{project}-docs/
├── AGENT.md
├── agent-setup.md
├── tasks.md
├── docs-guide.md
├── product/
│   ├── overview.md
│   └── architecture.md
├── features/
├── operations/
│   ├── planning.md
│   ├── implementing.md
│   └── workflow.md
└── README.md
```

### 2. Fill in project-specific content

Search for `{{PLACEHOLDER}}` across all files and replace each one:

| Placeholder | Meaning |
|---|---|
| `{{PROJECT_NAME}}` | Short name of the project |
| `{{PROJECT_DESCRIPTION}}` | One-paragraph description |
| `{{TASK_BACKEND}}` | `own-api` / `jira` / `linear` / `github-issues` / `none` |
| `{{PROJECT_ID}}` | Project ID or key in the task system |
| `{{REPO_NAME}}` | Repository name(s) |
| `{{REPO_PURPOSE}}` | What each repo owns |
| `{{MERGE_STRATEGY}}` | `squash` / `merge commit` / `rebase` |

In `tasks.md`, keep only the section matching the chosen backend and delete the others.

### 3. Configure environment variables

Set the variables listed in `AGENT.md` under Environment Variables using your agent's native config mechanism. These are credentials — store them in your agent's local config, never in the docs repo.

### 4. Agent entry files

Agent entry files (e.g. `CLAUDE.md`, `GEMINI.md`, `AGENTS.md`) are not part of the docs repo. They belong in the workspace root — the parent folder that contains the docs repo alongside the project's code repos. Each agent knows how to set up its own entry file; point it at `{project}-docs/AGENT.md`.
