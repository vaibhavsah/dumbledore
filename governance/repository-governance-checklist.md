---
document_type: checklist
scope: reusable
audience:
  - engineering_managers
  - solution_architects
  - principal_engineers
  - technical_leads
  - ai_agents
status: draft
review_cycle: quarterly
tags:
  - repository_governance
  - branch_protection
  - ownership
  - pull_requests
related_documents:
  - ../agents/development-agent.md
  - ../prompts/project-kickoff-prompts.md
  - ../governance/architecture-review-process.md
---

# Repository Governance Checklist

Use this checklist before creating a repository, modifying an existing repository's initial setup, or asking an AI development agent to push implementation work.

## Branch Safety

- [ ] Do not commit implementation, scaffolding, generated code, or governance changes directly to `main`.
- [ ] If the current checkout is on `main`, first update `main` from the remote default branch before creating a feature branch.
- [ ] Create a separate working branch when the user has not explicitly provided one.
- [ ] Use a short, descriptive branch name that identifies the task or repo setup.
- [ ] Push work to the working branch, not to `main`.
- [ ] Open a pull request for review before merging into `main`.

## Main Branch Protection

Every new repository must protect `main` before normal development begins.

- [ ] Require a pull request before merging into `main`.
- [ ] Require at least one approving review before merge.
- [ ] Require CODEOWNERS review when the repository has a `CODEOWNERS` file.
- [ ] Prevent direct pushes to `main` for regular contributors and automation.
- [ ] Keep branch protection enabled before handing the repository to implementation agents.

## Ownership

- [ ] Add a repository-level `CODEOWNERS` file during initial setup.
- [ ] Set default ownership to `@vaibhavsah` unless the user explicitly provides a different GitHub owner.
- [ ] Place `CODEOWNERS` under `.github/CODEOWNERS` unless the target repository already follows another supported GitHub location.
- [ ] Start from `templates/CODEOWNERS-template` when bootstrapping a repository from Dumbledore guidance.
- [ ] Keep ownership rules broad at repository creation, then refine by folder as teams and modules become clear.

## Existing Repository Updates

- [ ] Inspect the current branch before making changes.
- [ ] If on `main`, update `main`, create a working branch, and continue there.
- [ ] If already on a working branch, confirm it tracks the intended remote branch before pushing.
- [ ] Add or repair branch protection and `CODEOWNERS` before adding product implementation changes.
- [ ] Keep repository governance changes reviewable and separate from large product changes when possible.

## Agent Handoff Prompt

```text
Before changing code, inspect the current git branch. Do not commit or push directly to main.

If you are on main, update main from origin, create a separate working branch unless I provide one, and push all work to that branch.

For any new repository, protect main so merging requires a pull request, add .github/CODEOWNERS with @vaibhavsah as the default owner, and verify repository governance before implementation begins.
```
