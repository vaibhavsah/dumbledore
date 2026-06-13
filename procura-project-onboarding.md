# Procura Project Onboarding Brief

Last updated: 2026-05-21

## Purpose

This brief helps a new teammate understand the current Procura repository layout, local setup, run commands, and immediate development path. The codebase is still early scaffold stage, so `procura-docs` is the main source of product and architecture context.

## Repository Map

| Repo | Scope | Tech | Run Command |
| --- | --- | --- | --- |
| `procura-web` | Procura ERP web application | React 18, TypeScript, Vite, Vitest | `npm run dev` |
| `procura-docs` | Product, architecture, planning, ADRs, and documentation system of record | Markdown docs and templates | No app runtime |
| `procura-core-service` | Core ERP backend workflows | Java 21, Spring Boot 3.3, REST, PostgreSQL | `mvn spring-boot:run` |
| `procura-rbac-service` | Role and permission metadata service | Java 21, Spring Boot 3.3, REST, PostgreSQL | `mvn spring-boot:run` |
| `procura-identity-service` | Identity, authentication, JWT, refresh token lifecycle | Java 21, Spring Boot 3.3, REST, PostgreSQL | `mvn spring-boot:run` |

## High-Level Architecture

Procura starts as a small ERP MVP with separate IAM services and a core ERP service:

- `procura-web` owns browser UI, routing, client-side API integration, session handling, accessibility, and frontend state.
- `procura-core-service` owns auction, vendor, stock, warehouse-lite, audit, and reporting business workflows.
- `procura-identity-service` owns users, login, JWT issuance, refresh tokens, JWKS/public key exposure, and token revocation/versioning.
- `procura-rbac-service` owns roles, permissions, permission groups, role assignments, and tenant-scoped authorization metadata.
- `procura-docs` owns the source-of-truth product, architecture, workflow, and decision documents.

Keep domain rules on the backend. Keep identity and RBAC concerns separate. Do not add GraphQL, BFF, Kafka, Kubernetes, or service splits unless the docs/ADRs explicitly approve them.

## Clone And Setup

Clone all repos under one parent folder:

```sh
mkdir -p ~/git
cd ~/git

git clone git@github.com:erp-private/procura-docs.git
git clone git@github.com:erp-private/procura-web.git
git clone git@github.com:erp-private/procura-core-service.git
git clone git@github.com:erp-private/procura-rbac-service.git
git clone git@github.com:erp-private/procura-identity-service.git
```

Required local tools:

- Node.js 20+ and npm for `procura-web`.
- Java 21 and Maven for the backend services.
- PostgreSQL 16 for backend service persistence.
- GitHub SSH access to `erp-private`.

## Run Locally

### Frontend

```sh
cd ~/git/procura-web
npm install
npm run dev
```

Useful checks:

```sh
npm run build
npm run test
npm run lint
```

### Core Service

Default port: `8080`

Default database env:

```sh
PROCURA_CORE_DB_URL=jdbc:postgresql://localhost:5432/procura_core
PROCURA_CORE_DB_USER=procura
PROCURA_CORE_DB_PASSWORD=procura
```

Run:

```sh
cd ~/git/procura-core-service
mvn spring-boot:run
```

### Identity Service

Default port: `8081`

Default database env:

```sh
PROCURA_IDENTITY_DB_URL=jdbc:postgresql://localhost:5432/procura_identity
PROCURA_IDENTITY_DB_USER=procura
PROCURA_IDENTITY_DB_PASSWORD=procura
```

Run:

```sh
cd ~/git/procura-identity-service
mvn spring-boot:run
```

### RBAC Service

Default port: `8082`

Default database env:

```sh
PROCURA_RBAC_DB_URL=jdbc:postgresql://localhost:5432/procura_rbac
PROCURA_RBAC_DB_USER=procura
PROCURA_RBAC_DB_PASSWORD=procura
```

Run:

```sh
cd ~/git/procura-rbac-service
mvn spring-boot:run
```

## Current Structure

### `procura-web`

Important paths:

- `src/app/` - React app entry, root component, global styles.
- `src/features/` - planned feature areas: auction, auth, reporting, stock, vendor, warehouse.
- `src/shared/` - planned shared API clients, components, hooks, types, and utilities.
- `docs/` - frontend architecture, local development, testing, release, API integration, accessibility.

### `procura-docs`

Important paths:

- `docs/index.md` - start here.
- `docs/business/` - product overview, scope, personas, workflows, requirements, risks.
- `docs/architecture/` - system context, HLDs, LLDs, database strategy, module architecture.
- `docs/decisions/` - ADRs.
- `docs/planning/` - build plans, repo strategy, docs gate checklist.
- `templates/` - reusable documentation templates.
- `.ai/` - optional AI authoring guidance and prompts.

### Backend Services

Each service currently has a minimal Spring Boot scaffold:

- `src/main/java/.../*Application.java` - Spring Boot entrypoint.
- `src/main/resources/application.yml` - app name, datasource defaults, actuator exposure, port.
- `src/test/java/.../*ApplicationTests.java` - initial application context test.
- `docs/` - local service notes, testing, release, architecture links, and service-specific boundaries.
- `.github/CODEOWNERS` - repository ownership.

## Development Workflow

1. Start from `procura-docs/docs/index.md`.
2. Read the relevant HLD, LLD, ADR, and build plan before changing code.
3. Create a branch from updated `main`.
4. Keep changes focused to one repo and one feature slice where possible.
5. Link implementation PRs back to relevant docs.
6. Update docs in the same PR or a paired docs PR when behavior, APIs, storage, or decisions change.
7. Run local tests/builds before raising a PR.

Branch rule:

- Do not commit directly to `main`.
- Use a feature branch.
- Open a PR into `main`.
- `CODEOWNERS` is set to `@vaibhavsah`.

Suggested branch names:

```sh
feature/identity-login-api
feature/rbac-permission-model
feature/core-auction-draft
feature/web-auth-shell
docs/auction-workflow-update
```

## Immediate Next Steps

1. Confirm local access to all five repos and pull latest `main`.
2. Run `procura-web` with `npm run dev`.
3. Run each backend service with Maven and confirm `/actuator/health`.
4. Create or confirm local PostgreSQL databases:
   - `procura_core`
   - `procura_identity`
   - `procura_rbac`
5. Read these docs first:
   - `procura-docs/docs/index.md`
   - `procura-docs/docs/planning/repo-usage-and-development-strategy.md`
   - `procura-docs/docs/planning/iam-build-plan-0-0.md`
   - `procura-docs/docs/architecture/hld/identity-and-access-0-0.md`
   - `procura-docs/docs/architecture/hld/auction-platform-0-0.md`
6. Pick the first small vertical slice. Recommended starting areas:
   - identity health/config baseline and login API skeleton
   - RBAC role/permission model skeleton
   - core auction draft domain skeleton
   - web auth/session shell and API client foundation
7. For any unclear behavior, update `procura-docs` before locking implementation.

## Notes For The New Teammate

The current repos are intentionally lightweight scaffolds. Do not assume missing code means architecture is undecided. Check `procura-docs` first, then implement the smallest reviewable slice. If a code change affects architecture, APIs, storage, security, RBAC, audit, or workflows, update or reference the relevant docs and ADRs.
