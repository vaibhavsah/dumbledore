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

# Scaling Failures

## Purpose

Document recurring ways systems fail while trying to scale traffic, teams, data, or operations.

## Recommended Sections

- Failure mode.
- Trigger conditions.
- Business and operational impact.
- Prevention strategy.
- Recovery strategy.

## Failure Modes

- Adding services before domain boundaries are stable.
- Caching without invalidation ownership.
- Read replicas masking poor query design.
- Async workflows without idempotency.
- Scaling infrastructure while support processes remain manual.

## Review Questions

- Is the bottleneck measured?
- Is the proposed fix addressing the bottleneck or adding capacity theater?
- What new operational burden appears?
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
