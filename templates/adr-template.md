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

# ADR Template

## Purpose

Capture one architecture decision with context, options, rationale, consequences, and review triggers.

## Status

Proposed | Accepted | Superseded | Deprecated

## Context

Describe the problem, constraints, forces, and why a decision is needed now.

## Decision

State the decision in one or two direct paragraphs.

## Options Considered

| Option | Benefits | Costs/Risks | When It Fits |
| --- | --- | --- | --- |
| Option A | TBD | TBD | TBD |
| Option B | TBD | TBD | TBD |

## Rationale

Explain why the selected option best fits the context.

## Consequences

- Positive outcomes.
- Negative consequences.
- Operational impact.
- Security impact.
- Cost impact.

## Review Triggers

- Scale changes.
- Team ownership changes.
- Reliability incidents.
- Security findings.
- Vendor or platform constraints.
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
