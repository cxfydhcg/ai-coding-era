# AI 时代的软件开发流程

[English](README.md) | **简体中文**

这里记录我在 AI 辅助开发中的实践、踩坑，以及对团队协作的思考，供你参考和改造。

我关心的是：当代码更容易生成，怎样让一个人、一支团队和一个组织更可靠地交付软件？下面分四篇讲清楚，每篇都给出可以尝试的做法。

**共同前提：目标、计划、进度、决定和验证证据都落在仓库里。换人或换 Agent 后，接手者应能从仓库知道做什么、做到哪里、下一步是什么，不依赖原聊天或某个人的记忆。** [如何做到可接手](docs/06-repository-as-operational-memory.md)。

## 四条主线

| 从哪里开始 | 核心问题 | 可以带走什么 |
| --- | --- | --- |
| [个人开发流程](docs/02-individual-workflow.md) | 如何把需求交给 AI，并确认做对了？ | 定义任务、分步实现、验证和交付的日常循环 |
| [团队合作流程](docs/03-team-collaboration.md) | 多人、多 Agent 怎样配合？ | 按结果拆任务，先定接口，再并行与集成 |
| [任务管理](docs/04-task-management.md) | 先做什么，同时做多少，怎样算完成？ | 优先级、在制任务上限、完成深度与证据 |
| [组织架构优化](docs/05-organization-structure.md) | 哪些责任留在团队，哪些能力集中建设？ | 领域责任、共享平台、协作边界和改进信号 |

## 一个已经落地的例子

在 `smrtlite-android` 和 `bp_employee_app` 中，我把当前行为、变更原因、延后问题和需求契约分开存放，再用检查脚本和定期巡检维护它们。

这让下一次开发有地方找上下文，也让过期记录有退出条件。两个仓库的发布格式和兼容要求不同，复用时需要调整。[记录生命周期实践](docs/08-record-lifecycle.md)展示具体做法和测试边界。

## 按需查阅

- [核心原则](docs/01-core-principles.md)：各篇共用的判断标准。
- [仓库即交接](docs/06-repository-as-operational-memory.md)：换人或换 Agent 后，如何独立继续。
- [从小范围试起](docs/07-adoption-roadmap.md)：选一个问题，观察是否真的改善。
- [研究与证据边界](docs/00-research-foundation.md)：哪些有研究支持，哪些是实践建议。

模板：[任务](templates/task-contract.md) · [完成检查](templates/completion-depth-checklist.md) · [依赖](templates/dependency-map.md) · [Backlog](templates/backlog-item.md) · [决策](templates/decision-record.md) · [记录政策](templates/record-lifecycle-policy.md)。按需要取用，不必全部填写。

也可以看[中文交互导图](https://cxfydhcg.github.io/ai-coding-era/)或[英文导图](https://cxfydhcg.github.io/ai-coding-era/mindmap.html)。本地打开 `mindmap.zh-CN.html`；修改导图源文件后，运行 `npm ci` 和 `npm run mindmap` 重建。

这里的团队与组织建议需要结合自身环境验证；两个项目中的有效做法，不足以证明适用于所有团队。
