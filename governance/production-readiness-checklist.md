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

# Production Readiness Checklist

## Purpose

Confirm a service or system is ready to handle real users, failures, operational handoffs, and ongoing change.

## Recommended Sections

- Launch scope and ownership.
- Health targets and SLOs.
- Monitoring, alerting, and runbooks.
- Security and compliance status.
- Load, failure, and recovery evidence.
- Open risks and acceptance owner.

## Practical Guidance

Use this checklist before launch, before major scale events, and after large architecture changes. Findings should have owners and severity.

## Checklist

- [ ] Owner and escalation path are defined.
- [ ] SLOs or launch health targets are defined.
- [ ] Monitoring, alerting, and runbooks exist.
- [ ] Rollback and recovery procedures are tested.
- [ ] Security review findings are resolved or accepted.
- [ ] Load and failure testing match launch risk.
- [ ] Cost limits and capacity alerts exist.
- [ ] Support and incident process is ready.
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
