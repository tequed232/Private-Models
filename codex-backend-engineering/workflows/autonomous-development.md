# Workflow — Autonomous, Multi-Session Backend Development

A persistent workflow for large features, migrations, and multi-stage refactors. It adapts Anthropic's initializer + coding-agent pattern and OpenAI's Codex iterative-development harness. It is a workflow design, not a requirement to create separate agents.

## 1. When to use

Use when:
- The task spans multiple modules or sessions.
- The work can be decomposed into independently verifiable features.
- Context may be lost between sessions.
- A migration or long-running refactor needs explicit progress tracking.

Do not use for trivial changes.

## 2. Suggested workspace

```text
repo/
├── AGENTS.md
├── GOALS.md
├── PLANS.md
├── PROMPTS.md
├── harness/
│   ├── build/
│   │   ├── phase-00-foundation.md
│   │   └── phase-01-feature.md
│   ├── context/
│   │   └── decisions.md
│   ├── code_review/
│   └── build-log.md
└── tests/
```

Adapt names and locations to existing repository conventions; do not create redundant documentation if equivalent files already exist.

## 3. Initializer phase

The initializer should not implement the whole product immediately.

1. Read the specification and repository.
2. Identify assumptions, constraints, integrations, and non-goals.
3. Break the work into small, ordered, testable milestones.
4. Define observable acceptance criteria for each milestone.
5. Map dependencies and identify high-risk decisions.
6. Create/update `GOALS.md`, `PLANS.md`, and phase checklists.
7. Add a verification strategy and known environment constraints.
8. Confirm the plan is coherent before starting high-risk implementation.

A useful milestone is independently testable and small enough to complete and verify in one focused work session.

## 4. Coding iteration

At the start of each session:

1. Read `AGENTS.md`, `GOALS.md`, `PLANS.md`, relevant phase notes, and `build-log.md`.
2. Inspect `git status` and recent commits.
3. Re-verify the current implementation; do not trust stale notes blindly.
4. Select the highest-priority uncompleted milestone whose dependencies are satisfied.
5. Implement only that milestone or a tightly related set.
6. Run focused tests and relevant broader checks.
7. Inspect the diff and fix regressions.
8. Update progress and decision records with evidence.
9. Leave the repository in a coherent state; avoid ending with large unverified changes.

## 5. Persistent progress format

For each milestone, record:
- Status: Todo / In Progress / Blocked / Done.
- Scope and acceptance criteria.
- Files/modules involved.
- Implementation notes.
- Tests/checks executed and results.
- Commit/branch reference if applicable.
- Risks, blockers, and next action.

Only mark Done when acceptance criteria are verified. Distinguish implementation complete from verification complete.

## 6. Test-first option

For behavior with clear expected inputs/outputs:
1. Write tests from the specification.
2. Run them and confirm they fail for the expected reason.
3. Review the tests for missing edge cases.
4. Implement without weakening the tests.
5. Run the tests until they pass.
6. Add integration/regression coverage where unit tests are insufficient.

Do not force TDD when the behavior is exploratory or lacks a stable specification; first clarify the contract.

## 7. Context reset / handoff

When starting a fresh session, explicitly instruct Codex to:
- Read the persistent plan and progress files.
- Inspect the actual repository state and Git history.
- Re-run a basic relevant check before continuing.
- Identify drift between notes and current code.
- Continue from the next verified milestone, not from assumptions.

Do not rely on chat history as the sole source of project state.

## 8. Completion gate

Before declaring the overall task complete:
- All acceptance criteria are satisfied.
- Required tests and builds are run.
- Migrations and rollout/rollback are reviewed.
- Security and authorization implications are reviewed.
- Documentation and operational configuration are updated.
- Final diff contains no unrelated changes.
- Remaining limitations are explicitly documented.

## 9. Example kickoff prompt

```text
Read the repository instructions and the product specification first.
Do not implement immediately. Inspect the codebase, identify the existing
architecture and constraints, then create a milestone-based implementation
plan with observable acceptance criteria and a verification strategy.

Persist the plan and progress in the repository so work can continue across
sessions. After the plan is ready, implement one milestone at a time.
For each milestone, add or update tests, run the relevant checks, inspect
the diff, and record actual results. Never mark a milestone complete without
verification. Preserve unrelated user changes and ask before destructive,
breaking, or externally visible actions.
```
