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

### 3. Set up workspace-level agent entry files

Each AI agent needs an entry file at the **workspace root** (the parent directory that contains the docs repo and code repos). These files tell the agent where to find its instructions.

Create the relevant files for the agents being used on this project:

**CLAUDE.md** — Claude reads this via `@` reference:
```
@{project}-docs/AGENT.md
```

**GEMINI.md** — Gemini reads this as prose:
```
Read {project}-docs/AGENT.md before doing any work in this project.
All rules and workflows in that file apply to you.

[Add any Gemini-specific notes here, e.g. no watch mode for tests]
```

**AGENTS.md** — Codex reads this as prose:
```
Read {project}-docs/AGENT.md before doing any work in this project.
All rules and workflows in that file apply to you.
Treat any mention of a specific AI agent name in those docs as referring to you.
```

### 4. Configure environment variables

Each agent has its own local config file for injecting credentials. These files are gitignored — never committed.

Set the variables listed in `AGENT.md` under Environment Variables using the agent's native config mechanism:

- **Claude:** `.claude/settings.local.json`
- **Codex:** `.codex/config.toml`
- **Gemini:** `.gemini/settings.json`

### 5. Adding a new agent in future

Create a root entry file for the agent pointing at `{project}-docs/AGENT.md`. Add any agent-specific quirks to that file only — not to the shared docs.
