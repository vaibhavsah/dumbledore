---
document_type: playbook
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
  - architecture_governance
  - knowledge_base
  - ai_agents
related_documents:
  - principles/architecture-principles.md
  - governance/architecture-review-process.md
  - templates/hld-template.md
  - templates/lld-template.md
  - templates/adr-template.md
---

# Dumbledore

Dumbledore is a reusable architecture governance knowledge base for 0-to-1 products, SaaS platforms, frontend-heavy systems, AI and agentic systems, event-driven systems, scalable APIs, and modern cloud/platform engineering. It acts as architecture Confluence, governance memory, and AI-agent retrieval source for repeatable technical decision-making.

This repository is not project-specific. It defines principles, templates, checklists, patterns, anti-patterns, playbooks, and examples that project repositories can reference or copy from. Project-specific HLDs, LLDs, ADRs, incidents, requirements, and implementation decisions should live in their own repositories.

## Core Philosophy

- Prefer simple, evolvable architecture over premature complexity.
- Prefer modular monoliths before microservices unless domain boundaries, team topology, deployment independence, or scale clearly justify distribution.
- Stay technology-agnostic unless explaining trade-offs.
- Always explain trade-offs, risks, alternatives, and decision rationale.
- Separate MVP architecture from scale-stage architecture.
- Optimize for maintainability, developer productivity, operational excellence, cost-awareness, and security.
- Make documents useful to both humans and AI agents through consistent metadata, headings, checklists, and examples.

## Decision Independence Policy

Dumbledore acts as an architecture governance authority, not a confirmation engine. User preference is input, not decision. It treats proposed technologies, architecture styles, repository structures, infrastructure choices, and implementation preferences as context to evaluate, not instructions to accept.

Dumbledore should acknowledge proposed choices, compare reasonable alternatives, state trade-offs, challenge weak assumptions, reject overengineering, reject underengineering, and recommend the option with the strongest rationale. It should remain professional, direct, evidence-led, and governance-oriented.

## Technology Decision Evaluation Framework

| Dimension | Questions |
|---|---|
| Product Fit | Does this solve the actual product need? |
| Team Fit | Can the team build and operate it? |
| Complexity | Does it add unnecessary moving parts? |
| Maintainability | Will this be understandable in 12 months? |
| Scalability | Does it match realistic load expectations? |
| Security | Does it support secure defaults? |
| Operations | Can it be deployed, monitored, debugged, and rolled back? |
| Cost | What is the infra, licensing, and engineering cost? |
| Ecosystem | Is the ecosystem mature and supportable? |
| Evolution | Can we migrate away or evolve later? |

## Recommendation Format

For every major recommendation, Dumbledore should output:

1. User Preference
2. Dumbledore Assessment
3. Alternatives Considered
4. Trade-off Table
5. Decision
6. Why This Decision
7. What Would Change This Decision Later
8. Risks
9. ADR Required: Yes/No


## Repository Map

| Area | Purpose |
| --- | --- |
| `principles/` | Durable engineering and architecture beliefs used to evaluate decisions. |
| `templates/` | Reusable document structures for HLDs, LLDs, ADRs, RFCs, and incident reviews. |
| `governance/` | Review processes and checklists for APIs, security, observability, infrastructure, data, scale, and production readiness. |
| `playbooks/` | Practical guidance for common architecture domains and evolution paths. |
| `patterns/` | Reusable solution patterns with applicability, trade-offs, and review prompts. |
| `anti-patterns/` | Common failure modes to detect early in design and review. |
| `decisions/adr/` | ADRs for decisions about Dumbledore itself only. |
| `examples/` | Sample reusable documents demonstrating expected quality and structure. |

## Day-To-Day Usage

1. Start with principles to frame the decision.
2. Pick the smallest fitting template: HLD for system shape, LLD for implementation design, ADR for a decision, RFC for broader change discussion.
3. Run the relevant governance checklist before implementation begins.
4. Use playbooks and patterns to compare known options.
5. Record decision rationale in the project repo, not here.
6. Feed lessons learned back into Dumbledore only when they are reusable beyond a single project.

## Using Dumbledore With AI Tools

AI agents should treat this repository as a governance source, not as an implementation plan. When using it with ChatGPT, Codex, Copilot, Cursor, or another assistant:

- Retrieve the relevant principle, playbook, template, checklist, pattern, and anti-pattern files.
- Ask the agent to cite which governance documents shaped the output.
- Require the agent to separate assumptions from facts.
- Require MVP and scale-stage recommendations to be different sections.
- Require trade-offs, alternatives, risks, and open questions.
- Require the agent to challenge assumptions and avoid confirming preferred choices without evidence.
- Require major recommendations to separate user preference, architectural evidence, decision rationale, and unresolved risks.
- Require the agent to apply `governance/repository-governance-checklist.md` before creating repositories, updating repository setup, committing work, or pushing branches.
- Store project-specific outputs in the project repository.

Suggested prompt:

```text
Use Dumbledore as the architecture governance source. Create a project-specific HLD for <system>. Apply the architecture principles, SaaS playbook, API checklist, observability checklist, security checklist, and relevant anti-patterns. Do not simply follow my preferred choices. Challenge my assumptions. Compare alternatives. Recommend based on rationale, not preference. Keep technology choices as options unless already decided. Store the final document in this project repo, not in Dumbledore.
```

## Creating HLDs, LLDs, ADRs, And Reviews

- HLDs: start from `templates/hld-template.md`, then validate with `governance/architecture-review-process.md`, `governance/security-review-checklist.md`, and `governance/observability-checklist.md`.
- LLDs: start from `templates/lld-template.md`, then validate APIs, data model, failure modes, and testability.
- ADRs: start from `templates/adr-template.md` and capture one decision per ADR. Do not bury decisions inside HLD prose.
- Reviews: use the focused checklist that matches the risk area, then summarize findings by severity, owner, and required action.
- Repository setup: apply `governance/repository-governance-checklist.md` before creating new repositories or updating existing repository governance, and use `templates/CODEOWNERS-template` for default ownership.

## How Project Repositories Reference This Repo

Project repositories may:

- Link to Dumbledore documents from their own `docs/` navigation.
- Copy templates into their own repo and customize them.
- Record ADRs, review findings, diagrams, and implementation constraints locally.
- Pin a Dumbledore commit SHA when strict reproducibility is needed.

Project repositories should not:

- Store project-specific decisions here.
- Modify Dumbledore to justify a one-off project shortcut.
- Treat examples as production-ready designs without review.

## Governance Evolution

Dumbledore evolves quarterly or when a reusable lesson emerges from real delivery. Changes should be proposed through an RFC or ADR when they alter governance policy, decision criteria, or document structure. Small clarifications can be committed directly with clear rationale.

Useful change triggers:

- A repeated architecture review finding appears across projects.
- A checklist misses a material risk.
- A new delivery pattern becomes common enough to standardize.
- An anti-pattern causes measurable rework, incident risk, or cost growth.

## What Belongs Here

- Reusable principles and review criteria.
- Templates and example document shapes.
- Technology-agnostic decision frameworks.
- Patterns, anti-patterns, and playbooks that apply across products.
- ADRs about Dumbledore governance itself.

## What Does Not Belong Here

- Product-specific HLDs, LLDs, ADRs, or incident reviews.
- Vendor-specific implementation manuals unless framed as trade-off examples.
- Secrets, customer data, environment details, or internal credentials.
- Agent code, skills, automations, or runtime tooling. Those remain separate for now.
