---
document_type: anti_pattern
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
  - anti-pattern
related_documents:
  - ../templates/adr-template.md
---

# Architecture Smells

## Purpose

Identify early warning signs that an architecture is becoming harder to change, operate, secure, or reason about.

## Recommended Sections

- Smell description.
- Why it matters.
- Detection signals.
- Corrective actions.
- Review questions.

## Common Smells

- No clear module ownership.
- Business rules scattered across UI, API, jobs, and database triggers.
- Every change requires cross-team coordination.
- Diagrams show technology boxes but not responsibility boundaries.
- Critical decisions are hidden in chat messages.

## Practical Guidance

When a smell appears, ask whether the design lacks boundaries, lacks decision records, or lacks operational feedback. Fix causes, not symptoms.
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
