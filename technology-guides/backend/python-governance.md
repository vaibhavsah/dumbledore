---
document_type: technology_governance
scope: reusable
audience:
  - architects
  - engineering_managers
  - principal_engineers
  - developers
  - ai_agents
status: draft
review_cycle: quarterly
tags:
  - python
  - backend
  - ai
related_documents:
  - ../../principles/ai-system-principles.md
  - ../../playbooks/ai-agent-platform-playbook.md
  - ../../governance/production-readiness-checklist.md
---

# Python Governance

# Purpose

Define governance for Python backend services, AI systems, automation, and production workflows. The guide separates scripting from production systems and emphasizes typing, boundaries, observability, testing, and dependency control.

# When To Use This Technology

Use Python for AI/ML systems, data-heavy workflows, FastAPI services, automation, and product areas where ecosystem speed matters.

# When NOT To Use This Technology

Avoid Python for latency-critical CPU-heavy services unless the workload is offloaded or the performance profile is proven acceptable.

# Recommended Architecture Patterns

| Pattern | Use When | Risk |
| --- | --- | --- |
| FastAPI service | Typed API service is needed. | Blocking calls in async paths. |
| Worker pipeline | Background data or AI jobs are needed. | Hidden side effects. |
| Package modules | Production code needs ownership boundaries. | Giant utility modules. |
| Model gateway | AI providers need isolation. | Prompt and policy drift. |

# Project Structure Guidance

- Separate API, application, domain, infrastructure, and model/provider adapters.
- Keep notebooks out of production paths.
- Keep scripts separate from services.
- Avoid broad `utils.py` modules.

# Code Organization Standards

- Use type hints for production code.
- Validate external input with schemas.
- Keep side effects explicit.
- Pin and review dependencies.
- Keep AI prompts/config versioned and observable when used in production.

# API / Integration Guidance

- Use DTOs and validation at API boundaries.
- Set timeouts for external calls.
- Avoid blocking calls in async request paths.
- Wrap AI provider integrations behind explicit interfaces.

# State Management Guidance

- Avoid hidden global mutable state.
- Treat caches, model clients, and connection pools as lifecycle-managed dependencies.
- Keep data pipeline state durable and auditable.

# Error Handling Standards

- Classify domain, validation, dependency, and provider errors.
- Preserve diagnostic context without leaking sensitive data.
- Make retry behavior explicit.

# Security Guidance

- Protect API keys, prompts containing sensitive context, and model outputs.
- Validate files, inputs, and user-provided content.
- Audit AI tool calls and sensitive data access.

# Testing Expectations

- Unit test domain logic and prompt/mapping utilities.
- Integration test API and persistence boundaries.
- Use golden/evaluation tests for AI behavior where applicable.
- Test async failure and timeout behavior.

# Observability Expectations

- Structured logs and request IDs.
- Metrics for latency, errors, dependency failures, queue depth, and AI token/cost usage.
- Trace external provider calls where feasible.

# Performance Guidance

- Avoid blocking operations in async paths.
- Use workers for CPU-heavy or long-running work.
- Monitor memory and dependency startup cost.
- Batch carefully with backpressure.

# Scalability Guidance

- Scale APIs statelessly.
- Move heavy workflows to queues/workers.
- Use durable storage for task state.
- Define cost controls for AI workloads.

# Deployment & Operational Guidance

- Pin dependencies and generate reproducible builds.
- Validate config at startup.
- Separate notebooks, experiments, and production packages.
- Include health checks and smoke tests.

# Code Review Checklist

- [ ] Production code is typed.
- [ ] External inputs are validated.
- [ ] Async paths do not block.
- [ ] Dependencies are pinned and justified.
- [ ] AI behavior is evaluated and observable where relevant.
- [ ] Tests cover failure paths.

# Common Anti-Patterns

- Notebook-driven production.
- Untyped codebases.
- Giant utility modules.
- Hidden side effects.
- Blocking operations in async paths.

# AI Coding Assistant Guardrails

- Do not turn notebook code directly into production code.
- Add types, validation, and tests.
- Do not hardcode prompts, secrets, or provider keys.
- Include cost and evaluation considerations for AI features.

# Recommended Use Cases

- AI services.
- FastAPI APIs.
- Data workflows.
- Automation with production controls.

# Example Architecture Patterns

```text
app/
  api/
  application/
  domain/
  infrastructure/
  ai/
    providers/
    evaluations/
```

