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

# Architecture Patterns Library

## Purpose

Provide an index of reusable architecture patterns and the decision criteria for applying them.

## Pattern Format

Each pattern should include purpose, context, forces, implementation guidance, trade-offs, anti-patterns, review questions, and examples.

## Common Patterns

| Pattern | Use When | Avoid When |
| --- | --- | --- |
| Modular monolith | Product is early and domain boundaries are forming | Teams need independent release and operation now |
| CQRS-lite | Read models differ materially from write model | It only adds naming complexity |
| Outbox | Reliable event publication is required from transactional changes | Events are non-critical and can be regenerated |
| API gateway | Cross-cutting ingress policy is needed | It becomes a business logic dumping ground |
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
