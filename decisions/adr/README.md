---
document_type: example
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
  - adr
  - governance
related_documents:
  - ../templates/adr-template.md
---

# Dumbledore ADRs

## Purpose

This folder stores architecture decision records for Dumbledore itself: governance structure, document standards, review cadence, repository policy, and reusable framework evolution.

## Recommended Sections

- Decision title and status.
- Context.
- Decision.
- Options considered.
- Consequences.
- Review triggers.

## Usage Rules

- Store only Dumbledore decisions here.
- Store product or project ADRs in the relevant project repository.
- Use `templates/adr-template.md` for new ADRs.
- Number ADRs sequentially as `adr-0001-short-title.md`.

## Review Questions

- Does the ADR change reusable governance guidance?
- Is the decision broader than a single project?
- Are consequences and review triggers explicit?
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
