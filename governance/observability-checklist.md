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

# Observability Checklist

## Purpose

Ensure systems can be understood, debugged, and operated under normal and failure conditions.

## Recommended Sections

- Critical user journeys.
- Logs, metrics, and traces.
- SLOs and alert policy.
- Dashboards and runbooks.
- Retention, privacy, and cost controls.
- Review findings and owners.

## Practical Guidance

- Instrument user journeys, not only infrastructure.
- Prefer actionable alerts tied to SLOs.
- Include cost and dependency visibility.

## Checklist

- [ ] Logs include correlation IDs and key business identifiers where safe.
- [ ] Metrics cover latency, traffic, errors, saturation, and business flow health.
- [ ] Traces cover critical synchronous and asynchronous paths.
- [ ] Dashboards answer operator questions.
- [ ] Alerts map to user impact or imminent capacity risk.
- [ ] Runbooks exist for critical alerts.
- [ ] Data retention balances debugging value, cost, and privacy.
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
