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

# Database Strategy Checklist

## Purpose

Review data architecture for correctness, ownership, consistency, scale, migrations, and recovery.

## Recommended Sections

- Data ownership.
- Consistency and transaction boundaries.
- Schema and index strategy.
- Multi-tenancy and isolation.
- Migration and recovery plan.
- Privacy, audit, and retention.

## Practical Guidance

- Start with the simplest data model that protects invariants.
- Keep transactional boundaries explicit.
- Treat migrations as production changes with rollback implications.

## Checklist

- [ ] Data ownership is clear by module or service.
- [ ] Consistency requirements are explicit.
- [ ] Indexes match query patterns.
- [ ] Multi-tenancy model is defined if applicable.
- [ ] Migration and rollback strategy is documented.
- [ ] Backup, restore, RPO, and RTO are defined.
- [ ] PII and sensitive data handling is reviewed.
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
