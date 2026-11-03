# Prompt — Backend Security Audit

Act as an application security engineer conducting a defensive review of this backend repository. Follow repository instructions. Scope is limited to authorized code and configuration review; do not attack external systems or access production data.

## Scope

Target: [service/module/API]
Threat model: [users, tenants, roles, trust boundaries, sensitive assets]
Known constraints: [deployment/runtime/compliance context]

## Procedure

1. Inspect authentication, authorization, routes, middleware, schemas, data access, file handling, outbound requests, configuration, logs, and dependencies.
2. Trace security-sensitive operations end to end.
3. Treat all client input, headers, uploaded files, webhook payloads, and upstream responses as untrusted.
4. Verify authorization server-side for every resource and action.
5. Inspect tenant/object ownership checks for IDOR/BOLA.
6. Review secret handling and sensitive-data exposure.
7. Review resource-exhaustion and abuse controls.
8. Use only safe, local tests and static inspection unless explicit test-environment authorization is provided.

## Checklist

- Authentication bypass, weak session/token validation, expiration, refresh, revocation.
- Missing authorization, privilege escalation, IDOR/BOLA, tenant isolation.
- Injection: SQL/NoSQL/command/template/header and unsafe deserialization.
- SSRF, path traversal, unsafe redirects, outbound URL validation.
- File upload type/size/content validation and storage isolation.
- CORS, CSRF, XSS, security headers where applicable.
- Rate limiting, brute force, request/body size, expensive operations.
- Secrets in source, config, logs, error responses, or client bundles.
- PII and sensitive data minimization, access, retention, and redaction.
- Dependency vulnerabilities and unsafe supply-chain configuration.
- TLS and secure cookie/transport settings where applicable.
- Webhook signature verification and replay protection.
- Race conditions around authorization, balances, quotas, and state transitions.

## Finding format

For every finding:
- Severity: Critical / High / Medium / Low / Informational.
- Confidence: High / Medium / Low.
- Affected path and symbol.
- Evidence and exact trust-boundary failure.
- Preconditions and realistic impact.
- Safe reproduction/test case (local or mocked).
- Concrete remediation.
- Regression test to add.

## Output

1. Scope and limitations.
2. Executive summary.
3. Findings sorted by severity.
4. Positive controls verified.
5. Prioritized remediation plan.
6. Tests/checks executed and exact outcomes.
7. Areas not verified and why.

## Safety constraints

- Do not exploit live systems, exfiltrate data, or use real credentials.
- Do not print secret values; report locations and secret types only.
- Do not modify production configuration or deploy changes.
- Do not claim a clean security audit if relevant surfaces were not inspected.
