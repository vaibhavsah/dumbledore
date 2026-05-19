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

## Code Review Checklist

- [ ] API, application, domain, infrastructure, worker, script, and AI provider boundaries are clear.
- [ ] Python idioms are used without accepting notebook-style production code.
- [ ] Production-critical code is typed and externally visible contracts are validated at runtime.
- [ ] Async paths do not perform blocking I/O or CPU-heavy work.
- [ ] Security checks cover input validation, secrets, file handling, AI data exposure, and sensitive logs.
- [ ] Tests cover domain logic, API behavior, provider adapters, async failure paths, and AI evaluation cases where relevant.
- [ ] Performance risks are checked: blocking async paths, memory-heavy batch work, dependency startup cost, and unbounded queues.
- [ ] Observability includes structured logs, request IDs, metrics, traces, provider latency, and AI cost/token signals where relevant.
- [ ] Dependency management is reproducible and reviewed.
- [ ] Maintainability is protected from giant utility modules, hidden side effects, and mixed scripts/services.
- [ ] AI-generated code is checked for fake library APIs, hidden side effects, missing tests, and insecure defaults.

## Code Review Red Flags

- Blocking operations in async request paths.
- Untyped critical code.
- Notebook-style production code.
- Hidden side effects at import time.
- Giant utility modules.
- Unpinned or unjustified dependencies.
- AI provider calls without timeout, cost controls, or auditability.
- File or user-content handling without validation.

## AI Coding Assistant Review Guardrails

AI-generated Python code must be reviewed for hallucinated APIs, fake library methods, inconsistent package patterns, over-abstraction, missing tests, missing failure handling, insecure defaults, hidden side effects, and architectural drift from scripts/notebooks into production services.

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
