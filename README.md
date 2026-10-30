# Software Development in the AI Era

**English** | [简体中文](README.zh-CN.md)

These notes collect my experience with AI-assisted development, mistakes along the way, and ideas for team collaboration. Use and adapt what fits your work.

The question behind them: as code becomes easier to generate, how can individuals, teams, and organizations deliver software more reliably? Four articles cover different parts of that problem.

## Four starting points

| Article | Question | What you can use |
| --- | --- | --- |
| [Individual workflow](docs/en/02-individual-workflow.md) | How do I delegate to AI and establish correctness? | A daily loop for defining, implementing, verifying, and delivering a change |
| [Team collaboration](docs/en/03-team-collaboration.md) | How do people and agents work together? | Outcome-based slices, agreed interfaces, parallel work, and integration |
| [Task management](docs/en/04-task-management.md) | What comes first, how much starts, and what counts as done? | Priorities, work-in-progress limits, completion depth, and evidence |
| [Organization design](docs/en/05-organization-structure.md) | Which responsibilities stay local and which capabilities are shared? | Domain ownership, platforms, team boundaries, and improvement signals |

## One implemented example

In `smrtlite-android` and `bp_employee_app`, I separate current behavior, change rationale, deferred problems, and implementation contracts, then maintain them with checks and scheduled sweeps.

This gives the next development session somewhere to recover context and gives obsolete records a retirement rule. The repositories have different release formats and compatibility requirements. The [record lifecycle walkthrough](docs/en/08-record-lifecycle.md) explains the mechanism and the tests needed when adapting it.

## Reference when needed

- [Core principles](docs/en/01-core-principles.md): shared decision rules.
- [Repository memory](docs/en/06-repository-as-operational-memory.md): where information belongs and when it changes or leaves.
- [Start with a small trial](docs/en/07-adoption-roadmap.md): test whether a change helps.
- [Research and evidence boundaries](docs/en/00-research-foundation.md): research findings versus practice recommendations.

Templates: [task](templates/en/task-contract.md) · [completion](templates/en/completion-depth-checklist.md) · [dependencies](templates/en/dependency-map.md) · [backlog](templates/en/backlog-item.md) · [decision](templates/en/decision-record.md) · [record policy](templates/en/record-lifecycle-policy.md). Use only the fields you need.

Browse the [English mind map](https://cxfydhcg.github.io/ai-coding-era/mindmap.html) or [Chinese mind map](https://cxfydhcg.github.io/ai-coding-era/). Open `mindmap.html` locally; after editing the map sources, run `npm ci` and `npm run mindmap` to rebuild both editions.

The team and organization recommendations need local validation. Experience in two projects does not establish a universal workflow.
