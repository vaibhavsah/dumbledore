---
document_type: checklist
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
  - governance
  - review
related_documents:
  - ../templates/adr-template.md
---

# API Design Checklist

## Purpose

Review APIs for clarity, consistency, evolvability, security, and operational behavior.

## Recommended Sections

- API purpose and consumers.
- Resource or command model.
- Authentication and authorization.
- Request and response contracts.
- Errors, retries, idempotency, and versioning.
- Observability and operational ownership.

## Practical Guidance

- Design APIs around business capabilities and stable resource concepts.
- Define authentication, authorization, pagination, filtering, sorting, validation, errors, idempotency, rate limits, and versioning.
- Treat APIs as contracts with lifecycle ownership.

## Checklist

- [ ] API purpose and consumers are defined.
- [ ] Resource names and commands are consistent.
- [ ] Authorization rules are explicit per operation.
- [ ] Error response format is standardized.
- [ ] Idempotency is defined for retries and writes.
- [ ] Pagination and limits prevent unbounded reads.
- [ ] Backward compatibility strategy is clear.
- [ ] Observability includes request IDs, latency, errors, and saturation.
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
