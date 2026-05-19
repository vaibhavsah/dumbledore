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

# Multi-Tenant Patterns

## Purpose

Guide tenant isolation choices for SaaS systems.

## Practical Guidance

- Start with logical isolation when risk is low and speed matters.
- Use tenant-aware authorization, indexing, backup, export, and observability.
- Move to stronger isolation for compliance, enterprise tiers, data residency, or noisy-neighbor risk.

## Pattern Options

| Pattern | Benefits | Risks |
| --- | --- | --- |
| Shared schema with tenant_id | Simple and efficient | Query leaks if controls fail |
| Separate schema | Better isolation | More migration complexity |
| Separate database | Strong isolation | Higher operational cost |
| Separate deployment | Maximum isolation | Highest platform complexity |
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
