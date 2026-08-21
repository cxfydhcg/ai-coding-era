# 任务契约

[English](en/task-contract.md) | **简体中文**

> 建议 ID：`DOMAIN-001`。删除所有提示文字后再进入 Ready。

## Outcome

要改变的用户或系统结果是什么？使用可观察行为描述，不要只描述要修改的代码。

## Evidence

- 当前问题的复现、日志、数据或代码证据：
- 相关链接与时间：

## Scope

### In scope

- （填写）

### Out of scope

- （填写）

## Constraints

- 产品与兼容约束：
- 数据、安全与隐私约束：
- 性能与运行约束：
- 不可破坏的公共契约：

## Acceptance criteria

- [ ] （填写）
- [ ] （填写）

## 完成深度

- 目标深度（D1 主路径 / D2 边界与失败路径 / D3 真实系统可运行 / D4 结果被验证）：
- 显式不做的深度与原因：
- 未做部分的 backlog 条目与 owner：
- 检查表：[完成深度检查表](completion-depth-checklist.md)

## Verification plan

- 自动检查：
- 人工验证：
- 生产观察：
- 尚无法覆盖的风险：

## 依赖与解耦

- 被哪些任务阻塞（阻塞点是哪个接口或决定）：
- 阻塞了哪些任务：
- 依赖类型（契约 / 真实顺序 / 资源环境 / 决策）：
- 解耦方式（契约先行 / mock / expand-migrate-contract / feature flag / 反向切片）：
- 计划集成点与联合验证责任人：
- 地图：[依赖与切片地图](dependency-map.md)

## Responsibility and authority

- Accountable owner：
- Executor：
- Independent validator（如需要）：
- Release authority（如需要）：
- Agent 可以自主完成：
- 必须暂停并请求决定：

## Rollout and rollback

- 发布方式：
- 监控信号：
- 停止/回滚条件：
- 回滚方法：

## Completion evidence

- 实现/PR：
- 验证结果：
- 生产结果：
- 文档与后续清理：
