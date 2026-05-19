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
  - technology_governance
related_documents:
  - ../agents/code-review-agent.md
  - ../technology-guides/README.md
  - ../governance/architecture-review-process.md
  - ../governance/security-review-checklist.md
  - ../governance/api-design-checklist.md
  - ../governance/observability-checklist.md
---

# Code Review Prompts

These prompts execute the Dumbledore Code Review Agent workflow. Every review must include project context, PR/change summary, changed files, detected technologies, relevant Dumbledore docs, relevant technology guides, severity classification, and patch recommendations.

## Expected Review Output Format

Use this structure unless a project-specific review format already exists:

# Code Review Report

## 1. Review Context

- Change summary.
- Detected technologies.
- Review sources applied.
- Assumptions.

## 2. Executive Summary

- Overall recommendation: Approve / Approve with comments / Request changes.
- Risk level: Low / Medium / High.
- Key concerns.

## 3. Blocking Issues

| Issue | Severity | Location | Why It Matters | Recommended Fix | Source |
| --- | --- | --- | --- | --- | --- |

## 4. Major Issues

Use the same table.

## 5. Minor Issues

Use the same table.

## 6. Technology-Specific Findings

Group by detected technology.

## 7. Architecture Boundary Findings

## 8. Security Findings

## 9. API / Contract Findings

## 10. Data / Migration Findings

## 11. Observability & Operational Findings

## 12. Testing Gaps

## 13. Suggested Patch Plan

## 14. Final Merge Recommendation

Severity classification: Blocker, Major, Minor, Suggestion.

## Full PR Review Using Dumbledore

When to use: for any PR that changes production code, tests, infrastructure, schemas, or contracts.

Expected output: full Code Review Report with final merge recommendation.

```text
Review this PR as the Dumbledore Code Review Agent.

Project context:
[paste project goal, architecture summary, repo conventions, relevant HLD/LLD/ADR links]

PR/change summary:
[paste PR description and intended behavior]

Changed files:
[paste file list]

Diff or relevant code:
[paste diff or file excerpts]

Instructions:
1. Infer the detected technologies from files, folders, dependencies, imports, and PR context.
2. Select the relevant Dumbledore governance documents and technology guides.
3. Apply architecture, security, API, observability, database, infra, pattern, and anti-pattern guidance as applicable.
4. Classify every finding as Blocker, Major, Minor, or Suggestion.
5. Cite the source for each material finding.
6. Produce the full Code Review Report format.
7. End with Approve, Approve with comments, or Request changes.
```

## Technology-Specific Code Review

When to use: when a review needs deep stack-specific scrutiny.

Expected output: technology-specific findings plus merge recommendation.

```text
Review this change using Dumbledore technology governance.

Technology:
[React / Angular / TypeScript / Java / Node.js / Go / Python / REST / GraphQL / Middleware]

Relevant guide path:
[paste path, for example technology-guides/frontend/react-governance.md]

Project context:
[paste HLD/LLD/ADR/task context]

PR/change summary:
[paste summary]

Changed files:
[paste files]

Code:
[paste diff or excerpts]

Review focus:
- stack idioms
- folder/module boundaries
- error handling
- security
- testing
- performance
- observability
- maintainability
- stack-specific anti-patterns

Use the standard Code Review Report output and severity classification.
```

## General PR Review

When to use: lightweight review for low-risk changes.

Expected output: review findings with source-aware severity.

```text
Review this PR using Dumbledore governance.

Project context:
[paste context]

PR/change summary:
[paste summary]

Changed files:
[paste files]

Detected technologies:
[paste or ask the agent to infer]

Relevant Dumbledore docs:
[paste links or excerpts]

Relevant technology guides:
[paste links or excerpts]

Diff:
[paste diff]

Classify findings by severity and include a patch recommendation.
```

## Architecture Boundary Review

When to use: when a change touches modules, services, domain logic, shared packages, or integration boundaries.

Expected output: boundary violations, risks, and patch plan.

```text
Review this change for architecture boundary violations.

Project context:
[paste HLD/LLD/ADRs]

PR/change summary:
[paste summary]

Changed files:
[paste files]

Detected technologies and relevant guides:
[paste or infer]

Diff:
[paste diff]

Identify domain leakage, wrong-layer logic, hidden coupling, framework-specific boundary violations, and architecture drift. Cite the applicable Dumbledore sources and recommend the smallest safe fix.
```

## Backend Code Review

When to use: backend feature, service, worker, or persistence changes.

Expected output: backend correctness, boundary, security, and operational findings.

```text
Review this backend change using relevant backend technology guides.

Project context:
[paste architecture/task context]

PR/change summary:
[paste summary]

Changed files:
[paste files]

Detected backend stack:
[Java / Node.js / Go / Python / other]

Relevant guides:
[java-governance.md / nodejs-governance.md / golang-governance.md / python-governance.md plus API/DB/middleware guides if applicable]

Focus on domain logic, validation, authorization, transactions, data access, async behavior, error handling, observability, tests, performance, and operational risk.
```

