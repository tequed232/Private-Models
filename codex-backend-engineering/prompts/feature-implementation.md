# Prompt — Backend Feature Implementation

Copy this prompt into Codex and replace the bracketed sections.

---

You are acting as a senior backend engineer working inside an existing repository. Follow all applicable `AGENTS.md` instructions and the repository's established conventions.

## Objective

[Describe the behavior to implement and who/what consumes it.]

## Context

- Relevant modules/files: [known paths, or ask the agent to discover them]
- Runtime/framework: [if known]
- Data stores/integrations: [if known]
- Related issue/spec/API contract: [links or paths]

## Requirements

### Functional
- [Requirement 1]
- [Requirement 2]

### Non-functional
- Reliability: [expectations]
- Security/privacy: [expectations]
- Performance/scale: [workload or SLO, if known]
- Compatibility: [backward compatibility / migration constraints]

### Out of scope
- [Explicitly excluded behavior]

## Workflow

### Phase 1 — Investigate (do not edit yet)

1. Inspect repository instructions, docs, relevant code, tests, and Git status.
2. Trace the current request/data flow.
3. Identify existing patterns and integration boundaries.
4. List assumptions, ambiguities, dependencies, and risks.
5. Do not speculate about code you have not read.

Return a short findings summary with paths/symbols.

### Phase 2 — Design

Propose:
- Modules and responsibilities to change.
- API request/response/error contract.
- Validation and authorization rules.
- Database/schema/migration changes.
- Transaction, concurrency, retry, and idempotency behavior.
- Tests and verification commands.
- Rollout/compatibility concerns.

For a small and unambiguous task, keep this phase brief and proceed. For high-risk or breaking changes, stop for approval before implementation.

### Phase 3 — Implement

Implement the agreed behavior using existing conventions. Keep changes focused. Do not introduce dependencies, alter public contracts, or perform destructive operations without justification and authorization.

Add/update tests. Tests must validate the intended behavior, not merely mirror the implementation. Do not weaken or delete tests to obtain a green result.

### Phase 4 — Verify

Run the relevant formatter, linter, type checker, unit tests, integration/API tests, and build commands that exist in this repository.

For each check, report the exact command and outcome. If something cannot be run, state why. Fix failures caused by the change and rerun the relevant checks.

### Phase 5 — Final review

Inspect the complete diff. Check for:
- Missing validation/authentication/authorization.
- Data-integrity or migration hazards.
- Concurrency and partial-failure bugs.
- API compatibility issues.
- Secret or sensitive-data exposure.
- Unnecessary complexity or unrelated changes.

## Acceptance criteria

The task is complete only when:
- [Observable expected behavior]
- [Relevant authorization and validation behavior]
- [Data and compatibility requirements]
- [Required tests/checks]
- Documentation is updated where necessary.

## Final response format

1. **Implemented:** behavior and scope.
2. **Design:** important decisions and trade-offs.
3. **Changed files:** paths and purpose.
4. **Verification:** commands and actual results.
5. **Risks/limitations:** unresolved items, assumptions, and checks not run.

Do not claim completion or passing tests without evidence.
