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

# SaaS Architecture Playbook

## Purpose

Guide reusable SaaS architecture decisions across tenancy, identity, billing, permissions, operations, data isolation, and growth.

## Practical Guidance

- Define tenant, account, workspace, user, role, and entitlement concepts early.
- Keep tenant isolation proportional to risk and customer tier.
- Build auditability, support tooling, and admin workflows as product capabilities.
- Separate product usage metering from financial billing when possible.

## MVP To Scale Path

| Stage | Recommended Shape | Watch For |
| --- | --- | --- |
| MVP | Modular monolith, shared database, logical tenant isolation | Leaky permissions, weak audit logs |
| Growth | Dedicated modules, stronger background processing, tenant-aware observability | Noisy tenants, migration pain |
| Scale | Selective service extraction, stronger isolation tiers, automated operations | Distributed complexity |
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
