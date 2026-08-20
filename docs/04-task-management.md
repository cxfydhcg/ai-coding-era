# AI Coding 时代的任务管理

[English](en/04-task-management.md) | **简体中文**

传统任务系统常被当作“给人分配工作的清单”。AI 让执行并发几乎可以瞬间增加，这种系统会迅速失效：启动的任务更多，审查、集成和发布队列更长，真实目标反而更难看见。

AI 时代的任务管理应管理四件事：**选择、流动、权限和证据**。

## 不要把四种对象混成一层

```text
Outcome：希望改变的用户或业务结果
  └─ Initiative：为结果组织的一组协调性变化
      └─ Task contract：可独立负责和验证的工作单元
          └─ Execution attempt：一次人或 Agent 的执行会话
```

- Outcome 可能持续数月，并由指标验证；
- Initiative 协调多个任务、团队或 rollout 阶段；
- Task 是任务系统中的基本责任单位；
- Agent session 只是一次尝试，可以失败、重启或更换模型。

把每次 Agent 对话都建成任务会制造噪声；把一个大型 outcome 直接交给 Agent 又会失去边界。稳定 ID 应属于 task 或 initiative，而不是临时 session。

## 工作项必须是结果契约

一个 Ready 的任务至少包含：

| 字段 | 作用 |
| --- | --- |
| Outcome | 说明要改变什么，而不是要生成什么 |
| Evidence | 证明问题真实，避免 Agent 在假设上构建 |
| Scope / non-goals | 控制扩张与审查成本 |
| Constraints | 保存产品、数据、安全、兼容和运行边界 |
| Acceptance criteria | 把意图转化为可判断行为 |
| Verification plan | 提前决定证据来源和独立程度 |
| Owner / authority | 区分执行权、决策权和发布权 |
| Rollout / retirement | 连接生产观察和临时机制删除 |

可直接使用 [任务契约模板](../templates/task-contract.md)。

## 按工作形态路由

问题发现后先决定需要哪种治理，不要只按估算大小分类：

| 工作形态 | 路由 |
| --- | --- |
| 当前任务内可安全完成并验证 | Fix now |
| 问题真实且可独立执行，但当前不应扩大范围 | Backlog |
| 需要共享范围、阶段、跨团队协调、rollout 或 release gate | Requirement / Initiative |
| 证据不足，需要限时学习 | Discovery / Spike |
| 已不成立、被替代或无价值 | Reject / Retire |

AI 可以自动发现、去重、补充证据并建议路由；它不能因为发现问题就自动改变当前任务范围。

## 从“待办列表”变成显式 workflow

一个适合软件交付的基本流可以是：

```text
Discovery
→ Triage
→ Ready
→ In Progress
→ Verify / Review
→ Ready to Release
→ Observe
→ Done
```

每个状态必须定义进入、退出和 WIP 策略。

| 状态 | 关键问题 | 退出证据 |
| --- | --- | --- |
| Discovery | 问题真实且值得继续吗？ | 原始证据与 outcome |
| Triage | 现在做、延后还是拒绝？ | 优先级、owner、路由 |
| Ready | 是否足够清楚且可执行？ | 任务契约与依赖 |
| In Progress | 是否在边界内产生小增量？ | 可审查 change set |
| Verify / Review | 是否满足行为与风险要求？ | 验证记录与批准 |
| Ready to Release | 是否可安全进入目标环境？ | rollout、监控、回滚 |
| Observe | 真实结果是否支持假设？ | 生产与用户证据 |
| Done | 是否完成学习和清理？ | 文档、后续项、淘汰 gate |

不是所有任务都必须经历单独的 Observe 列。低风险任务可以合并状态，但责任不能因为看板简化而消失。

## WIP 由最稀缺的验证能力决定

Agent 可以同时启动许多实现，但人工领域审查、集成环境和安全验证仍然有限。团队应从瓶颈倒推 WIP：

- Verify 队列满时，停止启动新实现；
- 优先帮助旧工作跨过阻塞，而不是领取新任务；
- 为高风险任务保留专门 review 容量；
- 将不同 Agent 的尝试视为同一任务的内部并行，不分别增加业务 WIP；
- 超过 WIP 必须是显式例外，并说明恢复方法。

