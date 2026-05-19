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
  - code_review
  - pr_review
related_documents:
  - ../agents/code-review-agent.md
---

# Code Review Prompts

## Expected Review Output Format

- Summary.
- Blockers.
- Major issues.
- Minor issues.
- Suggestions.
- Tests missing.
- Security concerns.
- Architecture concerns.
- Recommended next action.

Severity classification: Blocker, Major, Minor, Suggestion.

## General PR Review

When to use: for any pull request.

Expected output: full review using the expected format.

```text
Review this PR as the Dumbledore Code Review Agent.

Context:
[paste goal, HLD/LLD/ADR links, diff or files]

Focus on correctness, maintainability, tests, architecture fit, security, observability, and production risk. Classify every finding by severity.
```

## Architecture Boundary Review

When to use: when a change touches modules, services, or domain logic.

Expected output: boundary violations and patch plan.

```text
Review this change for architecture boundary violations.

Architecture context:
[paste HLD/LLD/ADR]

Diff:
[paste diff]

Identify domain leakage, wrong-layer logic, hidden coupling, and architecture drift. Provide fixes.
```

## Backend Code Review

When to use: backend feature or service changes.

Expected output: backend correctness and maintainability findings.

```text
Review this backend change.

Focus on domain logic, validation, authorization, transactions, data access, error handling, observability, tests, and performance.
```

## Frontend Code Review

When to use: frontend feature changes.

Expected output: UI correctness, state, integration, and test findings.

```text
Review this frontend change.

Focus on component boundaries, state ownership, API integration, loading/empty/error states, permissions, accessibility, testability, and maintainability.
```

## API Contract Review

When to use: API changes.

Expected output: contract safety findings.

```text
Review this API contract change.

Focus on compatibility, request/response schema, validation, errors, auth, idempotency, versioning, observability, and contract tests.
```

## DB Migration Review

When to use: schema, data migration, or query changes.

Expected output: data safety and rollback findings.

```text
Review this DB migration.

Focus on data safety, backward compatibility, indexes, locks, rollback/forward-fix strategy, backfills, transactions, and tests.
```

## Security Code Review

When to use: auth, permissions, secrets, sensitive data, integrations.

Expected output: security blockers and mitigations.

```text
Review this change for security risks.

Focus on authentication, authorization, input validation, secrets, sensitive data exposure, audit logs, dependency risk, and trust boundaries.
```

## Performance Review

When to use: query-heavy, high-traffic, batch, or latency-sensitive code.

Expected output: performance risks and validation plan.

```text
Review this change for performance risk.

Focus on query behavior, N+1 risks, caching, memory usage, concurrency, external calls, latency, and load test needs.
```

## Maintainability Review

When to use: complex or fast-moving areas.

Expected output: maintainability risks and simplification suggestions.

```text
Review this change for maintainability.

Focus on readability, unnecessary abstraction, duplication, module boundaries, naming, testability, and future change cost.
```

## AI-Generated Code Review

When to use: reviewing code produced by AI assistants.

Expected output: hallucination, boundary, and test findings.

```text
Review this AI-generated code.

Assume it may contain plausible but incorrect behavior. Verify against existing patterns, architecture boundaries, tests, error handling, security, and runtime assumptions.
```

