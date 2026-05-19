---
document_type: template
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
  - template
related_documents: []
---

# Incident Review Template

## Purpose

Capture learning from production incidents without blame and convert findings into architecture, process, and operational improvements.

## Recommended Sections

- Summary.
- Timeline.
- Customer impact.
- Detection path.
- Contributing factors.
- What worked.
- What did not work.
- Corrective actions.
- Architecture implications.
- Follow-up ADRs or RFCs.

## Practical Guidance

- Separate symptom, trigger, and systemic cause.
- Assign owners and due dates to corrective actions.
- Update checklists when a reusable gap is discovered.

## Review Checklist

- Was detection fast enough?
- Did alerts reflect user impact?
- Was rollback available?
- Were dependencies visible?
- Did the architecture make failure contained or amplified?
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
