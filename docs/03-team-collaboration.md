# 团队协作的软件生命周期

[English](en/03-team-collaboration.md) | **简体中文**

个人生命周期保证一次执行可信；团队协作生命周期保证产品、设计、工程、安全、运行以及多个 Agent 能围绕同一个结果工作，不在职能交接中丢失意图。

软件开发不是“产品写需求、开发写代码、QA 找问题、运维上线”的接力赛。更好的模型是一个稳定团队共同拥有从用户问题到生产学习的完整价值流。

## 团队协作总览

```text
用户与业务发现
  → 共同定义目标
  → 技术探索与任务契约
  → 切片、接口与 ownership
  → 并行实现和持续集成
  → 风险导向审查
  → 渐进发布
  → 生产学习
  → 淘汰与系统改进
```

每个阶段都要有共同 artifact、清晰决定权和反馈入口。会议不是协作本身；协作是多种专业能力共同改变同一个结果。

## 1. 用户与业务发现

产品、设计、工程和支持共同理解问题。工程人员应尽量接触原始用户反馈、运行数据和业务约束，而不只接收压缩后的 solution request。

团队共同回答：

- 用户真正要完成什么；
- 当前行为在哪里失败；
- 机会的价值、紧迫性和风险；
- 什么结果值得投入；
- 哪些问题现在不做。

**共同 artifact：** outcome、用户证据、成功信号和 non-goals。

## 2. 共同定义目标

团队承诺的是目标与质量，不是预先列出的每个实现动作。Scrum Guide 中 Product Goal、Sprint Goal 和 Definition of Done 的价值就在于为不同 artifact 提供共同方向和透明的完成标准；这个思想可以独立于 Scrum 使用。[Scrum Guide](https://scrumguides.org/scrum-guide.html)

目标负责人决定优先级和产品取舍；团队共同确认目标在技术与运行上是否可行。AI 可以整理证据和提出候选标准，但不能自行决定产品价值。

## 3. 技术探索与任务契约

在承诺交付前，跨职能成员一起识别：

- 系统、数据、接口和团队依赖；
- 安全、隐私、合规与运行风险；
- 需要先验证的未知项；
- rollout、migration、support 和 retirement 要求；
- 哪些任务可以委托给 Agent，权限到哪里。

探索不是提前完成所有设计，而是把会推翻承诺的未知项尽早暴露。必要时先做 time-boxed spike，并把结论写回任务契约或 decision record。

## 4. 切片、接口与 ownership

把目标拆成可以独立集成和验证的垂直切片，而不是按“前端任务、后端任务、测试任务”制造新的交接队列。

并行工作前明确：

- 每个切片的 accountable owner；
- 输入、输出和接受标准；
- API、schema、事件或 UI contract；
- 哪些文件或事实源只有一个 writer；
- 组合验证由谁负责；
- 冲突和范围扩大如何升级。

Agent 可以并行处理独立检索、测试、迁移分析和边界清楚的模块；尚未解决的核心语义不能靠增加 Agent 数量并行化。

## 5. 并行实现和持续集成

团队成员各自使用 [个人软件开发生命周期](02-individual-workflow.md)，但变化持续回到共享主线。推荐：

- 小批量、短分支、频繁同步；
- 合同测试保护团队边界；
- 自动化检查先于人工审查；
- 共享进度以可运行 increment 表示，不以“完成百分比”表示；
- 新发现问题进入统一 triage，不在个人聊天里消失。

DORA 的研究把小批量、持续集成、测试自动化与松耦合团队视为持续交付的重要能力。[DORA Core Model](https://dora.dev/research/)

## 6. 风险导向审查

审查的目的不是让人重新执行 Agent 已做的所有工作。团队应分配审查注意力：

| 审查层 | 主要内容 | 更适合谁 |
| --- | --- | --- |
| 机械一致性 | 格式、静态规则、重复模式、已知漏洞 | 自动化与 AI first pass |
| 行为正确性 | 接受标准、错误路径、测试 oracle | 熟悉领域的工程师 |
| 系统影响 | 数据、接口、性能、可运行性 | 技术/服务 owner |
| 风险接受 | 产品、安全、合规、不可逆影响 | 明确的人类 authority |

代码审查还承担知识传播和共享 ownership，但并不自动等于有效功能测试。Microsoft 的研究指出，review 成本很高，且需要合适技能与社会环境，因此应精确设计 review，而不是把所有变化交给同样的通用审批。[Microsoft Research: Code Reviews](https://www.microsoft.com/en-us/research/publication/code-reviews-do-not-find-bugs-how-the-current-code-review-best-practice-slows-us-down/)

高风险变化应将 executor、independent validator 和 release authority 分开；低风险变化可以合并责任。

## 7. 渐进发布

团队共同确认：

- Definition of Done 已满足；
- 发布批次、feature flag 或 canary 策略；
- 监控与业务成功信号；
- 停止、回滚和事件响应条件；
- 值班、支持和跨团队通知责任。

发布不应需要临时召集大量团队协调。若一个团队无法独立测试和发布其边界内的大部分变化，组织或系统架构已经在阻碍价值流。[DORA: Loosely coupled teams](https://dora.dev/capabilities/loosely-coupled-teams/)

## 8. 生产学习

产品、工程和运行人员一起比较真实结果与原始目标：

- 用户是否获得预期价值；
- 哪些假设错误；
- 是否产生稳定性、支持或操作成本；
- 是否需要继续、调整、回退或停止；
- 哪些生产知识需要回写到测试与文档。

团队 review 的对象应是结果与价值流，而不只是每个人完成了多少任务。

## 9. 淘汰与系统改进

团队负责删除临时 feature flag、兼容路径、过期任务和重复文档。Retrospective 不只讨论“合作感觉”，还要定位系统瓶颈：

- 等待发生在哪个队列；
- 哪类变更最常返工；
- 哪些信息只存在于某个人；
- 哪种 Agent 错误反复出现；
- 哪项平台或自动化投资能缩短反馈；
- 哪些团队依赖应转为服务、facilitation 或重新划界。

## 团队中的责任

责任是必须覆盖的能力，不一定对应固定岗位：

| 责任 | 核心决定 |
| --- | --- |
| Outcome owner | 为什么做、优先级、什么结果有价值 |
| Domain/technical owner | 系统边界、长期技术与数据取舍 |
| Executor | 实现、局部验证和证据整理 |
| Independent validator | 关键假设是否被独立证明 |
| Service owner | 可运行性、SLO、事件与长期维护 |
| Release authority | 何时发布、停止、回滚或接受残余风险 |

Agent 可以参与每项活动，但不能成为最终 accountable owner。

## 协作健康度

SPACE 框架反对用单一指标描述生产力。团队应组合观察：

- **结果与质量：** 用户目标、可靠性、缺陷逃逸和返工；
- **流动：** lead time、cycle time、work item age 和等待时间；
- **协作：** review 负担、跨团队阻塞、知识集中度；
- **体验：** 反馈循环、认知负荷、心流和 burnout；
- **可持续性：** 技术债、旧机制淘汰和 on-call 负担。

AI 时代的团队合作，不是让每个人生成更多，而是让整个团队从问题到生产学习的循环更短、更清楚、更可靠。
