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
  - golang
  - backend
  - concurrency
related_documents:
  - ../../patterns/async-patterns.md
  - ../../governance/production-readiness-checklist.md
---

# Golang Governance

# Purpose

Define governance for Go services, APIs, workers, and event-driven systems with emphasis on simplicity, concurrency correctness, observability, and operational efficiency.

# When To Use This Technology

Use Go for services that need simple deployment, efficient concurrency, workers, platform tooling, APIs, and predictable runtime behavior.

# When NOT To Use This Technology

Avoid Go when the domain benefits heavily from mature enterprise frameworks, dynamic experimentation, or the team lacks Go concurrency discipline.

# Recommended Architecture Patterns

| Pattern | Use When | Risk |
| --- | --- | --- |
| Small service | Clear bounded capability exists. | Service sprawl. |
| Worker pool | Concurrent background processing is needed. | Leaking goroutines. |
| Ports and adapters | External dependencies need isolation. | Interface overuse. |
| Event consumer | Async processing is justified. | Ordering and idempotency complexity. |

# Project Structure Guidance

- Keep package boundaries simple and purposeful.
- Use `internal/` for private application packages.
- Avoid generic package names like `utils`.
- Keep interfaces close to consumers.

# Code Organization Standards

- Prefer explicit code over clever abstractions.
- Use context for cancellation and deadlines.
- Keep goroutine lifecycle owned.
- Return errors with useful context.
- Avoid Java-style OOP patterns.

# API / Integration Guidance

- Define explicit request, response, and error contracts.
- Use timeouts and context propagation.
- Treat retries as idempotency decisions.
- Validate payloads at boundaries.

# State Management Guidance

- Avoid hidden mutable shared state.
- Protect shared state with clear synchronization.
- Prefer stateless services where possible.

# Error Handling Standards

- Check errors.
- Wrap errors with context where useful.
- Do not log and return the same error repeatedly without reason.
- Classify retryable and non-retryable errors.

# Security Guidance

- Validate inputs.
- Avoid leaking sensitive data in logs.
- Use least-privilege credentials.
- Review dependency and container image risks.

# Testing Expectations

- Unit test business logic.
- Integration test adapters and persistence.
- Race-test concurrent code where relevant.
- Test cancellation, timeout, and retry behavior.

# Observability Expectations

- Structured logs.
- Metrics for latency, errors, queue depth, goroutines, and dependency failures.
- Tracing for request and worker flows.

# Performance Guidance

- Measure before optimizing.
- Bound goroutines and channels.
- Watch allocations and lock contention in hot paths.
- Use profiling for performance decisions.

# Scalability Guidance

- Scale stateless services horizontally.
- Use queues for async workloads.
- Make worker processing idempotent.
- Keep backpressure explicit.

# Deployment & Operational Guidance

- Build small static binaries where possible.
- Support graceful shutdown.
- Expose health checks.
- Configure timeouts and connection pools.

## Code Review Checklist

- [ ] Package, handler, service, repository, adapter, worker, and internal boundaries are clear.
- [ ] Go idioms are followed: simple composition, explicit errors, small interfaces, and context propagation.
- [ ] Goroutine lifecycle is owned and cancellation paths are clear.
- [ ] Shared mutable state is synchronized or avoided.
- [ ] API and integration code uses validation, deadlines, and explicit retry/idempotency behavior.
- [ ] Security checks cover input validation, secrets, auth, and sensitive logging.
- [ ] Tests cover business logic, adapters, concurrency, cancellation, timeouts, and failure paths.
- [ ] Performance risks are checked: goroutine leaks, allocation-heavy hot paths, lock contention, and unbounded queues.
- [ ] Observability includes structured logs, metrics, traces, queue depth, and dependency signals.
- [ ] Maintainability is protected from Java-style OOP, excessive interfaces, and magic frameworks.
- [ ] AI-generated code is checked for ignored errors, fake APIs, and hidden concurrency.

## Code Review Red Flags

- Goroutine leaks or goroutines started without ownership.
- Ignored errors.
- Shared mutable state without synchronization.
- Context misuse, missing deadlines, or lost cancellation.
- Channels used without clear close/backpressure semantics.
- Interfaces created before a consumer needs them.
- Retry loops without idempotency or backoff.
- Missing race-sensitive tests.

## AI Coding Assistant Review Guardrails

AI-generated Go code must be reviewed for hallucinated APIs, fake library methods, inconsistent package patterns, over-abstraction through unnecessary interfaces, missing tests, missing failure handling, insecure defaults, ignored errors, and architectural drift through hidden concurrency.

# Common Anti-Patterns

- Over-engineered abstractions.
- Java-style OOP in Go.
- Leaking goroutines.
- Hidden concurrency.
- Poor error handling.
- Magic frameworks.

# AI Coding Assistant Guardrails

- Do not introduce interfaces unless they serve a clear consumer need.
- Always handle errors.
- Add context cancellation for external calls.
- Include tests for concurrent behavior where relevant.

# Recommended Use Cases

- Platform services.
- Worker systems.
- High-throughput APIs.
- Event consumers.

# Example Architecture Patterns

```text
cmd/service/main.go
internal/
  orders/
    handler.go
    service.go
    repository.go
  platform/
    config/
    observability/
```
