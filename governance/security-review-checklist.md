---
document_type: checklist
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
  - governance
  - review
related_documents:
  - ../templates/adr-template.md
---

# Security Review Checklist

## Purpose

Provide a reusable security review baseline for application, platform, data, and AI-enabled systems.

## Recommended Sections

- Assets and trust boundaries.
- Identity and access model.
- Data classification and protection.
- Threats and mitigations.
- Auditability and incident response.
- Residual risks and acceptance owner.

## Practical Guidance

- Review threats early enough to affect design.
- Enforce identity, authorization, secrets management, data protection, and auditability through system controls.
- Do not rely on UI hiding or prompt instructions as security boundaries.

## Checklist

- [ ] Assets and trust boundaries are identified.
- [ ] Authentication method is appropriate for risk.
- [ ] Authorization is enforced server-side.
- [ ] Least privilege applies to users, services, agents, and jobs.
- [ ] Secrets are stored and rotated safely.
- [ ] Sensitive data is encrypted in transit and at rest.
- [ ] Audit logs cover privileged and high-risk actions.
- [ ] AI tools have permission boundaries and approval gates where needed.
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
