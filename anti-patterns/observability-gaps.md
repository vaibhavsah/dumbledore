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

# Observability Gaps

## Purpose

Identify common blind spots that make production systems difficult to debug and operate.

## Recommended Sections

- Missing signal.
- User impact.
- Debugging impact.
- Required instrumentation.
- Alert and runbook updates.

## Gaps

- Logs without correlation IDs.
- Metrics without business context.
- Alerts that do not map to user impact.
- Async jobs with no visible state.
- Dashboards nobody uses during incidents.
- AI systems without prompt, retrieval, tool-call, and approval traces.

## Practical Guidance

Design observability from critical user journeys outward. Every alert should have an owner, runbook, and expected action.
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
