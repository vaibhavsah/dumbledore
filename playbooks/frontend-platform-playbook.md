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

# Frontend Platform Playbook

## Purpose

Guide frontend-heavy systems where product velocity, consistency, performance, accessibility, and state management matter.

## Practical Guidance

- Treat design systems, routing, data fetching, state, permissions, and telemetry as platform concerns.
- Keep domain state close to the business workflow; avoid global stores for everything.
- Make performance budgets explicit.
- Accessibility and internationalization are architecture concerns, not polish tasks.

## Review Questions

- Where does server state live?
- Where does client-only interaction state live?
- How are permissions enforced and reflected in UI?
- How are errors, loading states, and empty states standardized?
- What is the bundle and runtime performance strategy?
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
