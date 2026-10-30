---
title: AI 时代的软件开发流程
markmap:
  colorFreezeLevel: 2
  initialExpandLevel: 2
  maxWidth: 320
  spacingHorizontal: 100
  spacingVertical: 10
---

# AI 时代的软件开发流程

## [English](https://cxfydhcg.github.io/ai-coding-era/mindmap.html)

## [个人开发流程](docs/02-individual-workflow.md)

- 确认真实问题与当前行为
- 写清目标、范围、约束和验收
- 小步实现，按风险验证
- 审查、发布、观察与清理
- [任务模板](templates/task-contract.md)

## [团队合作流程](docs/03-team-collaboration.md)

- 按可验证的结果拆任务
- 分清契约、顺序、资源与决策依赖
- 先定接口，再并行
- 假服务提前验证，真实联调不可省
- 点名阻塞与集成负责人
- [依赖地图](templates/dependency-map.md)

## [任务管理](docs/04-task-management.md)

- 优先级看价值、风险与完整成本
- 在制任务数受验证能力约束
- 完成深度先约定，再验收
  - D0 能演示
  - D1 主路径正确
  - D2 边界与失败正确
  - D3 能在真实系统运行
  - D4 结果已观察
- 证据不足不能靠改状态完成
- [完成检查](templates/completion-depth-checklist.md)
- [Backlog 模板](templates/backlog-item.md)

## [组织架构优化](docs/05-organization-structure.md)

- 领域团队持续对结果负责
- 共享平台减少重复劳动与等待
- 按需要补能力，不按人数套组织图
- 写清团队服务与决定边界
- 从反复阻塞定位改进点

## 按需参考

- [核心原则](docs/01-core-principles.md)
- [仓库记忆](docs/06-repository-as-operational-memory.md)
- [记录生命周期实践](docs/08-record-lifecycle.md)
  - 四类记录分别维护
  - 报告 → 审查 diff → 定期维护
  - 发布证据、人工门禁和删除测试
  - [记录政策模板](templates/record-lifecycle-policy.md)
- [小范围试点](docs/07-adoption-roadmap.md)
- [研究与证据边界](docs/00-research-foundation.md)
- [决策模板](templates/decision-record.md)
