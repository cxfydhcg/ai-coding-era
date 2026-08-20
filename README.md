# Evolving Software Development in the AI Coding Era

**English** | [简体中文](README.zh-CN.md)

## Visual navigation

Prefer an overview to opening documents one by one?

- [Open the interactive English mind map](https://cxfydhcg.github.io/ai-coding-era/mindmap.html) — expand, collapse, zoom, and follow links
- [打开中文交互式思维导图](https://cxfydhcg.github.io/ai-coding-era/)
- [Browse the clickable map directly on GitHub](MINDMAP.md)
- [Download the offline interactive Markmap preview](mindmap.html?raw=1), then open it locally

The preview is generated with the open-source [Markmap](https://github.com/markmap/markmap) project. After cloning the repository, open `mindmap.html`, or run `npm install` and `npm run mindmap` to rebuild both offline previews. Use `npm run mindmap:watch:en` for a live English preview while editing.

## How individual development, team collaboration, task management, and team architecture should change

AI is rapidly lowering the cost of turning an idea into code, but the fundamental constraints of software engineering have not disappeared. Requirements can still be unclear. Systems still run in production. Someone must still own failures. Future developers and agents must still maintain today's code.

The central question of AI coding is therefore not merely how to write better prompts. It is:

> When implementation capacity becomes cheap and abundant, how should individuals, teams, and companies redesign responsibility, workflows, task systems, and organizational structure?

This repository presents an approach that can be adopted incrementally. It is not a manual for a specific tool or codebase. It is a guide to the durable principles of software development in an AI-assisted environment.

## Core propositions

1. **AI increases implementation throughput; it does not automatically improve problem definition or result verification.**
2. **Humans increasingly move from primary code producers toward owners of intent, constraints, review, and production outcomes.**
3. **Agents may discover, implement, and verify, but discovery does not grant authority to expand scope or change production state.**
4. **A repository should become versioned operational memory, not merely a source-code container.**
5. **A task needs an outcome, boundaries, verification, and accountability; a prompt is not a task contract.**
6. **A team's advantage comes from high-quality feedback loops, not the volume of generated code.**
7. **Removing obsolete code, compatibility layers, and stale context is part of the lifecycle.**

## Reading guide

| Topic | Question | Document |
| --- | --- | --- |
| Research foundation | Which claims are research-backed, and which require local validation? | [Research foundation and evidence boundaries](docs/en/00-research-foundation.md) |
| Principles | What should remain invariant in AI-assisted development? | [Core principles](docs/en/01-core-principles.md) |
| Individual lifecycle | How does one person work with agents from problem to production evidence? | [Individual software development lifecycle](docs/en/02-individual-workflow.md) |
| Team lifecycle | How do people and agents collaborate across one value stream? | [Collaborative software development lifecycle](docs/en/03-team-collaboration.md) |
| Task management | How is work selected, queued, authorized, verified, and closed? | [Task management](docs/en/04-task-management.md) |
| Team architecture | How should domain ownership, platforms, enablement, and governance be structured? | [Team architecture](docs/en/05-organization-structure.md) |
| Repository memory | How does temporary discussion become executable long-term context? | [From code repository to operational memory](docs/en/06-repository-as-operational-memory.md) |
| Adoption | How does an organization move from individual trials to organizational capability? | [Adoption roadmap](docs/en/07-adoption-roadmap.md) |

## A minimal operating model

```text
Humans define outcomes, constraints, and risk boundaries
                         ↓
Agents retrieve context, propose plans, and implement
                         ↓
Automation verifies behavior, quality, and policy
                         ↓
Humans review consequential judgments and authorize release
                         ↓
Production evidence flows back into tasks, documentation, and retirement decisions
```

One person may hold several responsibilities in a small organization; a larger company may distribute them across teams. The titles are optional. The responsibilities are not.

## Keep the four levels distinct

```text
Individual SDLC: how one person turns one task into a trustworthy result
Team lifecycle: how a team moves from a user problem to production learning
Task system: how work is selected, queued, authorized, verified, and closed
Team architecture: how the company designs long-term ownership, platforms, and team interactions
```

The individual lifecycle optimizes an execution. Team collaboration optimizes an end-to-end delivery. Task management optimizes flow. Team architecture optimizes the organization's long-term ability to create value. They influence one another, but one diagram cannot replace all four.

## Ready-to-use templates

- [Task contract](templates/en/task-contract.md): make work executable before assigning it to a person or agent.
- [Backlog item](templates/en/backlog-item.md): preserve a real issue that should not expand the current scope.
- [Decision record](templates/en/decision-record.md): retain the durable “why” behind a consequential choice.

## What this approach does not claim

- Not all organizational knowledge belongs in a repository. Sensitive personnel, customer, and financial information belongs in the appropriate controlled systems.
- Not every small change needs a long specification. Process weight should follow uncertainty, coordination cost, and risk.
- Agents do not replace accountable owners. Execution can be delegated; accountability cannot.
- Maximum unsupervised automation is not the goal. High-risk actions require explicit authority and verifiable evidence.

## Status

This is an evolving bilingual practice guide. The English and Chinese editions use matching numbers and structure so that research, examples, evaluation methods, and implementation guidance can evolve together.
