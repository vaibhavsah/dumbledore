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

# Async Patterns

## Purpose

Guide reliable asynchronous work using queues, events, workers, schedulers, and retries.

## Practical Guidance

- Make handlers idempotent.
- Use retries with backoff and dead-letter handling.
- Track job state for user-visible workflows.
- Design poison message handling before production.

## Patterns

- Transactional outbox.
- Saga with compensating actions.
- Work queue.
- Event notification.
- Scheduled reconciliation.
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
