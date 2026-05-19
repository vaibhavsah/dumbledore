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

# Scalability Review Checklist

## Purpose

Evaluate whether the system can handle expected growth without introducing unnecessary complexity too early.

## Recommended Sections

- Current and target load.
- Critical paths and bottlenecks.
- MVP scaling strategy.
- Scale-stage evolution path.
- Load test and observability plan.
- Cost and operational trade-offs.

## Practical Guidance

- Require load assumptions before scale mechanisms.
- Identify the first likely bottleneck.
- Prefer staged evolution over one-time rewrites.

## Checklist

- [ ] Current and target load assumptions are stated.
- [ ] Critical paths are identified.
- [ ] Bottlenecks are measured or explicitly assumed.
- [ ] Caching strategy includes invalidation and correctness.
- [ ] Async processing protects user-facing latency where needed.
- [ ] Database scaling path is credible.
- [ ] Team and deployment scaling are considered.
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
