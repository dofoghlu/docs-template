# Agent Setup

Instructions for creating a project docs repo from this template. Follow the relevant path below. Delete this file from the project repo once setup is complete.

---

## Step 1 — Discovery

Before creating anything, discuss the following with the user:

| Topic | What to establish |
|---|---|
| Project name | Short name used for the repo (`{name}-docs`) |
| Description | What the project is and who it's for |
| Repos | Names and purpose of each code repo in the project |
| Default branch | `main` or `master` |
| Task system | Which backend (own-api / jira / linear / github-issues / none) and project ID |
| Personas | Does the project have multiple distinct user types? |
| Merge strategy | squash / merge commit / rebase |

Do not create any files until the user has confirmed these details.

---

## Path A — New project

### 1. Create the repo

```
{name}-docs/
├── AGENT.md
├── tasks.md
├── docs-guide.md
├── product/
│   ├── overview.md
│   └── architecture.md
├── features/
└── operations/
    ├── planning.md
    ├── implementing.md
    └── workflow.md
```

Add `product/personas.md` if the project has multiple user types.

### 2. Fill in content

Copy each file from this template and replace all `{{PLACEHOLDER}}` values using the information gathered in discovery.

### 3. Configure environment variables

Follow the instructions in `tasks.md` to configure environment variables and point the user to where values need to be entered.

### 4. Set up agent entry file

Create an entry file for your agent in the workspace root — the parent folder that contains the docs repo alongside the project's code repos. Point it at `{name}-docs/AGENT.md`. The workspace root is not part of the docs repo.

### 5. Delete this file

Remove `agent-setup.md` from the project repo.

---

## Path B — Existing project with docs

### 1. Audit existing docs

Read all existing documentation. Categorise every doc:

- **Cross-cutting** — product concepts, feature behaviour, workflows, architecture → belongs in the docs repo, map to template structure
- **Repo-specific** — implementation patterns, code conventions, setup instructions for a specific repo → does not belong in the docs repo; note it for moving to that repo's own agent entry file
- **Doesn't fit** — flag to the user before proceeding

### 2. Create the repo structure

Same structure as Path A. Migrate cross-cutting content into the appropriate files. Do not carry over repo-specific content.

### 3. Fill in gaps

Any information not covered by the existing docs should be filled in using the discovery details from Step 1.

### 4. Report to the user

Before finishing, tell the user:
- What was migrated and where it landed
- What repo-specific docs were identified and which repos they should move to
- What was flagged as not fitting and needs a decision

### 5. Configure environment variables

Follow the instructions in `tasks.md` to configure environment variables and point the user to where values need to be entered.

### 6. Set up agent entry file

Same as Path A Step 4.

### 7. Delete this file

Remove `agent-setup.md` from the project repo.
