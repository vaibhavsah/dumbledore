---
document_type: principle
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
  - engineering
  - delivery
related_documents:
  - ../templates/adr-template.md
---

# Engineering Philosophy

## Purpose

Set expectations for pragmatic engineering behavior: build maintainable systems, make decisions visible, and reduce accidental complexity.

## Recommended Sections For Engineering Plans

- Problem statement.
- User and operator impact.
- Delivery constraints.
- Simplicity strategy.
- Testing and rollout plan.
- Known compromises and expiry dates.

## Practical Guidance

- Optimize for changeability before raw throughput unless performance is already measured as a bottleneck.
- Keep code, documentation, and operations aligned. A design nobody can operate is incomplete.
- Use strong defaults and narrow extension points. Open-ended extensibility creates hidden product commitments.
- Prefer boring technology for undifferentiated work.
- Make quality gates proportional to blast radius.

## Example Engineering Standard

A team may accept a manual operational step during MVP if the step is documented, auditable, low frequency, and has an owner. It should become automated when frequency, risk, or handoff cost rises.

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
