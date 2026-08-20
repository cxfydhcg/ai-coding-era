# Team Architecture in the AI Coding Era

**English** | [简体中文](../05-organization-structure.md)

The collaborative lifecycle describes how one value stream completes work. Team architecture describes how a company continuously allocates ownership, cognitive load, platform capability, and inter-team relationships across many value streams.

AI makes code production elastic. It does not make domain knowledge, review attention, production accountability, or coordination infinite. Organizations should therefore optimize for **fast flow with clear ownership**, not for the fastest code producer.

## Move from functional relay races to value-stream ownership

The traditional structure looks like this:

```text
Product → Design → Frontend → Backend → QA → Security → Operations
```

Each department may be locally efficient while work waits at every handoff. Accelerating one stage with AI can simply lengthen the downstream queue.

A better target is:

```text
Domain team owning an end-to-end outcome
    ├─ self-serves through an internal platform
    ├─ receives temporary help from enabling teams
    ├─ consumes specialist subsystem capabilities
    └─ decides autonomously inside company guardrails
```

Technical and organizational architecture shape one another. [DORA's loosely coupled teams](https://dora.dev/capabilities/loosely-coupled-teams/) capability describes teams that can test, deploy, and complete most changes without fine-grained external coordination.

## The stable team is the smallest unit of long-term ownership

Individuals and agents leave, switch tasks, and lose context. A long-lived system should not depend on one expert or one exceptional prompt.

A stable team owns:

- a defined business domain or value stream;
- its software, data, operations, and service quality;
- technical decisions, documentation, and backlog;
- release, incident response, and legacy retirement;
- interfaces and service commitments to other teams.

An individual may own a task. A team owns a long-lived system. An agent is a capability available to the team, not an ownership entity.

## Four kinds of team capability

The four Team Topologies types are useful patterns, not names that every organization must adopt immediately. [Official concepts](https://teamtopologies.com/key-concepts)

### 1. Stream-aligned or domain product team

A stable, cross-functional team aligned to a customer journey, product capability, or business domain. It designs, builds, runs, and improves its service while seeing direct user and production feedback.

In the AI era:

- every domain team can use and evaluate agents;
- task contracts and local rules stay close to the domain;
- AI-generated changes receive the same quality accountability as human-authored changes;
- new execution capacity first shortens feedback and removes complexity rather than expanding the roadmap indefinitely.

### 2. Platform team

The platform gives domain teams a secure, self-service paved road:

- repository and development-environment templates;
- CI/CD, test environments, and release capabilities;
- agent runtimes, model gateways, identity, permissions, and audit;
- secrets, dependencies, supply-chain and security scanning;
- observability, evaluation, cost, and usage data;
- organizational knowledge entry points and context retrieval.

The platform is an internal product with user research, clear boundaries, reliability goals, documentation, support, and adoption measures. DORA 2025 argues that a quality internal platform can absorb downstream disorder created when AI accelerates generation ahead of testing, security, and deployment. [DORA: Platform engineering](https://dora.dev/capabilities/platform-engineering/)

### 3. Enabling team

An enabling team helps domain teams cross a temporary capability gap—security modeling, AI workflow design, test strategy, data migration, or reliability engineering. It spreads skill through pairing, workshops, and working examples rather than taking over domain delivery permanently.

Every enablement engagement needs a goal, time boundary, and exit condition. Success means the receiving team can operate independently afterward.

### 4. Complicated-subsystem team

Some areas—advanced algorithms, hardware, compilers, cryptography, payment networks, or ML infrastructure—need concentrated specialist knowledge. A specialist team exposes a stable boundary so every domain team does not absorb unreasonable cognitive load.

It is not a generic approval department. It needs a clear API, service quality, support model, and evolution path.

## What to centralize and what to keep local

| Central capability | Domain-team responsibility |
| --- | --- |
| Model procurement, gateway, cost, vendor management | User outcomes and product behavior |
| Identity, least privilege, sandboxing, audit | Task scope and domain risk judgment |
| Shared agent runtime, evaluation, observability | Local instructions, test oracles, acceptance |
| Company data and security policy | Domain documentation, backlog, decisions |
| Common CI/CD and paved roads | Release decisions, production outcomes, legacy ownership |

This avoids both extremes: every team rebuilding unsafe infrastructure, or a central AI team becoming a code factory without domain context.

## Use three explicit interaction modes

Team Topologies defines three modes that expose ambiguous dependencies:

| Mode | When to use it | Exit |
| --- | --- | --- |
| Collaboration | Two teams jointly discover a boundary or solve an unknown | Time-bounded; ends with an interface or new ownership |
| X-as-a-Service | One team offers a stable self-service capability | Sustained through Team API, SLO, docs, and support |
| Facilitation | One team helps another gain a capability | Ends when the learning goal is achieved |

“Keep coordinating forever” is not a fourth mode. It usually signals an unclear interface or ownership boundary.

## Give every team a Team API

A Team API is more than a technical endpoint. It states:

- the team's mission and value stream;
- system, data, and decision boundaries;
- services, APIs, documentation, and SLOs;
- how to request collaboration, support, and escalation;
- the current interaction mode and expected exit;
- data agents may access and actions they may perform;
- change, incident, and deprecation communication.

This allows people and agents to decide whether to act locally, consume a platform service, request facilitation, or begin cross-team collaboration.

## Governance is a guardrail, not a ticket queue

Company-wide governance should define a small set of non-negotiable boundaries:

- which code, data, and customer information may enter which models;
- which permissions, production actions, and irreversible operations require human or two-person approval;
- provenance, audit, licensing, and supply-chain requirements;
- how models and tools are evaluated, introduced, degraded, and retired;
- release and incident standards for high-risk systems;
- escalation and response paths for boundary violations.

DORA includes a clear and communicated AI stance as a foundational capability. Ambiguity makes cautious teams stop experimenting while aggressive teams cross boundaries accidentally. [DORA AI capabilities](https://dora.dev/ai/)

Implement deterministic policy through platform defaults and automation where possible. Keep product judgment and risk acceptance with explicit human authorities rather than a central approval queue for normal delivery.

## Cognitive load determines team boundaries

Reconsider the design when:

- teams spend large amounts of time on infrastructure unrelated to their core domain;
- every release needs synchronized coordination with many teams;
- one team owns too many unrelated systems and on-call surfaces;
- critical knowledge is concentrated in one person;
- a “self-service” platform still requires tickets and relationships;
- agents repeatedly fail because repository context conflicts.

The solution may be a better platform, temporary facilitation, a specialist subsystem, a new domain boundary, or deletion of system complexity—not necessarily more headcount.

## Patterns by organization size

### 1–5 people

Do not create a separate platform team. Name outcome, technical, validation, and release responsibilities. Encode shared capability in repository templates and automation. Seek cross-review for high-risk changes.

### 6–30 people

Form a small number of domain teams with a shared platform owner and security/AI champions. Avoid permanent frontend, backend, and QA handoff departments. Use communities of practice to spread learning.

### 30–150 people

Create a real platform product team, temporary enabling capability, and explicit Team APIs. Evolve domain boundaries around value flow and measure cross-team waiting and cognitive load.

### Larger organizations

Multiple platform and governance layers may be necessary, but every layer must reduce domain-team burden. Unify identity, policy, and observability while keeping domain knowledge and product decisions local. Organization design must evolve continuously; a reorganization is never a permanent answer.

## The new focus of leaders and managers

- select and protect clear value-stream boundaries;
- improve user goals and priority decisions;
- find the real bottleneck from generation to production;
- manage team cognitive load, WIP, and long-term ownership;
- invest in platforms, testing, documentation, and production feedback;
- define a clear AI stance and risk escalation path;
- create space for learning and deleting complexity;
- measure multidimensional outcomes, not individual code volume, story points, or AI usage.

AI-era team architecture is not about using fewer people to preserve the old relay race. It is a sociotechnical system in which stable teams own outcomes, platforms lower cognitive load, governance defines boundaries, and agents expand execution capacity.
