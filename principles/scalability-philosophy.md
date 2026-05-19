---
document_type: principle
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
  - scalability
  - performance
related_documents:
  - ../templates/adr-template.md
---

# Scalability Philosophy

## Purpose

Keep scalability work grounded in measured demand, clear bottlenecks, and staged evolution.

## Recommended Sections

- Current load and growth assumptions.
- Performance goals.
- Known bottlenecks.
- MVP capacity strategy.
- Scale-stage architecture.
- Load test and monitoring plan.

## Practical Guidance

- Scale vertically, cache carefully, and optimize queries before distributing systems.
- Scale teams and deployment cadence as deliberately as traffic.
- Separate read scaling, write scaling, storage scaling, and organizational scaling; they rarely need the same solution at the same time.
- Define load shapes: steady traffic, bursts, batch jobs, fan-out, and noisy tenants.

## Scale Trigger Examples

- Sustained CPU, memory, or database saturation after local optimization.
- A domain module requires independent deployment due to release cadence or risk.
- Tenant isolation requirements exceed logical isolation.
- Event volume requires asynchronous processing to protect user-facing latency.

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
