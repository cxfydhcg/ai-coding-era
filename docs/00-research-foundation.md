# 研究基础与证据边界

[English](en/00-research-foundation.md) | **简体中文**

这套方法综合了软件交付、开发者生产力、工作流、团队设计、安全开发和 AI-assisted development 的一手研究。它不是对某一种 Agile 方法的重新包装，也不把单个厂商实验当作普遍规律。

## 研究给出的共同方向

### AI 的效果取决于任务和系统，而不是工具名称

不同研究得到的生产力结果并不一致：

- Microsoft、Accenture 和一家 Fortune 100 企业开展的三项随机现场实验，合计覆盖 4,867 名开发者；合并结果显示，获得 AI coding assistant 的开发者完成任务数提高了 26.08%，新手收益更明显。[Microsoft Research, 2025](https://www.microsoft.com/en-us/research/publication/the-effects-of-generative-ai-on-high-skilled-work-evidence-from-three-field-experiments-with-software-developers/)
- METR 对 16 名熟悉成熟开源项目的资深开发者进行随机对照实验，共涉及 246 个真实任务；使用 2025 年初 AI 工具时，任务完成时间反而增加约 19%。研究者也强调，该结果只代表特定人群、工具和任务环境。[METR study](https://metr.org/Early_2025_AI_Experienced_OS_Devs_Study-paper.pdf)

这两项结果不应被粗暴平均。它们说明：AI 的价值随开发者经验、代码库熟悉度、任务形态、工具能力和验证成本变化。组织必须测量自己的完整交付周期，不能只测生成速度或主观感受。

### AI 是组织系统的放大器

DORA 2025 将 AI 描述为放大器：组织若已有明确用户目标、版本控制、小批量交付、高质量平台和健康数据，AI 更可能转化为整体绩效；如果测试、审查和发布本来就是瓶颈，更快生成只会制造 downstream disorder。[DORA 2025](https://dora.dev/research/2025/dora-report/)

DORA 提出的七项 AI 基础能力是：用户中心、强版本控制、AI 可访问的内部数据、小批量工作、清晰公开的 AI 立场、高质量内部平台和健康数据生态。[DORA AI capabilities](https://dora.dev/ai/)

### 生产力不能用单一活动指标表示

SPACE 框架把开发者生产力分为满意度与福祉、绩效、活动、沟通协作、效率与流动五个维度，并明确反对用单一指标代表生产力。[SPACE framework](https://www.microsoft.com/en-us/research/publication/the-space-of-developer-productivity-theres-more-to-it-than-you-think/)

DevEx 研究把影响开发体验的关键因素归纳为反馈循环、认知负荷和心流状态。这意味着 AI 时代的优化重点不仅是让人输入更少，还包括更快获得可靠反馈、减少无关认知负担，并保护连续思考时间。[DevEx in Action](https://www.microsoft.com/en-us/research/publication/devex-in-action-a-study-of-its-tangible-impacts/)

### 意图澄清和测试反馈比一次生成更可靠

TiCoder 的用户研究通过测试驱动的意图澄清，让参与者更容易正确判断 AI 生成代码，并降低任务认知负荷；其大规模实验也观察到多轮交互对生成正确率的改善。这支持“先建立可执行接受标准，再委托实现”的流程。[Microsoft Research, TiCoder](https://www.microsoft.com/en-us/research/publication/llm-based-test-driven-interactive-code-generation-user-study-and-empirical-evaluation/)

### 安全必须嵌入整个生命周期

NIST SSDF 将安全实践组织为准备组织、保护软件、生产安全软件和响应漏洞四组活动，并建议把它们集成到现有 SDLC，而不是在发布前增加一次孤立审计。[NIST SP 800-218](https://csrc.nist.gov/pubs/sp/800/218/final)

### 团队应围绕价值流和认知负荷设计

Team Topologies 提出四类基本团队：stream-aligned、platform、enabling 和 complicated-subsystem；以及三种团队交互方式：有期限的 collaboration、X-as-a-Service 和 facilitation。重点不是套用名称，而是减少永久交接、控制团队认知负荷并加快价值流。[Team Topologies key concepts](https://teamtopologies.com/key-concepts)

DORA 对 loosely coupled teams 的定义进一步强调：团队应能够在不依赖外部细粒度协调的情况下完成测试、部署和大部分变化。[DORA: Loosely coupled teams](https://dora.dev/capabilities/loosely-coupled-teams/)

### 任务系统应管理流动，而不是制造更多启动

Kanban Guide 要求显式定义 workflow、控制 WIP，并使用 throughput、work item age 和 cycle time 等流动指标；Service Level Expectation 应根据历史周期时间给出概率预测。[The Kanban Guide, 2025](https://kanbanguides.org/the-kanban-guide/)

Scrum Guide 强调 Product Goal、Sprint Goal 和 Definition of Done 带来的共同目标与透明度。本文借用“共同目标”和“共同完成标准”，但不要求团队采用 Scrum。[The Scrum Guide, 2020](https://scrumguides.org/scrum-guide.html)

## 本文由研究推导出的设计判断

以下是综合上述研究后的推导，不是任何单一来源直接提出的标准：

1. Agent session 不是任务；任务是包含结果、边界、证据和责任人的长期工作单元。
2. AI 降低执行成本后，WIP 必须由验证和集成能力约束，而不是由可启动的 Agent 数量决定。
3. 个人流程与团队流程必须分别设计；前者保证一次执行可信，后者保证多角色的端到端价值流不在交接中断裂。
4. 团队架构的基本单元仍应是拥有长期结果的稳定团队，Agent 是团队能力，不是新的责任主体。
5. 中央 AI 团队更适合提供平台、评估和治理能力，不适合作为替所有领域团队写代码的工厂。
6. 生产观察与旧机制淘汰必须进入 Definition of Done 或后续 lifecycle gate，不能永远停在“已合并”。

## 如何阅读后续建议

- “应当”表示多个研究方向一致，或属于安全与责任的基础约束。
- “建议”表示合理的实践推导，需要结合团队环境试验。
- 带具体数值的研究结果只适用于其样本与实验条件，不应直接成为组织 KPI。
- 框架的最终验证方式，是在本组织记录基线、小范围试点并观察完整价值流结果。
