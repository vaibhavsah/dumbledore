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
  - development
  - implementation
  - ai_coding
related_documents:
  - ../agents/development-agent.md
  - ../templates/lld-template.md
---

# Development Prompts

## Shared Guardrails

- Respect architecture boundaries.
- Avoid broad rewrites.
- Generate or update tests.
- Explain assumptions.
- Keep changes small and reviewable.
- Do not introduce unnecessary abstractions.

## Convert HLD To Implementation Plan

When to use: after HLD approval.

Expected output: sequenced work plan.

Guardrails: keep project-specific outputs in the project repo.

```text
Using this HLD, create an implementation plan:
[paste HLD]

Break work into backend, frontend, database, API, tests, infrastructure, and documentation tasks. Identify vertical slices, dependencies, risks, and review checkpoints.
```

## Vertical Slice Planning

When to use: before coding a feature.

Expected output: thin end-to-end slice plan.

Guardrails: avoid giant PRs.

```text
Create a vertical slice plan for [feature].

Include the smallest useful UI, API, domain logic, persistence, tests, and release validation. Keep it reviewable in one PR where possible.
```

## Backend Feature Implementation Plan

When to use: before backend coding.

Expected output: module, API, data, tests, risks.

Guardrails: keep controllers thin and domain logic in the correct layer.

```text
Plan backend implementation for [feature].

Include affected modules, domain rules, APIs, validation, authorization, data access, migrations, error handling, observability, and tests.
```

## Frontend Feature Implementation Plan

When to use: before frontend coding.

Expected output: components, state, API integration, UX states.

Guardrails: do not leak domain logic into UI.

```text
Plan frontend implementation for [feature].

Include pages/components, state ownership, API calls, loading/empty/error/permission states, accessibility, tests, and integration risks.
```

## API Implementation Plan

When to use: before building or changing APIs.

Expected output: endpoint plan and contract tests.

Guardrails: preserve compatibility.

```text
Plan API implementation for [feature].

Include resources, endpoints, request/response schemas, errors, auth, idempotency, versioning, contract tests, and observability.
```

## DB Migration Plan

When to use: before schema or data changes.

Expected output: migration sequence and rollback plan.

Guardrails: avoid destructive changes without compatibility.

```text
Create a DB migration plan for [change].

Include schema changes, data migration, backfill, indexes, compatibility period, rollback/forward-fix strategy, tests, and release risks.
```

## Integration Plan

When to use: before connecting internal or external systems.

Expected output: integration contract and failure model.

Guardrails: define timeout, retry, and idempotency.

```text
Create an integration plan for [systems].

Include contracts, authentication, data mapping, error handling, retries, idempotency, rate limits, observability, and test strategy.
```

## Environment Setup Plan

When to use: before local, test, staging, or production environment setup.

Expected output: environment checklist.

Guardrails: avoid hardcoded secrets.

```text
Create an environment setup plan for [project].

Include config, secrets, local dependencies, CI variables, staging/prod differences, database setup, seed data, and smoke validation.
```

## AI Coding Assistant Implementation Prompt

When to use: when asking Codex, Cursor, Claude, or Windsurf to implement code.

Expected output: small patch with tests.

Guardrails: require changed files and verification commands.

```text
You are implementing [feature] in [repo].

Context:
- Architecture boundary: [boundary]
- Relevant HLD/LLD/ADR: [links or pasted context]
- Required behavior: [behavior]

Before editing, inspect existing patterns. Then implement the smallest reviewable change. Add or update tests. Do not rewrite unrelated code. After implementation, report changed files, assumptions, tests run, and residual risks.
```

## Step-By-Step Development Execution

When to use: when a feature needs guided execution.

Expected output: ordered execution checklist.

Guardrails: validate after each step.

```text
Create a step-by-step execution checklist for [feature].

Include:
- code inspection steps
- implementation steps
- tests after each step
- review checkpoints
- rollback notes
- final verification
```

