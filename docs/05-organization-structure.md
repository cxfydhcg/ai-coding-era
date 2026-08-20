# AI Coding 时代的团队架构

[English](en/05-organization-structure.md) | **简体中文**

团队协作描述一次价值流如何完成；团队架构描述公司如何长期划分 ownership、认知负荷、平台能力与团队关系，使许多价值流可以持续运行。

AI 让代码生产能力变得弹性，但没有让领域知识、审查注意力、生产责任和跨团队协调变得无限。因此，组织不应围绕“谁写代码最快”设计，而应围绕 **fast flow with clear ownership** 设计。

## 从职能接力转向价值流 ownership

传统结构常见：

```text
产品 → 设计 → 前端 → 后端 → QA → 安全 → 运维
```

每个部门局部效率可能很高，但工作在交接和等待中变慢。AI 加速任何一个环节，都可能只让下游队列更长。

推荐结构：

```text
拥有端到端结果的领域团队
    ├─ 使用内部平台自助交付
    ├─ 在需要时获得 enabling team 帮助
    ├─ 消费专业 subsystem 能力
    └─ 在公司治理边界内自主决策
```

技术架构和组织架构互相塑造。DORA 将 loosely coupled architecture/team 描述为团队能够独立测试、部署和完成大部分变化，而不依赖外部细粒度协调。[DORA: Loosely coupled teams](https://dora.dev/capabilities/loosely-coupled-teams/)

## 最小长期 ownership 单位是团队

个人和 Agent 都可能离开、切换任务或失去上下文。长期系统不应依赖“某位专家”或“某个特别好的 prompt”。

稳定团队应共同拥有：

- 一个明确的业务领域或价值流；
- 相应的软件、数据、运行与服务质量；
- 技术决策、文档和 backlog；
- 发布、事件响应和 legacy retirement；
- 与其他团队的接口与服务承诺。

个人可以 owner 一个任务，团队 owner 一个长期系统。Agent 是团队可调用的执行能力，不是 ownership 主体。

## 四类团队能力

可以借用 Team Topologies 的四种基本类型，但按组织实际演化，而不是一次性改名。[官方概念](https://teamtopologies.com/key-concepts)

### 1. Stream-aligned / 领域产品团队

围绕客户旅程、产品能力或业务领域，长期负责 design、build、run 和 improve。它应该拥有完成大多数变化所需的跨职能能力，并能直接看到用户与生产反馈。

AI 时代的变化：

- 每个团队都具备使用和评估 Agent 的能力；
- 任务契约与局部规则靠近领域；
- 团队对 AI 生成结果承担与人写代码相同的质量责任；
- 新增执行容量首先用于缩短反馈和清理复杂度，而非无限扩张 roadmap。

### 2. Platform team / 内部平台团队

为领域团队提供安全、自助、可组合的 paved road，例如：

- repository 与开发环境模板；
- CI/CD、测试环境和发布能力；
- Agent runtime、模型网关、身份、权限和审计；
- secret、依赖、供应链和安全扫描；
- 可观测性、评估、成本与使用数据；
- 组织级知识入口和上下文检索。

平台必须作为产品运营：有内部用户研究、清晰服务边界、可靠性目标、文档、支持和采用指标。DORA 2025 指出，高质量内部平台能缓解 AI 加速生成后出现的测试、安全和部署 downstream disorder。[DORA: Platform engineering](https://dora.dev/capabilities/platform-engineering/)

### 3. Enabling team / 赋能团队

帮助领域团队短期跨越能力缺口，例如安全建模、AI workflow 设计、测试策略、数据迁移或 SRE。它通过 pairing、workshop 和示范传播能力，不长期接管领域交付。

赋能关系必须有目标、时间边界和退出条件；成功标准是接受帮助的团队以后能够自主完成。

### 4. Complicated-subsystem / 专业子系统团队

当算法、硬件、编译器、密码学、支付网络或 ML infrastructure 等领域需要高度专业能力时，由专门团队提供稳定边界，避免每个领域团队重复承担不合理认知负荷。

该团队不是通用审批部门，而应提供清晰 API、服务质量和演进路径。

## AI 能力应该集中什么、分散什么

| 集中建设 | 领域团队保留 |
| --- | --- |
| 模型采购、网关、成本与供应商管理 | 用户目标和产品行为 |
| 身份、最小权限、sandbox 与审计 | 任务 scope 和领域风险判断 |
| 通用 Agent runtime、评估框架和观测 | 局部 instructions、测试 oracle 和验收 |
| 公司级数据与安全政策 | 领域文档、backlog 和 decision records |
| 共用 CI/CD、开发环境与 paved road | 发布决定、生产结果与 legacy ownership |

这避免两个极端：每个团队重复建设不安全基础设施，或中央 AI 团队成为脱离领域上下文的代码工厂。

## 团队之间只有三种明确交互

Team Topologies 提出的三种 interaction mode 很适合减少模糊依赖：

| 模式 | 使用时机 | 退出方式 |
| --- | --- | --- |
| Collaboration | 两团队为发现新边界或解决未知问题密集合作 | 有期限，形成接口或新的 ownership 后结束 |
| X-as-a-Service | 一方提供稳定、自助的能力 | 通过 Team API、SLO、文档和支持持续服务 |
| Facilitation | 一方帮助另一方获得能力 | 达到学习目标后退出 |

“长期一起协调一下”不是第四种模式，而是 ownership 或接口没有设计清楚的信号。

## 为每个团队建立 Team API

Team API 不是只有技术 endpoint，而是一份团队间契约：

- 团队使命和拥有的价值流；
- 系统、数据和决策边界；
- 提供的服务、API、文档和 SLO；
- 如何请求协作、支持和升级；
- 当前 interaction mode 与预期结束条件；
- Agent 可以访问的数据和可执行动作；
- 重大变更、事件与弃用如何通知。

这让人和 Agent 都能判断“应该自己做、调用平台、请求 facilitation，还是需要跨团队 collaboration”。

## 公司级治理是护栏，不是任务审批流水线

公司应明确少量不可协商的边界：

- 哪类代码、数据和客户信息可以进入哪些模型；
- 哪些权限、生产动作和不可逆操作需要人工或双人授权；
- provenance、审计、第三方许可和供应链要求；
- 模型和工具如何评估、上线、降级与退出；
- 高风险系统的测试、发布与事件标准；
- 违反边界时的升级和响应路径。

DORA 的 AI capabilities model 将 clear and communicated AI stance 列为基础能力。模糊政策会让谨慎者停止尝试，也会让激进者无意越界。[DORA AI capabilities](https://dora.dev/ai/)

治理规则应尽可能由平台默认配置和自动检查执行。需要产品或风险判断的部分保留明确的人类 authority，避免建立一个审批所有正常变更的中央队列。

## 认知负荷决定团队边界

团队需要理解的领域、技术和运行责任不能无限增加。出现以下信号时应重新设计：

- 大量时间用于理解与核心领域无关的基础设施；
- 每次发布都需要多个外部团队同步；
- 一个团队拥有太多无关系统和 on-call 面；
- 关键知识集中在单个人；
- 平台“自助”仍需要工单和内部关系；
- Agent 反复因上下文冲突做出同类错误。

解决方法可能是改善平台、引入 facilitation、提取专业 subsystem、重新划分领域边界或删除系统复杂度，不一定是增加人手。

## 不同规模的组织

### 1–5 人

不需要建立独立平台团队。明确 outcome、technical、validation 和 release 责任；把通用能力做成 repository 模板和自动化；高风险变更找外部或交叉审查。

### 6–30 人

形成少数领域团队，共享轻量平台 owner 和安全/AI champion。避免按前端、后端、QA 建永久交接部门。使用 community of practice 传播方法。

### 30–150 人

建立真正的平台产品团队、临时 enabling 能力和清晰 Team API。围绕价值流调整领域边界，追踪跨团队等待和认知负荷。

### 更大组织

可以形成多层平台和治理，但每层都应减少领域团队负担。用统一身份、政策和可观测性连接组织，同时让领域知识和产品决定保持本地化。组织设计必须持续演化，不能把某次重组当作永久答案。

## 领导者与管理者的新职责

- 选择和保护清晰的价值流边界；
- 提高用户目标和优先级质量；
- 识别从生成到生产之间的真实瓶颈；
- 管理团队认知负荷、WIP 和长期 ownership；
- 投资平台、测试、文档和生产反馈；
- 建立清晰 AI stance 与风险升级路径；
- 让团队有空间学习和删除复杂度；
- 用多维结果衡量系统，而不是用代码量、story points 或 AI 使用率评价个人。

AI 时代的团队架构，不是用更少的人维持原来的流水线，而是重新设计一个让稳定团队拥有结果、平台降低认知负荷、治理提供边界、Agent 扩展执行能力的社会技术系统。
