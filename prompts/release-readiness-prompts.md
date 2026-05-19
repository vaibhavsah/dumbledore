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
  - release_readiness
  - production
related_documents:
  - ../agents/release-readiness-agent.md
  - ../governance/production-readiness-checklist.md
---

# Release Readiness Prompts

## Production Readiness Review

When to use: before production release.

Expected output: readiness report and risks.

Decision criteria: no unresolved blockers in data safety, security, rollback, observability, or ownership.

```text
Perform a production readiness review for [feature/system].

Context:
[paste release notes, architecture, tests, deployment plan]

Return go/no-go recommendation, blockers, risks, monitoring gaps, rollback gaps, ownership gaps, and required actions.
```

## Go/No-Go Review

When to use: immediately before release decision.

Expected output: go, go with conditions, or no-go.

Decision criteria: acceptable residual risk with owners.

```text
Run a go/no-go review for [release].

Evaluate scope, test results, open defects, rollback, migrations, monitoring, security, support readiness, and business impact.
```

## Rollback Plan

When to use: before deployment.

Expected output: rollback checklist.

Decision criteria: rollback is tested or forward-fix path is explicit.

```text
Create a rollback plan for [release].

Include deployment rollback, database strategy, feature flags, data compatibility, verification steps, owner, and escalation path.
```

## Migration Readiness

When to use: any release with schema or data changes.

Expected output: migration risk assessment.

Decision criteria: no unsafe destructive migration without mitigation.

```text
Review migration readiness for [database change].

Assess compatibility, locks, data backfill, rollback/forward-fix, test evidence, monitoring, and release sequencing.
```

## Observability Readiness

When to use: before releasing new workflows or services.

Expected output: monitoring checklist and gaps.

Decision criteria: production failures can be detected and diagnosed.

```text
Review observability readiness for [feature/system].

Include logs, metrics, traces, dashboards, alerts, SLOs if relevant, ownership, and post-release validation.
```

## Security Readiness

When to use: before release involving auth, data, integrations, or permissions.

Expected output: security readiness report.

Decision criteria: no unresolved critical security risk.

```text
Review security readiness for [feature/system].

Assess auth, authorization, input validation, secrets, sensitive data, audit logs, dependency risk, and accepted exceptions.
```

## Performance Readiness

When to use: before high-volume or latency-sensitive release.

Expected output: performance risk assessment.

Decision criteria: expected load has validation or explicit risk acceptance.

```text
Review performance readiness for [feature/system].

Assess query paths, concurrency, latency, caching, background jobs, capacity, load test evidence, and monitoring.
```

## Incident Readiness

When to use: before production launch or high-risk release.

Expected output: incident readiness checklist.

Decision criteria: owner, runbook, alerts, and escalation path exist.

```text
Assess incident readiness for [feature/system].

Include runbook, alert owners, dashboards, escalation, known failure modes, customer impact, and mitigation steps.
```

## Post-Release Validation

When to use: after deployment.

Expected output: validation plan.

Decision criteria: release success can be verified objectively.

```text
Create a post-release validation plan for [release].

Include checks for health, logs, metrics, user journeys, error rates, data integrity, performance, and rollback trigger thresholds.
```

## Operational Handover

When to use: before support or operations teams take ownership.

Expected output: handover checklist.

Decision criteria: ownership and support model are explicit.

```text
Create an operational handover checklist for [system/feature].

Include owner, support process, runbook, dashboards, alerts, common issues, escalation, deployment process, and documentation links.
```

