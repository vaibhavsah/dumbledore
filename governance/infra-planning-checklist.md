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

# Infrastructure Planning Checklist

## Purpose

Review infrastructure choices for reliability, cost, security, deployment safety, and team operability.

## Recommended Sections

- Environment model.
- Deployment and rollback plan.
- Network, identity, and secrets model.
- Capacity and cost assumptions.
- Backup and recovery targets.
- Operational ownership.

## Practical Guidance

- Start with managed services unless requirements justify ownership.
- Separate environment strategy from deployment strategy.
- Design rollback, secrets, identity, and network boundaries before production.

## Checklist

- [ ] Environment model is defined.
- [ ] Deployment process is repeatable.
- [ ] Rollback path is tested.
- [ ] Secrets and configuration are managed centrally.
- [ ] Network boundaries and ingress/egress are understood.
- [ ] Capacity and cost assumptions are documented.
- [ ] Backups and recovery targets are defined.
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
