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

# RFC Template

## Purpose

Provide a structured proposal format for changes that need review before a decision is recorded.

## Recommended Sections

- Summary.
- Motivation.
- Goals and non-goals.
- Current state.
- Proposal.
- Alternatives.
- Rollout plan.
- Risks and mitigations.
- Review feedback.
- Decision outcome and ADR link.

## Practical Guidance

Use RFCs when a change crosses teams, affects platform direction, changes operating model, or requires meaningful trade-off discussion. Do not use RFCs as bureaucracy for small local changes.

## Review Checklist

- Is the problem worth solving now?
- Are constraints explicit?
- Are alternatives credible?
- Is the rollout reversible?
- Does this require an ADR after discussion?
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
