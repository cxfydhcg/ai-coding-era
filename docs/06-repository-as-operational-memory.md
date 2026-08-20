# 从代码仓库到运行记忆

## 面向人类与 AI Agent 协作的软件生命周期

AI coding agent 已经可以参与需求分析、代码实现、review、测试、文档和维护。但在长期软件项目中，真正困难的通常不是生成下一段代码，而是正确回答：系统现在为什么这样工作？哪些行为是当前事实，哪些只是未来计划？某段兼容逻辑什么时候可以删除？一个新发现的问题是否属于当前任务？

这些答案往往分散在聊天、issue、PR、文档、监控系统和个人记忆中。人类团队过去依赖长期关系与口头交流来弥补这种分散；临时进入任务的 Agent 没有这种连续记忆。

因此，AI-native 软件生命周期的关键不是让模型记住更多聊天，而是把必要上下文转化为可版本控制、可检索、可验证、可以随生命周期移动的 artifact。

## Repository 的角色需要扩大

Repository 不应只回答“源代码是什么”，还应帮助人和 Agent 回答：

- 系统当前做什么；
- 当前应该如何开发、测试与运行；
- 已经批准的未来变化是什么；
- 哪些问题已知但暂不处理；
- 哪些关键取舍仍影响今天；
- 哪些生产证据允许发布或删除旧能力。

这不意味着所有组织知识都进入 Git。人员、客户、财务和敏感运营数据应留在适当的受控系统中。更准确的原则是：

> Repository-native，而不是 repository-only。

Repository 保存与软件行为直接相关的权威入口、规则、契约和证据链接，并作为人类与 Agent 的共同控制平面。

## 按时间语义分离知识

Agent 很容易把“计划实现”误解成“当前已经支持”，也容易把旧 change log 当作当前操作说明。解决办法不是增加更多文字，而是为不同 artifact 规定清晰职责。

| Artifact | 时间语义 | 回答的问题 |
| --- | --- | --- |
| Source code / schema | Present | 系统实际上做什么？ |
| Current-state docs | Present | 现在应如何理解、使用和运行？ |
| Task contract / requirement | Approved future | 接下来承诺实现什么？ |
| Backlog | Deferred future | 已知但暂未承诺的问题是什么？ |
| Decision record | Relevant past | 为什么选择当前方向？ |
| Git / PR | Full history | 具体如何变化和讨论？ |
| Production evidence | Operational reality | 真实环境是否支持我们的判断？ |

时间边界可以概括为：

```text
requirement       → 已批准的未来
current docs      → 当前
decision/change   → 仍有价值的过去
Git / PR          → 完整历史证据
production signal → 运行现实
```

同一段信息不应永久复制在所有位置。需求实现后，详细的未来意图应压缩为当前行为和必要的历史原因；完整过程由 Git 保留。

## Repository memory 不是一篇巨型文档

一个不断增长的总说明会快速变成噪声。更有效的运行记忆具有以下特征：

- 信息靠近其适用的代码和领域；
- 全局规则很少，只保存真正跨领域的约束；
- 每个 artifact 有 owner、时间语义和淘汰方式；
- 稳定 ID 和链接连接生命周期，而不是复制全文；
- Agent 按任务渐进检索，不一次加载所有内容；
- 自动检查验证结构、链接和确定性规则。

文档的价值不由长度决定，而由它是否改变正确决策决定。

## 工作需要在生命周期中移动

一个问题可以经历以下状态：

```text
discovered → deferred → contracted → implemented → observed → retired
```

例如，review 中发现一个真实但范围外的问题：它先进入 backlog；当团队决定执行，它被提升为任务契约；实现完成后，当前行为进入 docs，关键原因进入 decision record；生产证据确认旧路径不再需要后，兼容代码和过期文档被删除。

每个阶段应有一个有效事实源。Promotion 不是复制，而是状态迁移。稳定 ID 可以保留追溯性，而无需让多个文档独立漂移。

## 按工作形态选择载体

任务路由不应只看规模：

