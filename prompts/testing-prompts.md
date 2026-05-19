---
document_type: prompt_library
scope: reusable
audience:
  - engineering_managers
  - solution_architects
  - principal_engineers
  - technical_leads
  - developers
  - ai_agents
status: draft
review_cycle: monthly
tags:
  - testing
  - quality
related_documents:
  - ../agents/testing-agent.md
---

# Testing Prompts

## Test Strategy Generation

When to use: before implementation or release.

Expected output: test strategy and matrix.

Test coverage focus: critical workflows and risk-based coverage.

```text
Create a test strategy for [feature/system].

Include unit, integration, contract, E2E, smoke, performance, security, and regression coverage. Prioritize by business risk and production impact.
```

## Unit Test Generation

When to use: for domain logic and edge cases.

Expected output: unit test cases.

Test coverage focus: business rules and branches.

```text
Generate unit test cases for [module/function].

Include normal cases, edge cases, invalid input, permission-related behavior if relevant, and expected failures. Avoid testing implementation details.
```

## Integration Test Planning

When to use: for persistence, adapters, framework wiring.

Expected output: integration test plan.

Test coverage focus: module boundaries and real dependencies where valuable.

```text
Plan integration tests for [feature].

Include database behavior, external adapter boundaries, transactions, error handling, and setup/cleanup strategy.
```

## Contract Test Planning

When to use: APIs consumed by frontend, services, or external systems.

Expected output: provider and consumer contract plan.

Test coverage focus: compatibility and breaking changes.

```text
Plan contract tests for [API].

Include request/response schemas, errors, auth expectations, versioning, backward compatibility, and consumer assumptions.
```

## E2E Test Planning

When to use: critical user journeys.

Expected output: small E2E suite plan.

Test coverage focus: end-to-end business confidence.

```text
Plan E2E tests for [workflow].

Keep tests limited to critical journeys. Include setup data, steps, assertions, failure handling, and flakiness risks.
```

## Smoke Test Planning

When to use: before release or deployment automation.

Expected output: smoke checklist.

Test coverage focus: deployability and critical health.

```text
Create a smoke test plan for [system].

Include service health, login/auth if relevant, core API response, database connectivity, background job health, and critical UI route checks.
```

## Edge Case Discovery

When to use: before finalizing tests.

Expected output: edge case list by risk.

Test coverage focus: boundary values and unusual states.

```text
Discover edge cases for [feature].

Consider permissions, empty data, duplicate data, invalid states, concurrency, time zones, partial failures, retries, and large data sets.
```

## Failure Scenario Discovery

When to use: for production-critical workflows.

Expected output: failure scenarios and expected behavior.

Test coverage focus: graceful degradation and recovery.

```text
Identify failure scenarios for [workflow].

Include dependency outage, database failure, timeout, invalid input, authorization failure, partial success, retry behavior, and observability expectations.
```

## Regression Test Planning

When to use: after bugs, incidents, or risky refactors.

Expected output: regression suite additions.

Test coverage focus: preventing repeat failures.

```text
Create a regression test plan for [bug/risk].

Include root behavior, minimal reproduction, test type, assertions, and where the test should live.
```

## CI Test Pipeline Review

When to use: before relying on CI for release confidence.

Expected output: CI gaps and recommendations.

Test coverage focus: fast feedback and release confidence.

```text
Review the CI test pipeline for [project].

Assess speed, reliability, unit/integration/e2e split, smoke tests, artifacts, flaky tests, required checks, and release blockers.
```

