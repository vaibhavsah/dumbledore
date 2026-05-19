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

# Frontend State Patterns

## Purpose

Guide frontend state decisions across server state, form state, local UI state, workflow state, and global application state.

## Practical Guidance

- Keep server state in data-fetching/cache abstractions.
- Keep form state local unless multiple steps require shared workflow state.
- Use global state for cross-cutting session, permissions, theme, or navigation context, not arbitrary domain data.
- Represent loading, error, empty, and stale states consistently.

## Review Questions

- Is this state derived from the server?
- Can it be recomputed instead of stored?
- What invalidates it?
- Does it survive navigation or reload?
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
