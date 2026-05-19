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
  - project_kickoff
  - discovery
related_documents:
  - ../agents/architecture-governance-agent.md
  - ../templates/hld-template.md
---

# Project Kickoff Prompts

Use these prompts when starting a new product or major product area. Replace bracketed values with project-specific context.

## Product Discovery

| Field | Detail |
| --- | --- |
| When to use | At the start of a product or major initiative. |
| Expected output | Product summary, goals, users, workflows, unknowns, decision log. |

```text
Act as the Dumbledore Architecture Governance Agent. Help discover the product context for [project].

Known context:
[paste product notes]

Ask clarifying questions first if needed. Then produce:
- product goal
- target users
- core workflows
- MVP outcome
- non-goals
- assumptions
- open questions
- architecture implications
```

## MVP Scope Definition

When to use: when feature scope is unclear or too broad.

Expected output: MVP scope, excluded scope, risks, sequencing.

```text
Define the MVP scope for [project]. Separate must-have workflows from later roadmap items.

Use Dumbledore principles:
- simplicity first
- modular evolution
- explicit trade-offs

Produce:
- MVP capabilities
- non-MVP capabilities
- acceptance criteria
- delivery risks
- architecture decisions needed before implementation
```

## Domain Discovery

When to use: before HLD or module design.

Expected output: domain map, bounded contexts, ownership questions.

```text
Analyze the domains for [project].

Context:
[paste business processes, entities, users, workflows]

Produce:
- candidate bounded contexts
- core entities and ownership
- cross-context workflows
- integration points
- risks of wrong boundaries
- recommended MVP module boundaries
```

## User And Persona Discovery

When to use: before workflow, permission, or UX architecture.

Expected output: personas, permissions, workflows, edge cases.

```text
Identify user personas and role-based workflows for [project].

Produce:
- personas
- primary jobs to be done
- permissions and access boundaries
- critical workflows
- failure or exception workflows
- architecture implications for auth, audit, and UI state
```

## Functional Requirements Discovery

When to use: before development planning.

Expected output: capability list, user stories, dependencies, open questions.

```text
Convert the following product notes into functional requirements for [project]:
[paste notes]

Produce:
- capability groups
- user-facing requirements
- admin/internal requirements
- integration requirements
- reporting requirements
- assumptions and gaps
```

## Non-Functional Requirements Discovery

When to use: before architecture review or release planning.

Expected output: NFR table with priority and review criteria.

```text
Discover non-functional requirements for [project].

Consider scalability, availability, latency, security, compliance, observability, recovery, cost, maintainability, and developer productivity.

Produce a table with:
- requirement
- priority
- target or constraint
- why it matters
- how to validate it
```

## Architecture Constraint Discovery

When to use: before selecting architecture style or infrastructure.

Expected output: constraints, implications, decisions needed.

```text
Identify architecture constraints for [project].

Include:
- timeline
- team capability
- budget
- deployment environment
- data sensitivity
- integrations
- expected scale
- regulatory needs

Produce constraints, architecture implications, and ADRs likely needed.
```

## Team, Budget, And Timeline Discovery

When to use: before choosing managed services, microservices, Kubernetes, or complex platform investments.

Expected output: delivery model and architecture fit assessment.

```text
Assess team, budget, and timeline constraints for [project].

Context:
[team size, skills, budget, deadlines]

Recommend architecture choices that fit the team's operational capability. Call out choices that are too expensive or operationally risky.
```

## Compliance And Security Discovery

When to use: before data model, auth, integration, or deployment decisions.

Expected output: security requirements, audit needs, risks.

```text
Discover compliance and security requirements for [project].

Produce:
- sensitive data types
- role and permission needs
- audit logging requirements
- data retention expectations
- integration trust boundaries
- security review questions
- architecture risks
```

## Initial Repo Strategy

When to use: before creating project repositories.

Expected output: repo model, ownership, docs locations.

```text
Recommend an initial repository strategy for [project].

Assume project-specific HLDs, LLDs, ADRs, and implementation docs must live in the project repo. Dumbledore is only reusable governance.

Produce:
- recommended repos
- folder structure for docs
- ADR location
- module ownership approach
- CI and review expectations
```

## Initial Architecture Roadmap

When to use: after MVP scope and constraints are known.

Expected output: MVP architecture, scale-stage roadmap, ADR list.

```text
Create an initial architecture roadmap for [project].

Separate:
- MVP architecture
- post-MVP hardening
- scale-stage evolution
- decisions that require ADRs
- risks to monitor
- review checkpoints
```

