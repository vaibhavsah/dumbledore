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

# Microservices Evolution Playbook

## Purpose

Guide responsible evolution from modular monoliths or coarse services to microservices when justified by domain, scale, compliance, or team needs.

## Practical Guidance

- Extract services only when boundaries are already stable.
- Require independent data ownership, deployment ownership, and operational ownership.
- Start with one extraction and learn from it before broad decomposition.
- Budget for observability, CI/CD, security, incident response, and platform support.

## Extraction Criteria

- The module has high change frequency independent of the core.
- The module has distinct scale or reliability requirements.
- The domain boundary is stable and well understood.
- The owning team can operate the service.
- Cross-boundary transactions are avoidable or explicitly managed.
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
