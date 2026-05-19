---
document_type: example
scope: reusable
audience:
  - engineering_managers
  - solution_architects
  - principal_engineers
  - technical_leads
  - ai_agents
status: draft
review_cycle: quarterly
tags:
  - example
related_documents:
  - ../templates/adr-template.md
---

# Sample ADR: Start With A Modular Monolith

## Status

Accepted for sample purposes.

## Context

The product is pre-scale. Domain boundaries are emerging, and the team needs high delivery speed with limited operational overhead.

## Decision

Start with a modular monolith organized by business capabilities. Preserve clear module APIs and table ownership. Defer service extraction until scale, ownership, or compliance requirements justify it.

## Alternatives

| Option | Benefits | Risks |
| --- | --- | --- |
| Modular monolith | Fast delivery, simpler operations | Boundary erosion if unmanaged |
| Microservices | Independent deployability | High platform and coordination cost |
| Serverless functions only | Low initial infrastructure | Fragmented business logic |

## Consequences

The team must enforce module boundaries through code review and tests. Future extraction remains possible but is not free.
## Anti-Patterns

- Treating this document as a technology mandate instead of a decision aid.
- Copying examples without validating domain, team, scale, and operating constraints.
- Skipping explicit trade-offs because one option feels familiar.
- Optimizing for theoretical scale before proving product and usage patterns.

## Review Questions

- Does this guidance favor the simplest architecture that can satisfy current constraints?
- Are MVP and scale-stage choices separated clearly?
- Are trade-offs, risks, and alternatives explicit?
- Can a human reviewer and an AI agent apply this guidance without project-specific assumptions?
- Are security, operability, cost, and maintainability considered before novelty?
