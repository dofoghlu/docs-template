# docs-template

A reference template for project documentation repos. AI agents use this to create and structure docs for a specific project.

## How to use

An AI agent reads `agent-setup.md` to understand how to create a new project docs repo from this template.

## Structure

```
docs-template/
├── AGENT.md              — agent entry point: reading order, always-on rules, env vars
├── agent-setup.md        — how to create a project docs repo from this template
├── tasks.md              — task system config (own-api and Jira variants)
├── docs-guide.md         — documentation maintenance rules
├── product/
│   ├── overview.md       — what the project is
│   └── architecture.md   — stable technical patterns
├── features/             — one file per durable feature
└── operations/
    ├── planning.md       — how to plan a feature
    ├── implementing.md   — how to implement a task
    └── workflow.md       — git, commit, and PR conventions
```
