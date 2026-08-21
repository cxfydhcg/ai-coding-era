---
title: AI Coding 时代的软件开发进化
markmap:
  colorFreezeLevel: 2
  initialExpandLevel: 2
  maxWidth: 320
  spacingHorizontal: 100
  spacingVertical: 10
---

# AI Coding 时代的软件开发进化

## [English / 英文](https://cxfydhcg.github.io/ai-coding-era/mindmap.html)

## 从这里开始

### [研究基础](docs/00-research-foundation.md)

- AI 效果取决于任务与系统环境
- AI 会放大优势，也会放大瓶颈
- 衡量完整交付生命周期

### [核心原则](docs/01-core-principles.md)

- 结果优先于代码数量
- 意图先于生成
- 证据优先于信心
- 有边界的自主性
- 删除是一等工程活动

## [一、个人软件开发生命周期](docs/02-individual-workflow.md)

### 选择问题

- 从用户、业务或运行证据开始
- 定义可观察结果

### 先理解，再改变

- 恢复局部上下文
- 区分事实、推断和未知项
- 选择人主导、结对、委托或并行研究模式

### 契约与设计

- Outcome、scope、non-goals
- 约束与接受标准
- 风险、可逆性、rollout、rollback

### 实现与验证

- 小的行为切片
- 静态 → 单元 → 集成 → 端到端
- 高风险行为使用独立 oracle

### 交付与学习

- 自我审查与团队审查
- 渐进发布
- 生产观察
- 更新运行记忆并淘汰临时机制

## [二、团队协作的软件生命周期](docs/03-team-collaboration.md)

### 共同发现

- 产品、设计、工程、支持、运行共同参与
- 一个 outcome 和共同成功信号

### 共同契约

- 技术探索
- 跨职能 Definition of Done
- 明确决策权

### 切片、分配与依赖解耦

- 时长构成变了：实现变短，验证与等待变长
- 分配结果和决定权，不是工时
- 垂直切片，而不是职能交接
- 四种依赖
  - 契约依赖
  - 真实顺序依赖
  - 资源与环境依赖
  - 知识与决策依赖
- 解耦手段
  - 契约先行
  - mock 与假实现
  - expand → migrate → contract
  - feature flag
  - 反向切片
  - 单写者原则
- 阻塞可见并按时限升级
- 未确定的语义无法并行

### 并行交付

- 接口契约与 ownership
- 小批量持续集成

### 风险导向的审查与发布

- 自动化和 AI 检查机械问题
- 人类审查语义与风险
- 重要变化需要独立验证

### 生产学习

- 用真实结果对照原始目标
- 证据回流到任务、测试和文档
- 淘汰 flag、兼容路径和过期上下文

## [三、任务管理](docs/04-task-management.md)

### 四个层次不要混淆

- Outcome
  - 用户或业务结果
- Initiative
  - 围绕结果协调的一组变化
- Task contract
  - 持久、有人负责、可以验证的工作单元
- Execution attempt
  - 一次人或 Agent 的执行会话

### 按工作形态路由

- Fix now
- Backlog
- Requirement 或 initiative
- Discovery 或 spike
- Reject 或 retire

### 管理显式工作流

- Discovery → Triage → Ready
- In Progress → Verify
- Ready to Release → Observe → Done

### 保护瓶颈

- WIP 由验证能力决定
- 管理任务老化与阻塞队列
- 使用历史 cycle time 和概率式 SLE

### 完成深度

- D0 存在：点了有反应
- D1 主路径正确
- D2 边界与失败路径
- D3 在真实系统中可运行
- D4 结果被验证并删除旧路径
- 任务契约声明目标深度
- 深度由风险与可逆性决定
- 典型浅完成模式
  - 只覆盖被提到的输入
  - 测试与实现同源
  - 只在演示数据上正确
  - 运行面缺失
  - 只做加法不做减法
- Done 是有证据的断言，不是状态点击

### 权限与风险匹配

- 低风险：Agent 执行，作者确认
- 中风险：同行审查与自动验证
- 高风险：计划先批准、独立验证
- 极高风险：最小权限与双人授权

## [四、团队架构](docs/05-organization-structure.md)

### 稳定 ownership 单位

- 个人 owner 一个任务
- 稳定团队 owner 一个长期系统
- Agent 是能力，不是责任主体

### 四类团队能力

- 领域产品团队
  - 负责 design、build、run、improve
- 平台团队
  - 安全的自助交付与 Agent 基础设施
- 赋能团队
  - 有期限的能力传播
- 专业子系统团队
  - 在稳定边界后提供专家能力

### 三种团队交互模式

- Collaboration
  - 临时共同探索
- X-as-a-Service
  - 稳定自助服务关系
- Facilitation
  - 帮助另一个团队获得独立能力

### 有选择地集中

- 集中：模型网关、身份、政策、审计、公共平台
- 本地：用户结果、领域规则、任务 scope、发布责任

### 治理是护栏

- 清晰的 AI stance
- 最小权限与显式授权
- Provenance、许可、安全与事件标准
- 不需要判断的政策尽量自动化

## 共享系统

### [Repository 作为运行记忆](docs/06-repository-as-operational-memory.md)

- 当前：代码与 current-state docs
- 已批准的未来：任务契约与 requirement
- 延后的未来：backlog
- 仍有价值的过去：decision record
- 运行现实：生产证据
- 每个生命周期状态只有一个有效事实源

### 可直接使用的模板

- [任务契约](templates/task-contract.md)
- [完成深度检查表](templates/completion-depth-checklist.md)
- [依赖与切片地图](templates/dependency-map.md)
- [Backlog 条目](templates/backlog-item.md)
- [决策记录](templates/decision-record.md)

### [采用路线图](docs/07-adoption-roadmap.md)

- 一、安全边界
- 二、Repository 上下文
- 三、任务契约
- 四、自动验证与政策
- 五、生产证据与淘汰

## 一句话模型

### 人类拥有意图、重要判断和生产权限

### Agent 在明确边界内检索、建议、实现和验证

### 自动化提供快速、可重复的证据

### 生产现实关闭反馈循环
