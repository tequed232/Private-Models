---
name: backend-engineering
description: Investigate, design, implement, test, and review backend features and services. Use for API endpoints, business logic, database changes, authentication/authorization, integrations, reliability, security, performance, and backend refactoring.
---

# Backend Engineering Skill

Use this workflow for backend tasks. Adapt depth to risk and scope; do not turn a one-line fix into a heavyweight process.

## Step 1 — Classify the task

Identify:
- User-visible behavior and acceptance criteria.
- Affected service boundaries and data flows.
- Data sensitivity and security impact.
- Compatibility and migration risk.
- Operational/performance requirements.
- Whether the task is small, medium, or cross-cutting.

If a critical requirement is ambiguous and cannot be safely inferred, ask one focused question. Otherwise state assumptions and proceed.

## Step 2 — Investigate the repository

1. Read applicable instructions and project docs.
2. Inspect the Git working tree; preserve pre-existing modifications.
3. Find the entry points and trace relevant call paths.
4. Inspect data models, migrations, API schemas, configuration, and tests.
5. Identify established patterns, dependencies, and runtime constraints.
6. Record findings with file paths and symbols, not vague descriptions.

Do not invent files, commands, frameworks, or architecture that have not been confirmed.

## Step 3 — Design before editing

For non-trivial work, produce a concise implementation plan covering:
- Proposed behavior and module boundaries.
- API contract and validation.
- Data model and migration strategy.
- Authorization and threat considerations.
- Transaction, retry, and failure semantics.
- Test matrix and acceptance evidence.
- Rollout, compatibility, and rollback considerations.

Prefer the smallest design that satisfies requirements and fits the existing codebase.

## Step 4 — Implement incrementally

- Make focused changes in coherent steps.
- Keep transport, business logic, and persistence responsibilities aligned with the repository.
- Validate at trust boundaries.
- Enforce authorization at the resource/action boundary, not merely in the UI.
- Preserve data integrity with constraints and transactions.
- Handle errors explicitly; do not hide failures.
- Avoid unnecessary dependencies and speculative abstractions.
- Update migrations, docs, and examples as required.

For test-driven tasks, write tests from the specification first, confirm they fail for the expected reason, then implement without weakening those tests.

## Step 5 — Verify

Run checks in increasing scope:
1. Formatting/lint/type checks for touched modules.
2. Focused unit tests.
3. Relevant integration and API tests.
4. Broader regression suite/build when feasible.
5. Manual verification or benchmark for requirements not covered by automated tests.

For each command, capture the actual result. If a check cannot run, explain the blocker and provide the next-best evidence. Do not fabricate passing results.

## Step 6 — Review the diff

Inspect the final diff for:
- Unintended files or unrelated edits.
- Missing validation or authorization.
- Race conditions, transaction gaps, and partial failure.
- Data migration and rollback hazards.
- Leaked secrets or sensitive logging.
- API compatibility and documentation gaps.
- Dead code, duplicated logic, and unnecessary complexity.

Fix issues found, then rerun relevant checks.

## Step 7 — Report

Provide a concise report with:
- Implemented behavior.
- Key files changed.
- Design decisions and assumptions.
- Verification commands and exact outcomes.
- Known limitations and residual risks.

## Backend-specific review checklist

### API
- Contract is explicit and stable.
- Inputs are validated; outputs do not leak internal data.
- Pagination and idempotency are considered where needed.
- Errors and status codes are consistent.

### Authorization
- Every protected operation checks the authenticated principal.
- Object ownership/tenant boundaries are enforced server-side.
- Negative authorization tests exist for sensitive operations.

### Database
- Constraints and indexes reflect invariants and query patterns.
- Transactions cover atomic business operations.
- Concurrent updates and duplicate requests are safe.
- Migrations are deployable and data-preserving.

### Operations
- Timeouts, retries, resource cleanup, and observability are appropriate.
- Failure modes are explicit and recoverable.
- Resource consumption is bounded.
