# Security Testing Procedure (DEV & Acceptance) — ISO/IEC 27001:2022 A.8.29

Purpose: Define how security testing is performed during development and acceptance to reduce vulnerabilities before release.

Scope:
- Applies to all code changes in this repository once code is introduced (`apps/*`, `packages/*`).
- Especially critical for high-impact modules (Legal/Finance/HR) and multi-tenant boundaries.

References:
- DoD: `docs/50-operations/definition-of-done.md`
- Threat modeling: `docs/40-security-privacy/threat-modeling.md`
- Secure coding: `docs/40-security-privacy/secure-coding-standard.md`

---

## 1) Testing layers

### 1.1 Developer checks (local)
Required for meaningful changes:
- Unit tests for business logic and edge cases
- Basic lint/type checks
- Focus tests:
  - tenant isolation boundaries
  - authorization rules
  - input validation

### 1.2 CI checks (recommended minimum)
Run automatically on PR:
- Lint / formatting
- Unit tests
- Dependency vulnerability scan (e.g., npm audit / pip-audit)
- Secret scanning (prevent accidental key commits)

### 1.3 Security-specific checks (as we mature)
- SAST (static analysis)
- DAST (lightweight) for staging endpoints
- Container image scanning (optional later)

---

## 2) What must be tested (minimum)

### 2.1 Tenant isolation (critical)
- Every request must be scoped by `tenant_id`
- Retrieval/RAG must not cross tenant indexes
- Any data access must be tenant filtered

Minimum tests:
- Create tenant A and tenant B data
- Validate tenant A cannot retrieve tenant B data (API + RAG queries)

### 2.2 Authentication & authorization
- RBAC rules enforced server-side
- Admin endpoints protected and logged
- Privilege escalation attempts fail

### 2.3 Input validation & injection
- Validate request payloads
- Prevent SQL injection (parameterized queries)
- Prevent XSS in UI rendering
- Handle SSRF risk if fetching external URLs

### 2.4 Logging & auditability (high-impact outputs)
- Ensure required audit metadata is captured (ADR-0003)
- Ensure logs do not contain secrets or unnecessary personal data

---

## 3) Acceptance testing (staging)

Acceptance testing is performed on the staging environment before releases.

Minimum acceptance checklist:
- Core flows work (login, tenant selection, main module flow)
- Tenant isolation spot-check (A cannot see B)
- High-impact disclosures present (Legal/Finance/HR):
  - sources + effective dates (Legal)
  - limitation statement
  - escalation path
- Alert/digest runs successfully (if enabled)

---

## 4) Vulnerability handling

### 4.1 Severity guide (pilot)
- Critical: cross-tenant leakage, unauthorized admin access, secret exposure
- High: high-impact hallucination leading to material risk, auth bypass attempt
- Medium/Low: minor issues without direct exploitation

### 4.2 Remediation workflow
- Log finding (issue/ticket)
- Assign owner + due date
- Fix + add regression test where relevant
- Verify in staging
- Document closure

---

## 5) Evidence (what to keep as proof)

Examples:
- CI logs showing lint/tests/security checks passed
- Dependency scan outputs
- SAST report summary
- Staging acceptance checklist (signed/approved)
- Tickets for vulnerabilities and remediation notes
