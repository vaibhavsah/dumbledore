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
  - angular
  - frontend
related_documents:
  - ../../playbooks/frontend-platform-playbook.md
  - ../../governance/api-design-checklist.md
---

# Angular Governance

# Purpose

Define governance for scalable Angular applications with maintainable feature boundaries, disciplined dependency injection, controlled RxJS usage, and enterprise frontend operations.

# When To Use This Technology

Use Angular when teams need a structured frontend platform, strong conventions, enterprise maintainability, dependency injection, forms, routing, and a batteries-included ecosystem.

# When NOT To Use This Technology

Avoid Angular when the product needs a very small interactive surface, the team lacks Angular/RxJS capability, or framework weight is not justified.

# Recommended Architecture Patterns

| Pattern | Use When | Governance Need |
| --- | --- | --- |
| Feature-first modules/routes | Product areas map to routes or workflows. | Enforce boundaries. |
| Standalone components | Newer Angular apps need lighter composition. | Avoid dumping dependencies everywhere. |
| Lazy loading | Feature areas are independently entered. | Keep routes and ownership clear. |
| Facade services | Complex state or API coordination exists. | Prevent component bloat. |

# Project Structure Guidance

- Organize by feature and route boundary.
- Keep shared UI, shared utilities, and domain features separate.
- Avoid shared modules that become global dumping grounds.
- Keep API clients and DTO mapping outside templates.

# Code Organization Standards

- Keep templates declarative.
- Keep business logic out of templates.
- Use DI boundaries intentionally.
- Prefer composition over inheritance.
- Keep services cohesive and feature-owned.

# API / Integration Guidance

- Use typed clients and explicit DTOs.
- Keep transformation at feature API or facade boundaries.
- Centralize auth headers, retries, and error mapping.

# State Management Guidance

- Use local component state for local concerns.
- Use services/facades for feature state.
- Use heavier state libraries only when state transitions, debugging, or cross-feature behavior justify them.
- Avoid shared mutable state.

# Error Handling Standards

- Handle observable errors explicitly.
- Avoid swallowed subscription failures.
- Provide user-friendly messages and operational diagnostics.

# Security Guidance

- Do not expose secrets in environment files.
- Treat route guards as UX gates, not backend authorization.
- Sanitize dynamic HTML.
- Review role and permission assumptions.

# Testing Expectations

- Unit test services, pipes, validators, and complex components.
- Integration test feature flows with routing and API mocks.
- E2E test critical workflows.
- Include subscription and error-path tests.

# Observability Expectations

- Capture frontend exceptions and failed API calls.
- Track route-level failures and performance.
- Include correlation IDs when supported.

# Performance Guidance

- Use lazy loading for large feature areas.
- Manage change detection intentionally.
- Avoid expensive template expressions.
- Unsubscribe or use lifecycle-safe patterns.

# Scalability Guidance

- Scale with feature boundaries, lazy loading, and ownership.
- Keep shared libraries governed.
- Avoid god modules and monolithic services.

# Deployment & Operational Guidance

- Validate environment config.
- Use route smoke tests.
- Monitor error rate and failed API calls after deploy.

## Code Review Checklist

- [ ] Feature, route, component, service, facade, and shared-library boundaries are clear.
- [ ] Angular idioms are followed: DI is explicit, templates are declarative, and standalone/module patterns match the project.
- [ ] Business logic is not in templates or god services.
- [ ] RxJS streams have safe lifecycle management, error handling, and bounded subscriptions.
- [ ] API integration uses typed clients, DTO mapping, and consistent error handling.
- [ ] Security-sensitive checks are enforced on the backend, with route guards used only as UX controls.
- [ ] Tests cover services, validators, critical components, routing behavior, and observable error paths.
- [ ] Performance risks are checked: heavy template expressions, unnecessary change detection, missing lazy loading, and large bundles.
- [ ] Observability exists for route failures, frontend exceptions, and failed API calls.
- [ ] Maintainability is preserved through cohesive services and limited shared mutable state.
- [ ] AI-generated code is checked for fake Angular APIs, uncontrolled subscriptions, and project-inconsistent patterns.

## Code Review Red Flags

- Uncontrolled subscriptions or missing lifecycle-safe unsubscribe patterns.
- God services that own unrelated workflow, API, and state logic.
- Logic-heavy templates or expensive template expressions.
- Module, route, or shared-library boundary leaks.
- Shared mutable state across unrelated features.
- Excessive inheritance or framework magic hiding behavior.
- API calls directly from components when the project uses facades/services.
- Missing tests for observable error paths.

## AI Coding Assistant Review Guardrails

AI-generated Angular code must be reviewed for hallucinated Angular APIs, fake RxJS operators, uncontrolled subscriptions, inconsistent standalone/module patterns, over-abstracted services, missing tests, missing error handling, insecure route-guard assumptions, and architectural drift across feature boundaries.

# Common Anti-Patterns

- God modules.
- Shared mutable state.
- Excessive inheritance.
- Business logic in templates.
- Monolithic services.
- Uncontrolled subscriptions.

# AI Coding Assistant Guardrails

- Follow existing Angular version and standalone/module patterns.
- Do not create shared services for feature-specific logic.
- Include tests for services and critical components.
- Make RxJS error handling explicit.

# Recommended Use Cases

- Enterprise admin systems.
- Workflow-heavy dashboards.
- Teams that benefit from strict framework conventions.

# Example Architecture Patterns

```text
src/app/
  features/
    inventory/
      inventory.routes.ts
      pages/
      components/
      services/
      models/
  shared/
    ui/
    http/
```