| 特征 | 合适载体 |
| --- | --- |
| 当前 diff 内可以完成并验证 | Fix now |
| 可独立描述但当前不应扩大范围 | Backlog |
| 需要共享范围、接受标准、阶段、rollout 或 release gate | Requirement / initiative |

小改动可能包含不可逆的数据风险，大型重构也可能只是机械变化。决定流程重量的应是未知性、协作边界、风险和证据需求。

## 自动发现不授予权限

Agent 比人更容易系统扫描相邻问题，这是优势，也可能制造 scope creep。可靠的规则是：

> Agent 可以自动发现、分类、提供证据和建议；扩大范围、改变产品语义、接受风险和操作生产环境仍需要相应授权。

一个 review finding 应明确处置：不是问题、当前修复、形成 backlog，或提升为 requirement。真实问题不应留在临时聊天里；但保存它也不表示当前任务必须处理它。

## Policy 与 Mechanism 必须配套

“请保持文档更新”只是政策。要形成可重复行为，还需要机制，例如：

- 局部 Agent instructions 或 skills；
- task、backlog 和 decision 模板；
- CI 中的链接、schema 与索引验证；
- 路径到相关 backlog 的检索；
- release tag 与 requirement 状态检查；
- 生产版本、迁移和旧流量报告。

并非所有规则都适合自动化。产品判断和风险接受保留在人类层；格式、结构、确定性约束与证据收集尽可能交给机器。

## 生产现实必须进入生命周期

代码合并只能证明 repository 改变，不能证明真实环境已经安全迁移。涉及混合版本客户端、数据库迁移、离线队列或兼容 API 时，完成条件必须包含生产证据。

一个兼容层的 removal gate 可以要求：

```text
对每一个仍登记且未退役的客户端：

版本达到要求
AND 升级后成功启动
AND 必要迁移已经应用
AND 旧格式流量在观察窗口内消失
AND 回滚支持窗口已经结束
```

不同旧机制需要不同淘汰策略：请求兼容 adapter 可以在 fleet gate 后删除；dual read/write 要等待所有旧 writer 消失和队列排空；数据库 repair migration 可能因为旧备份恢复而必须永久保留。

这说明删除不是单纯的代码清理，而是一个基于证据的生命周期决定。

## 与已有实践的关系

这套模型不是替代所有已有方法：

- Spec-driven development 负责在实现前定义期望行为；
- Docs-as-code 负责让文档与代码共同版本化和审查；
- ADR 保存长期重要的技术取舍；
- GitOps 让声明式配置驱动基础设施和部署；
- Issue tracker 负责跨团队排期、协作与可见性。

Repository operational memory 将它们放入更完整的流动中：

```text
Discovery
→ Triage
→ Contract / Spec
→ Implementation
→ Verification
→ Release
→ Production observation
→ Retirement
```

其新增重点是跨任务上下文连续性、信息的时间语义、Agent 的权限边界，以及生产证据驱动的淘汰。

## 渐进式落地

无需先设计一套庞大的目录体系。可以按以下顺序开始：

1. 为关键领域建立准确的 current-state docs；
2. 使用一个简短任务契约定义结果、范围和验证；
3. 建立 fix now / backlog / requirement 三种路由；
4. 用稳定 ID 连接任务、PR、决策与发布；
5. 自动验证格式、链接和确定性规则；
6. 为临时兼容逻辑记录 owner 与 removal gate；
7. 定期压缩过期上下文并删除达到条件的旧机制。

## 结论

AI Agent 的主要长期限制不是代码生成，而是上下文持续性。真正成熟的 AI-native SDLC，不是保存越来越多文字，而是让必要信息以正确的语义存在、在正确的阶段移动，并在不再有价值时被删除。

> AI-native、repository-native SDLC，是一种将需求、延后工作、当前行为、历史原因、运行门禁和淘汰规则表达为版本化 artifact 的软件生命周期。Agent 可以发现并执行这些规则，而重要的产品、风险与生产决策仍由人类负责。
