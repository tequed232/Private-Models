# Prompt — Backend Architecture Review

Act as a principal backend engineer reviewing the architecture of this repository. Follow all repository instructions. This is an evidence-based review, not a request to rewrite the system.

## Goal

Assess [system/module/service] for correctness, modularity, maintainability, scalability, reliability, and operational complexity.

## Review process

1. Read project instructions, README, architecture docs, dependency manifests, deployment/CI configuration, and relevant source.
2. Map the actual runtime flow and module dependencies.
3. Identify architectural boundaries, shared state, persistence patterns, external integrations, and failure paths.
4. Trace representative critical workflows end to end.
5. Inspect tests to understand which guarantees are actually covered.
6. Do not infer runtime behavior solely from filenames or comments.

## Evaluate

- Separation of concerns and dependency direction.
- API and domain boundaries.
- Data ownership and consistency.
- Transaction boundaries and concurrency behavior.
- Authentication and authorization placement.
- Error propagation and failure isolation.
- External-service timeouts/retries/circuit breaking where relevant.
- Configuration and secret management.
- Observability and operational diagnostics.
- Testability and deployment/migration strategy.
- Performance hotspots supported by code or runtime evidence.

## Output

### 1. Executive summary
Overall assessment and the three highest-impact risks/opportunities.

### 2. Architecture map
Describe the verified request/data flow and key module responsibilities. Cite file paths and symbols.

### 3. Findings
For each finding include:
- Severity: Critical / High / Medium / Low / Informational.
- Evidence: file path, symbol, and relevant behavior.
- Impact and realistic failure scenario.
- Recommended remediation.
- Effort/risk estimate: Small / Medium / Large.

Do not label a concern as a confirmed vulnerability without sufficient evidence.

### 4. Targeted improvement plan
Group recommendations into:
- Immediate fixes.
- Incremental refactors.
- Longer-term architectural changes.

Prioritize by impact, risk reduction, and implementation cost.

### 5. Verification plan
Specify tests, telemetry, benchmarks, or deployment checks needed to validate each major recommendation.

## Constraints

- Do not modify files during the review unless explicitly asked.
- Do not recommend a rewrite merely because another architecture is fashionable.
- Preserve working conventions unless evidence shows they cause material problems.
- Separate verified facts from assumptions and questions.
