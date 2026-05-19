---
document_type: playbook
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
  - playbook
related_documents:
  - ../templates/adr-template.md
---

# Event-Driven Playbook

## Purpose

Guide when and how to use asynchronous messaging, events, queues, streams, and integration patterns.

## Practical Guidance

- Use events to decouple time, ownership, and reliability boundaries; do not use them to hide unclear domain boundaries.
- Define event ownership, schema evolution, idempotency, replay, ordering, and dead-letter behavior.
- Keep commands and events distinct. Commands request action; events state facts that happened.

## Review Questions

- Is async required for latency, reliability, scale, or integration independence?
- What happens when consumers fail?
- Can events be replayed safely?
- How are duplicate messages handled?
- Is eventual consistency acceptable to users?
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