## Frontend Code Review

When to use: UI, state management, routing, API integration, or component changes.

Expected output: frontend architecture, accessibility, state, integration, and testing findings.

```text
Review this frontend change using relevant frontend technology guides.

Project context:
[paste architecture/task context]

PR/change summary:
[paste summary]

Changed files:
[paste files]

Detected frontend stack:
[React / Angular / TypeScript / other]

Relevant guides:
[react-governance.md / angular-governance.md / typescript-governance.md]

Focus on component/module boundaries, state ownership, API integration, loading/empty/error states, accessibility, performance, tests, and framework anti-patterns.
```

## API Contract Review

When to use: REST, GraphQL, schema, DTO, or external contract changes.

Expected output: compatibility and contract safety findings.

```text
Review this API contract change.

Project context:
[paste HLD/ADR/API standards]

PR/change summary:
[paste summary]

Changed files:
[paste files]

Detected API style:
[REST / GraphQL / other]

Relevant Dumbledore docs:
- governance/api-design-checklist.md
- technology-guides/api/rest-governance.md or technology-guides/api/graphql-governance.md

Focus on compatibility, request/response schema, validation, errors, auth, idempotency, versioning, observability, contract tests, and client impact.
```

## DB Migration Review

When to use: schema, migration, query, index, or data backfill changes.

Expected output: data safety, compatibility, and rollback findings.

```text
Review this DB migration or data change.

Project context:
[paste data ownership, ADRs, release plan]

PR/change summary:
[paste summary]

Changed files:
[paste migration/query/model files]

Relevant Dumbledore docs:
- governance/db-strategy-checklist.md
- relevant backend technology guide

Focus on data safety, backward compatibility, indexes, locks, rollback/forward-fix strategy, backfills, transactions, test coverage, and runtime impact.
```

## Security Code Review

When to use: auth, permissions, secrets, sensitive data, dependency, or integration changes.

Expected output: security findings and mitigations.

```text
Review this change for security risks.

Project context:
[paste auth/security model, ADRs, data sensitivity]

PR/change summary:
[paste summary]

Changed files:
[paste files]

Detected technologies:
[paste or infer]

Relevant docs:
- governance/security-review-checklist.md
- relevant technology guides

Focus on authentication, authorization, tenant isolation, input validation, secrets, sensitive data exposure, audit logs, dependency risk, and trust boundaries.
```

## Performance Review

When to use: query-heavy, high-traffic, frontend rendering, batch, worker, or latency-sensitive code.

Expected output: performance risks and validation plan.

```text
Review this change for performance risk.

Project context:
[paste scale expectations and SLOs if any]

PR/change summary:
[paste summary]

Changed files:
[paste files]

Detected technologies and guides:
[paste or infer]

Focus on query behavior, rendering cost, N+1 risks, caching, memory usage, concurrency, external calls, latency, backpressure, and load test needs.
```

## Maintainability Review

When to use: complex, shared, or fast-moving areas.

Expected output: maintainability risks and simplification suggestions.

```text
Review this change for maintainability.

Project context:
[paste architecture and ownership context]

PR/change summary:
[paste summary]

Changed files:
[paste files]

Relevant technology guides:
[paste or infer]

Focus on readability, unnecessary abstraction, duplication, module boundaries, naming, testability, framework idioms, and future change cost.
```

## AI-Generated Code Review

When to use: reviewing code produced by ChatGPT, Codex, Cursor, Claude, Windsurf, or another AI assistant.

Expected output: stricter review for hallucination, unsafe shortcuts, and drift.

```text
Review this AI-generated code using the Dumbledore Code Review Agent.

Project context:
[paste architecture, ADRs, repo conventions]

AI task prompt:
[paste original implementation prompt if available]

PR/change summary:
[paste summary]

Changed files:
[paste files]

Detected technologies:
[paste or infer]

Relevant Dumbledore docs and technology guides:
[paste or infer]

Be stricter than a normal review. Check for:
- hallucinated APIs
- fake library methods
- unnecessary abstractions
- missing edge cases
- hidden security risks
- inconsistent project patterns
- untested logic
- missing failure handling
- architectural drift

Produce the full Code Review Report and final merge recommendation.
```

## Patch Plan Prompt

When to use: after review findings are known and the team needs an implementation plan.

Expected output: smallest safe patch plan with tests and validation.

```text
Convert these review findings into a patch plan.

Project context:
[paste context]

Review findings:
[paste blockers, major issues, minor issues]

Changed files:
[paste files]

Constraints:
- keep the patch small and reviewable
- preserve architecture boundaries
- fix blockers before improvements
- add or update tests
- avoid broad rewrites

Produce:
- ordered patch steps
- file-by-file changes
- tests to add or update
- validation commands
- rollback considerations
- residual risks
```
