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

# Auth Patterns

## Purpose

Guide authentication and authorization architecture across SaaS, APIs, and agentic systems.

## Practical Guidance

- Keep authentication separate from authorization.
- Enforce authorization in trusted backends.
- Model tenant and role scope explicitly.
- Use policy checks for high-risk actions.
- Agents and automation require identities, permissions, and audit trails.

## Review Questions

- Who is the actor: user, service, job, or agent?
- What tenant or resource scope applies?
- Is authorization checked at every write boundary?
- Can privileged actions be audited?
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
