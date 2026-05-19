---
document_type: pattern
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
  - pattern
related_documents:
  - ../templates/adr-template.md
---

# API Patterns

## Purpose

Capture reusable API design patterns for internal and external interfaces.

## Practical Guidance

- Use resource APIs for stable domain objects.
- Use command endpoints for business actions that do not map cleanly to CRUD.
- Use idempotency keys for retried writes.
- Use cursor pagination for large or changing collections.

## Example

A payment capture command should be idempotent because client retries can otherwise double-charge or create duplicate downstream work.
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
