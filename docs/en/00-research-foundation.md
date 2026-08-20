# Research Foundation and Evidence Boundaries

**English** | [简体中文](../00-research-foundation.md)

This guide synthesizes primary research on software delivery, developer productivity, workflow, team design, secure development, and AI-assisted software engineering. It is not a rebranding of one Agile framework, and it does not treat a single vendor study as a universal law.

## Shared directions in the research

### AI outcomes depend on the task and delivery system

Productivity studies do not produce one universal result:

- Three randomized field experiments at Microsoft, Accenture, and a Fortune 100 company covered 4,867 developers. Combined results reported a 26.08% increase in completed tasks for developers with an AI coding assistant, with larger gains among less-experienced developers. [Microsoft Research, 2025](https://www.microsoft.com/en-us/research/publication/the-effects-of-generative-ai-on-high-skilled-work-evidence-from-three-field-experiments-with-software-developers/)
- METR ran a randomized controlled trial with 16 experienced developers completing 246 real tasks in mature open-source repositories they knew well. With early-2025 AI tools, completion time increased by roughly 19%. The authors explicitly limit the finding to that population, tool generation, and task setting. [METR study](https://metr.org/Early_2025_AI_Experienced_OS_Devs_Study-paper.pdf)

These results should not be averaged into a generic productivity number. They show that value varies with experience, repository familiarity, task shape, tool capability, and verification cost. Organizations need to measure their own end-to-end delivery system rather than generation speed or perceived speed alone.

### AI amplifies the existing organizational system

DORA 2025 characterizes AI as an amplifier. Organizations with clear user goals, strong version control, small batches, quality platforms, and healthy data systems are more likely to turn AI use into organizational performance. Where testing, review, and release are already bottlenecks, faster generation can create downstream disorder. [DORA 2025](https://dora.dev/research/2025/dora-report/)

DORA's seven AI capabilities are user-centric focus, strong version control, AI-accessible internal data, working in small batches, a clear and communicated AI stance, a quality internal platform, and healthy data ecosystems. [DORA AI capabilities](https://dora.dev/ai/)

### Developer productivity is multidimensional

The SPACE framework describes five dimensions: satisfaction and well-being, performance, activity, communication and collaboration, and efficiency and flow. It explicitly rejects using one metric as a complete representation of developer productivity. [SPACE framework](https://www.microsoft.com/en-us/research/publication/the-space-of-developer-productivity-theres-more-to-it-than-you-think/)

DevEx research organizes critical experience factors around feedback loops, cognitive load, and flow state. AI-era improvement is therefore not just about reducing typing. It should shorten trustworthy feedback, remove irrelevant cognitive burden, and protect focused work. [DevEx in Action](https://www.microsoft.com/en-us/research/publication/devex-in-action-a-study-of-its-tangible-impacts/)

### Intent clarification and test feedback outperform one-shot generation

In the TiCoder study, test-driven intent clarification helped participants evaluate AI-generated code more correctly and reduced task-induced cognitive load. Its scaled experiments also found that iterative feedback improved generation accuracy. This supports establishing executable acceptance criteria before delegating implementation. [Microsoft Research: TiCoder](https://www.microsoft.com/en-us/research/publication/llm-based-test-driven-interactive-code-generation-user-study-and-empirical-evaluation/)

### Security belongs throughout the lifecycle

NIST's SSDF organizes practices around preparing the organization, protecting software, producing well-secured software, and responding to vulnerabilities. It recommends integrating them into the chosen SDLC rather than adding one isolated audit before release. [NIST SP 800-218](https://csrc.nist.gov/pubs/sp/800/218/final)

### Teams should be designed around value flow and cognitive load

Team Topologies defines four fundamental team types—stream-aligned, platform, enabling, and complicated-subsystem—and three interaction modes: time-bounded collaboration, X-as-a-Service, and facilitation. The goal is not adopting labels; it is reducing permanent handoffs, controlling team cognitive load, and improving flow. [Team Topologies key concepts](https://teamtopologies.com/key-concepts)

DORA's loosely coupled teams capability further emphasizes that teams should complete testing, deployment, and most changes without fine-grained external coordination. [DORA: Loosely coupled teams](https://dora.dev/capabilities/loosely-coupled-teams/)

### Task systems should manage flow, not maximize starts

The Kanban Guide requires an explicit workflow, WIP control, and flow measures such as throughput, work item age, and cycle time. A Service Level Expectation should use historical cycle time to express a probabilistic forecast. [The Kanban Guide, 2025](https://kanbanguides.org/the-kanban-guide/)

The Scrum Guide's Product Goal, Sprint Goal, and Definition of Done create shared direction and transparency. This guide borrows the ideas of a shared goal and a shared completion standard without requiring Scrum. [The Scrum Guide, 2020](https://scrumguides.org/scrum-guide.html)

## Design judgments derived from the research

The following are syntheses, not standards stated by any one source:

1. An agent session is not a task. A task is a durable unit containing an outcome, boundaries, evidence, and accountability.
2. Once AI lowers execution cost, WIP must be constrained by verification and integration capacity—not by the number of agents that can be started.
3. Individual and team lifecycles need separate designs. One makes an execution trustworthy; the other keeps the end-to-end value stream from breaking at handoffs.
4. The stable team remains the smallest unit of long-term ownership. An agent is a capability, not an accountable entity.
5. A central AI team is better suited to platforms, evaluation, enablement, and governance than acting as a code factory for every domain.
6. Production observation and legacy retirement belong in the Definition of Done or in explicit lifecycle gates after release.

## How to interpret the recommendations

- “Should” indicates convergence across research or a baseline safety and accountability constraint.
- “Recommended” indicates a reasoned practice that needs local experimentation.
- Numeric findings remain bounded by their samples and experimental conditions; they should not become organizational KPIs directly.
- The final validation method is to record a local baseline, run a bounded pilot, and measure the complete value stream.
