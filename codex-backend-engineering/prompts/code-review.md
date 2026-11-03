# Prompt — Backend Pull Request / Diff Review

Review the current branch diff against [base branch/commit]. Act as a senior backend reviewer. Prioritize defects over style preferences.

## Review instructions

1. Inspect Git status and the exact diff, including surrounding code.
2. Read relevant call sites, data models, API contracts, tests, and repository instructions.
3. Trace changed behavior through authorization, persistence, and failure handling.
4. Look for regressions, edge cases, concurrency problems, and compatibility risks.
5. Verify tests are meaningful and not weakened to match faulty behavior.
6. Do not modify files unless explicitly requested.

## Review priorities

- Incorrect behavior or broken invariants.
- Authentication/authorization flaws and tenant isolation.
- Data loss, corruption, migration, or transaction defects.
- Race conditions, duplicate side effects, and idempotency gaps.
- Missing validation and unsafe trust-boundary handling.
- Error handling, retries, timeouts, and partial failures.
- API/schema backward compatibility.
- Performance regressions supported by evidence.
- Missing or inadequate tests.
- Maintainability issues only when they create concrete risk.

## Finding format

Each finding must include:
- Severity: P0 / P1 / P2 / P3.
- File path and line range in the changed diff where possible.
- Specific failure scenario.
- Why the current code causes it.
- Suggested fix.
- Test that would catch it.

Do not report:
- Pure style preferences as bugs.
- Hypothetical risks without a plausible path.
- Issues unrelated to the diff unless they block correctness.
- Duplicate findings for the same root cause.

## Output

Start with findings, highest severity first. If no findings are identified, state that no actionable defects were found in the reviewed scope and list important areas that were not verified. Summarize test coverage and checks actually run. Never imply a full security audit from a routine diff review.
