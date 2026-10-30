# Organization Design: Align Responsibility with Delivery Capability

**English** | [简体中文](../05-organization-structure.md)

When AI shortens implementation, delivery can still stall on cross-department waiting, expert review, and release coordination. Observe those constraints before changing responsibilities and service boundaries. A new organization chart need not be the starting point.

These are design recommendations to validate in your own organization.

## Give domains lasting ownership

A domain needs continuing responsibility for behavior, code, data, operations, and maintenance. Specialization is useful, but the outcome must remain owned across handoffs. Individuals own tasks, agents execute work, and long-lived systems retain accountable people.

For example, an orders team should understand the user consequences of a change, implement and verify routine work, and respond after release without rediscovering who owns the interface, logs, and deployment each time.

## Share capabilities, keep domain decisions close

| Shared capabilities | Domain decisions |
| --- | --- |
| Model access, identity, permissions, audit | User goals, priorities, product behavior |
| Environments, CI, release and monitoring tools | Task scope, acceptance, domain tests |
| Data-use, security, supply-chain policies | Current docs, issue records, compatibility constraints |
| Common evaluation, cost and support tools | Authorized releases, production observation, maintenance |

Shared capabilities should reduce duplication and waiting. If routine use requires tickets or personal connections, improve self-service and service commitments. Domain autonomy still operates within common data and production rules.

## Add capabilities when needed

[Team Topologies](https://teamtopologies.com/key-concepts) offers four useful lenses: domain delivery, internal platforms, temporary enablement, and specialist subsystems. Use them to identify gaps; they do not require four departments.

- Small teams can combine roles and share capability through templates and automation.
- Repeated problems across teams may justify platform ownership.
- Temporary skill gaps can use pairing or coaching with an exit condition.
- Expertise that is difficult to distribute may need a specialist team behind a stable interface.

Clarify whether teams are exploring together, consuming a service, or receiving temporary coaching, and when intensive coordination should end. These interaction categories come from the same framework; boundaries still depend on the system.

## Describe team boundaries on one page

Publish owned systems and outcomes, provided services, support routes, autonomous decisions, interface evolution rules, and incident contacts. Make agent data access and action permissions discoverable too.

Collaborate to establish new boundaries; once stable, aim for services that other teams can use without renegotiating each change.

## Improve recurring blocking points

| Signal | First question |
| --- | --- |
| Every release waits for several teams | Are interfaces tightly coupled or release responsibilities fragmented? |
| Most questions go to one person | Are knowledge, documentation, and decision rights concentrated? |
| Review grows while new tasks keep starting | Does work in progress exceed validation capacity? |
| Teams maintain unrelated infrastructure | Would a shared service or removal of complexity help? |
| AI repeats the same mistakes | Are contracts, local rules, and checks missing or conflicting? |

Managers can address these obstacles by setting priorities, protecting review capacity, and completing feedback and ownership. Evaluate changes through waiting, rework, incidents, and team burden rather than AI usage alone.
