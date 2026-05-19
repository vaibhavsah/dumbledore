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
  - nodejs
  - backend
  - api
related_documents:
  - ../../governance/api-design-checklist.md
  - ../../patterns/async-patterns.md
  - ../../governance/observability-checklist.md
---

# Node.js Governance

# Purpose

Define governance for Node.js APIs, BFFs, services, workers, and integration systems with async correctness, modularity, validation, observability, and operational simplicity.

# When To Use This Technology

Use Node.js for API layers, BFFs, real-time gateways, integration-heavy services, and teams that benefit from TypeScript across frontend and backend.

# When NOT To Use This Technology

Avoid Node.js for CPU-heavy workloads unless offloaded to workers or separate services. Avoid it when the team does not understand async failure modes.

# Recommended Architecture Patterns

| Pattern | Use When | Risk |
| --- | --- | --- |
| Modular API service | Domain APIs need clear ownership. | Giant app files if boundaries are weak. |
| BFF | Frontend-specific orchestration is needed. | Business logic may drift into BFF. |
| Worker service | Background jobs or queues are needed. | Retry and idempotency must be governed. |
| Hexagonal adapters | External integrations dominate complexity. | Can become over-abstracted. |

# Project Structure Guidance

- Organize by domain or feature module.
- Keep routes/controllers thin.
- Keep validation, application logic, and persistence separate.
- Keep config, logging, and error handling centralized.

# Code Organization Standards

- Use TypeScript for production systems.
- Validate all external input.
- Bound async concurrency.
- Use dependency injection or explicit composition without excessive framework magic.
- Keep business logic out of route handlers.

# API / Integration Guidance

- Define typed DTOs and consistent error contracts.
- Set timeouts for external calls.
- Use retries only with idempotency.
- Avoid hidden synchronous dependency chains.

# State Management Guidance

- Keep process memory state disposable.
- Do not rely on in-memory state for correctness across replicas.
- Use durable queues or storage for critical workflows.

# Error Handling Standards

- Do not swallow rejected promises.
- Use centralized error mapping.
- Preserve correlation IDs.
- Fail fast on invalid config.

# Security Guidance

- Validate inputs and sanitize outputs.
- Keep secrets outside source and logs.
- Review dependency risk.
- Enforce auth and authorization at backend boundaries.

# Testing Expectations

- Unit test domain logic and validators.
- Integration test APIs, persistence, and external adapters.
- Contract test important APIs.
- Test timeout, retry, and failure behavior.

# Observability Expectations

- Structured logs with request IDs.
- Metrics for latency, error rate, queue depth, and external dependency failures.
- Traces across API and worker boundaries.

# Performance Guidance

- Avoid blocking the event loop.
- Bound concurrency and payload sizes.
- Use worker threads or separate services for CPU-heavy tasks.
- Monitor event-loop lag.

# Scalability Guidance

- Scale stateless API processes horizontally.
- Move long-running tasks to workers.
- Use queues with dead-letter handling for async work.
- Keep shared caches and sessions external.

# Deployment & Operational Guidance

- Validate environment variables at startup.
- Include health checks and graceful shutdown.
- Handle SIGTERM correctly.
- Ensure workers stop safely.

# Code Review Checklist

- [ ] Routes are thin and validated.
- [ ] Async concurrency is bounded.
- [ ] Timeouts and retries are explicit.
- [ ] Business logic is in the correct module.
- [ ] Tests cover failure paths.
- [ ] Observability is present.

# Common Anti-Patterns

- Callback hell.
- Unbounded async concurrency.
- Giant Express apps.
- Business logic in routes.
- Missing validation.
- No timeout or retry policies.

# AI Coding Assistant Guardrails

- Inspect framework and module patterns before editing.
- Do not add unbounded `Promise.all` over large inputs.
- Add validation and tests with new endpoints.
- Do not hardcode config or secrets.

# Recommended Use Cases

- BFFs.
- APIs for SaaS applications.
- Integration services.
- Worker systems with clear async governance.

# Example Architecture Patterns

```text
src/
  modules/
    billing/
      billing.routes.ts
      billing.service.ts
      billing.repository.ts
      billing.schemas.ts
  shared/
    config/
    http/
    observability/
```

