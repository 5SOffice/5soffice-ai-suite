# Secure Coding Standard (DEV) — ISO/IEC 27001:2022 A.8.28

Purpose: Provide a practical secure coding standard for development teams, aligned with ISO/IEC 27001:2022 control **A.8.28 Secure coding**.

This standard is designed to be used in:
- Code reviews
- Pull requests
- Development onboarding
- Definition of Done (DoD)

---

## 1) General principles

- **Secure by default:** choose safe defaults; avoid “optional security”.
- **Least privilege:** minimal permissions for services, users, and tokens.
- **Defense in depth:** multiple controls (auth + validation + logging + rate limit).
- **Fail securely:** errors must not reveal secrets or sensitive details.
- **No secrets in code:** never commit credentials, tokens, private keys.

---

## 2) Input validation & output encoding

- Validate all external inputs (API requests, webhooks, file uploads).
- Use allow-lists where possible (e.g., enums, formats).
- Apply output encoding for UI rendering to prevent injection issues.
- Protect against:
  - SQL injection (use parameterized queries / ORM safe APIs)
  - XSS (escape output, use safe rendering)
  - SSRF (block internal network access unless explicitly required)

---

## 3) Authentication & session security

- Prefer strong authentication methods (OIDC, SSO) where applicable.
- Store passwords only as strong hashes (if used).
- Protect sessions:
  - secure cookies (Secure, HttpOnly, SameSite)
  - short-lived tokens with refresh strategy
- Implement account lockout / rate limiting for brute force attempts.

---

## 4) Authorization (RBAC / ABAC)

- Enforce authorization server-side for every sensitive operation.
- Do not rely on UI-only checks.
- Multi-tenant requirement:
  - every request must be scoped by `tenant_id`
  - never allow cross-tenant access (see ADR-0001)

---

## 5) Error handling & logging

- Do not leak sensitive info in error messages (stack traces, tokens, keys).
- Log security-relevant events:
  - admin actions
  - permission changes
  - authentication failures
- Logs must avoid containing secrets and unnecessary personal data.

(Reference: ADR-0003)

---

## 6) Cryptography usage (basic rules)

- Use modern, vetted algorithms and libraries.
- Do not implement custom crypto.
- Encrypt in transit (TLS) and consider encryption at rest for sensitive data.
- Store keys securely (KMS/secret manager), rotate as needed.

(Reference: A.8.24; crypto standard file recommended)

---

## 7) Dependency and supply-chain security

- Pin versions where practical.
- Monitor vulnerabilities (dependency scanning).
- Remove unused dependencies.
- Validate third-party packages and avoid untrusted sources.

---

## 8) File upload & document handling

- Validate file type and size.
- Scan for malware (when feasible).
- Store uploads in isolated storage with restricted access.
- Prevent path traversal and unsafe filename usage.
- Do not store sensitive documents unencrypted.

---

## 9) Secure coding checklist (for PR reviews)

PR author confirms:

- [ ] No secrets committed
- [ ] Input validation applied for external inputs
- [ ] Authorization enforced server-side (including tenant scope)
- [ ] Sensitive data is not logged
- [ ] Errors handled safely (no sensitive leakage)
- [ ] Dependencies updated or scanned (where applicable)
- [ ] Security tests updated/run (where applicable)

Reviewer confirms:

- [ ] Changes align with this standard and DoD
- [ ] High-risk changes have appropriate tests
- [ ] Multi-tenant isolation is preserved

---

## 10) Minimum evidence (what “implementation” looks like)

Evidence examples:
- PRs referencing this checklist
- Code review comments indicating issues fixed
- CI logs showing lint/tests/security checks
- Records showing secret scanning enabled
