---
document_type: anti_pattern
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
  - anti-pattern
related_documents:
  - ../templates/adr-template.md
---

# Distributed Monoliths

## Purpose

Explain how systems get the cost of microservices without the independence benefits.

## Recommended Sections

- Warning signs.
- Root causes.
- Impact on delivery and operations.
- Consolidation options.
- Separation options.

## Warning Signs

- Services share the same database tables.
- Deployments must be coordinated across many services.
- Synchronous call chains mirror internal function calls.
- Ownership is split technically but not by business capability.
- Local development requires the entire platform.

## Practical Guidance

Return to business boundaries. Consolidate where independence is fake, or complete the separation by assigning data ownership, contracts, observability, and deployment ownership.
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
