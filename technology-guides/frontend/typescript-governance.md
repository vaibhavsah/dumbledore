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
  - typescript
  - contracts
related_documents:
  - ../../governance/api-design-checklist.md
  - ../../patterns/api-patterns.md
---

# TypeScript Governance

# Purpose

Define standards for TypeScript type safety, domain contracts, API typing, runtime validation, shared contracts, and maintainable codebases.

# When To Use This Technology

Use TypeScript for JavaScript systems that need safer refactoring, API contracts, maintainable frontend/backend code, and AI-assisted development with stronger structural feedback.

# When NOT To Use This Technology

Do not treat TypeScript as a substitute for runtime validation, domain modeling, tests, or API compatibility governance.

# Recommended Architecture Patterns

| Pattern | Use When | Risk |
| --- | --- | --- |
| Strict domain types | Business rules matter. | Can drift without runtime validation. |
| DTO and domain separation | API shape differs from internal model. | Requires mapping discipline. |
| Shared contract package | Frontend and backend share stable API contracts. | Can become giant shared dependency. |
| Runtime schemas | External input crosses trust boundary. | Adds maintenance overhead. |

# Project Structure Guidance

- Keep API DTOs separate from domain models.
- Keep validation schemas near boundaries.
- Keep shared types small, versioned, and owned.
- Avoid cross-project type imports that create hidden coupling.

# Code Organization Standards

- Enable strict mode.
- Avoid `any` unless isolated and justified.
- Prefer explicit public API types.
- Use discriminated unions for expected variants.
- Keep generics understandable.

# API / Integration Guidance

- Validate external input at runtime.
- Type API responses and errors.
- Do not leak database models to APIs.
- Version shared contracts when compatibility matters.

# State Management Guidance

- Model state transitions explicitly.
- Use union types for loading, success, empty, and error states.
- Avoid nullable state spread across many fields.

# Error Handling Standards

- Define typed error categories where callers need behavior differences.
- Preserve original error details for logs.
- Avoid throwing strings or ambiguous objects.

# Security Guidance

- Treat type checks as compile-time only.
- Validate untrusted input.
- Avoid unsafe casting around auth, permissions, and sensitive data.

# Testing Expectations

- Test runtime validation.
- Test mappers between DTOs and domain models.
- Add contract tests for API types.
- Use type checks in CI.

# Observability Expectations

- Log validation failures safely.
- Include typed error categories in telemetry where useful.

# Performance Guidance

- Avoid type-level complexity that slows builds without meaningful safety.
- Keep generated types bounded and reviewed.

# Scalability Guidance

- Govern shared types in monorepos.
- Keep ownership clear for contract packages.
- Avoid giant shared type libraries across unrelated domains.

# Deployment & Operational Guidance

- Type safety must run in CI.
- Generated types must be reproducible.
- Runtime validation changes should be release-reviewed.

# Code Review Checklist

- [ ] Strict typing is preserved.
- [ ] No unjustified `any` or unsafe casts.
- [ ] DTOs do not leak persistence models.
- [ ] Runtime validation exists at trust boundaries.
- [ ] Shared types are small and owned.
- [ ] Error types are actionable.

# Common Anti-Patterns

- `any` everywhere.
- Unsafe casting.
- Giant shared types.
- Leaking DB models to APIs.
- Over-engineered generics.

# AI Coding Assistant Guardrails

- Do not silence type errors with casts.
- Generate runtime validation when handling external input.
- Keep generated types local unless a shared contract is explicitly requested.
- Explain any type compromise.

# Recommended Use Cases

- Frontend applications.
- Node.js services.
- Shared API contracts.
- Monorepos with typed packages.

# Example Architecture Patterns

```text
src/
  domain/
  api/
    dtos/
    schemas/
    mappers/
  shared/
    result.ts
    errors.ts
```