The Kanban Guide 要求显式控制 started 到 finished 之间的工作项数量，并观察 WIP、throughput、work item age 和 cycle time。[Kanban Guide](https://kanbanguides.org/the-kanban-guide/)

## 管理队列老化，而不是只催截止日期

对每个已开始任务显示 age，并使用历史 cycle time 建立概率式 Service Level Expectation，例如“85% 的标准任务在 8 天内完成”。任务接近或超过 SLE 时，讨论的不是“谁不够努力”，而是：

- 是否被依赖、等待或决策阻塞；
- 是否范围不断增长；
- 是否缺少验证环境；
- 是否应该拆分、降级、取消或升级处理；
- Agent 是否持续生成但没有收敛。

相较单点工时承诺，历史流动数据更适合预测不确定的软件工作。

## 优先级必须连接结果与成本

建议同时考虑：

- 用户/业务价值；
- 时间敏感性；
- 风险降低或机会开启；
- 延迟成本；
- 验证与协调成本；
- 可逆性和认知负荷；
- 是否减少未来 WIP 或依赖。

“AI 很快能做完”不是优先级理由。实现便宜但验证昂贵的任务，可能占用更多系统容量。

## 风险决定 Agent 权限

| 风险级别 | 示例 | Agent 权限与门禁 |
| --- | --- | --- |
| 低 | 文案、机械重构、局部测试 | 可连续实现和自验证，作者确认 |
| 中 | 常规业务逻辑、内部接口 | 可实现，必须同行 review 和自动验证 |
| 高 | 权限、支付、公共 API、迁移 | 计划与关键取舍先批准，独立验证，渐进发布 |
| 极高 | 不可逆数据、生产安全边界 | 最小权限、双人授权、演练和明确 release authority |

权限是任务属性，不应只由“使用哪个模型”决定。同一 Agent 在测试代码和生产删除任务中应有不同能力边界。

## 新发现问题的处置

```text
真实问题？
  ├─ 否：记录为什么不成立，不进入 backlog
  └─ 是
      ├─ 当前 scope 内且可验证：fix now
      ├─ 可独立保存但暂不承诺：backlog
      ├─ 需要协调或批准：requirement / initiative
      └─ 证据不足：time-boxed discovery
```

Backlog 条目必须能脱离原对话执行，模板见 [Backlog Item](../templates/backlog-item.md)。定期删除重复、失效或永远不会执行的条目；backlog 不是组织焦虑的永久存储。

## Definition of Ready 与 Definition of Done

### Ready

- outcome、owner 和优先级明确；
- 关键证据可访问；
- 范围、non-goals 与 Agent 权限明确；
- 接受标准可以验证；
- 依赖与主要未知项已识别；
- 任务大小适合当前反馈周期。

### Done

- 接受标准有与风险相称的证据；
- scope deviation 已解释并获得授权；
- 代码、测试、当前文档和运行配置一致；
- release、rollback 与必要观察已完成；
- 范围外发现已明确处置；
- 临时机制已删除或存在 owner 和 removal gate。

如果多个团队共同交付一个产品，应共享最低 Definition of Done；否则一个团队的“完成”会成为另一个团队的隐性队列。[Scrum Guide](https://scrumguides.org/scrum-guide.html)

## 任务系统应测量什么

- Outcome 达成率，而非只看关闭数量；
- 从 Ready 到生产证据的 lead time；
- 各状态等待时间和 work item age；
- throughput、cycle time 与 WIP；
- review 返工、scope expansion 和 reopen 比例；
- 生成时间与验证时间的比例；
- 发布失败、回滚与生产缺陷；
- 达到 removal gate 后仍存活的旧机制。

不要用 story points、代码行数、Agent 调用数或关闭任务数衡量个人绩效。SPACE 研究指出，开发者生产力必须跨多个维度理解，单一活动指标会造成错误激励。[SPACE](https://www.microsoft.com/en-us/research/publication/the-space-of-developer-productivity-theres-more-to-it-than-you-think/)

AI 时代的好任务系统不是让所有东西更快开始，而是让最有价值的工作更可靠地完成。
