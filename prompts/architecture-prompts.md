---
document_type: prompt_library
scope: reusable
audience:
  - engineering_managers
  - solution_architects
  - principal_engineers
  - technical_leads
  - developers
  - ai_agents
status: draft
review_cycle: monthly
tags:
  - architecture
  - hld
  - adr
related_documents:
  - ../agents/architecture-governance-agent.md
  - ../templates/hld-template.md
  - ../templates/lld-template.md
  - ../templates/adr-template.md
---

# Architecture Prompts

Each prompt should be run with project context, existing ADRs, and relevant Dumbledore documents.

## Decision Independence Prompt Clause

Use this clause in any prompt that asks for an HLD, ADR, technology choice, architecture style, repository strategy, infrastructure strategy, or stack recommendation:

```text
Do not simply follow my preferred choices. Challenge my assumptions. Compare alternatives. Recommend based on rationale, not preference. Treat user preference as input, not decision.
```

Major recommendations must use the Recommendation Format from `agents/architecture-governance-agent.md`: User Preference, Dumbledore Assessment, Alternatives Considered, Trade-off Table, Decision, Why This Decision, What Would Change This Decision Later, Risks, and ADR Required: Yes/No.


## System Context

When to use: before HLD creation.

Expected output: system boundary, actors, integrations, data flows.

Review focus: missing actors, hidden dependencies, unclear ownership.

```text
Create a system context for [project].

Use the Architecture Governance Agent behavior. Include:
- system purpose
- actors
- external systems
- high-level data flows
- trust boundaries
- assumptions
- open questions
```

## MVP HLD

When to use: before implementation starts.

Expected output: MVP HLD using the project repo's HLD location.

Review focus: simplicity, boundaries, operability, security.

```text
Create an MVP HLD for [project] using Dumbledore HLD standards.

Context:
[paste product scope, constraints, system context]

Prefer simple, evolvable architecture. Explain trade-offs. Avoid premature microservices. Do not simply follow my preferred choices. Challenge my assumptions. Compare alternatives. Recommend based on rationale, not preference.
```

## Scale-Stage HLD

When to use: when growth path needs to be understood without overbuilding MVP.

Expected output: scale-stage architecture roadmap.

Review focus: scaling triggers, data growth, operational maturity.

```text
Create a scale-stage HLD for [project] that evolves from the MVP design.

Do not replace the MVP with scale architecture. Produce scaling triggers, options, risks, and ADRs required later.
```

## LLD

When to use: before implementing a module or feature.

Expected output: LLD with modules, APIs, data model, errors, tests.

Review focus: implementation boundaries and failure handling.

```text
Create an LLD for [feature/module] in [project].

Use the current HLD and ADRs. Include:
- module boundaries
- APIs
- data model changes
- business rules
- error handling
- observability
- test strategy
- rollout risks
```

## ADR Generation

When to use: for material architecture decisions.

Expected output: one ADR per decision.

Review focus: options, rationale, consequences, review triggers.

```text
Draft an ADR for this decision: [decision].

Context:
[paste context and options]

Use one decision per ADR. Do not simply follow my preferred choices. Challenge my assumptions. Compare alternatives. Recommend based on rationale, not preference. Include options, rationale, rejected options, consequences, operational impact, security impact, cost impact, and review triggers.
```

## Bounded Context Analysis

When to use: before module or service boundaries are set.

Expected output: context map and boundary recommendations.

Review focus: ownership, coupling, transaction boundaries.

```text
Analyze bounded contexts for [project/domain].

Produce:
- candidate contexts
- responsibilities
- owned data
- APIs/events between contexts
- risks
- MVP module recommendation
```

## API Strategy

When to use: before API implementation.

Expected output: API style, resources, contracts, errors, versioning.

Review focus: consumer needs, compatibility, auth, observability.

```text
Define the API strategy for [project/feature].

Prefer REST unless GraphQL or gRPC is justified. Do not simply follow my preferred choices. Challenge my assumptions. Compare alternatives. Recommend based on rationale, not preference. Include endpoints, request/response shape, errors, auth, versioning, idempotency, and contract tests.
```

## Database Strategy

When to use: before schema design or migration.

Expected output: data ownership, schema approach, migration plan.

Review focus: ownership, integrity, indexing, rollback.

```text
Define the database strategy for [project/feature].

Include entities, ownership, relationships, transactions, indexes, migrations, rollback, retention, and audit needs.
```

## Event-Driven Strategy

When to use: only when async workflows are needed.

Expected output: event candidates, reliability model, alternatives.

Review focus: whether events are justified.

```text
Evaluate whether [project/feature] needs event-driven architecture.

Compare synchronous API, background job, queue, and event approaches. Recommend the simplest fit and document failure handling, idempotency, ordering, and observability.
```

## Infra Strategy

When to use: before environment or deployment design.

Expected output: infrastructure recommendation and trade-offs.

Review focus: managed services, cost, team capability.

```text
Define infrastructure strategy for [project].

Prefer managed infrastructure unless self-hosting is justified. Avoid Kubernetes unless operationally justified. Do not simply follow my preferred choices. Challenge my assumptions. Compare alternatives. Recommend based on rationale, not preference. Include deployment, environments, secrets, networking, monitoring, cost, and ownership.
```

## Observability Strategy

When to use: before production readiness.

Expected output: logs, metrics, traces, alerts, dashboards.

Review focus: supportability and incident diagnosis.

```text
Create an observability strategy for [project/feature].

Include key user journeys, logs, metrics, traces, dashboards, alerts, SLOs if relevant, and ownership.
```

## Security Model

When to use: before auth, permissions, data, or integration work.

Expected output: trust boundaries, roles, threats, controls.

Review focus: secure-by-default design.

```text
Create a security model for [project/feature].

Include identities, roles, permissions, sensitive data, trust boundaries, threats, mitigations, audit logs, and unresolved risks.
```

## Architecture Review

When to use: before major implementation or release.

Expected output: review decision, issues, risks, actions.

Review focus: blockers and decision quality.

```text
Review this architecture for [project/feature]:
[paste HLD/LLD/ADRs]

Return:
- summary
- blockers
- major issues
- minor issues
- security concerns
- operational concerns
- missing ADRs
- recommended next action
```


## Technology Stack Recommendation

When to use: before choosing frontend, backend, database, cloud, eventing, AI, or platform technologies.

Expected output: objective recommendation with alternatives, trade-offs, risks, and ADR requirement.

Review focus: product fit, team fit, complexity, maintainability, scalability, security, operations, cost, ecosystem, and evolution path.

```text
Recommend a technology stack for [project/feature].

Context:
[paste product goals, functional requirements, NFRs, team capability, budget, timeline, expected scale, security requirements, and any user-preferred options]

Do not simply follow my preferred choices. Challenge my assumptions. Compare alternatives. Recommend based on rationale, not preference. Treat user preference as input, not decision.

Use this output format:
1. User Preference
2. Dumbledore Assessment
3. Alternatives Considered
4. Trade-off Table
5. Decision
6. Why This Decision
7. What Would Change This Decision Later
8. Risks
9. ADR Required: Yes/No
```
