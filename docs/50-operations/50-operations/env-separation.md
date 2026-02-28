# Environment Separation (Dev / Test / Prod) — ISO/IEC 27001:2022 A.8.31

Purpose: Ensure development, test, and production environments are separated to reduce risk of unauthorized access, accidental changes, and data leakage.

Scope:
- Applies to all services supporting the suite (web/API, workers, database, storage, monitoring).

References:
- Infra notes: `docs/20-architecture/infra.md`
- Environments: `docs/50-operations/environments.md`
- Security baseline: `docs/40-security-privacy/security-baseline.md`

---

## 1) Separation requirements (minimum)

### 1.1 Logical separation
- Separate environment configurations (different endpoints, keys, databases)
- Separate access controls (RBAC/IAM) per environment
- Separate secrets per environment (never reuse production keys in dev/test)

### 1.2 Data separation
- No production data in dev/test by default
- Use synthetic or masked data for testing (see test-data handling policy when added)

### 1.3 Change separation
- Production changes only via approved change management process
- Staging used to validate releases before production

---

## 2) Access control per environment

### Development
- Wider access allowed for contributors, but still role-based
- Secrets are limited-scope (dev keys)

### Staging (pilot)
- Restricted access (team + selected pilot tenants)
- Admin endpoints protected
- Logging enabled for key actions

### Production (later)
- Strict access (least privilege)
- Production database access limited to minimal operators
- Elevated actions logged and reviewed

---

## 3) Recommended technical patterns

- Separate Postgres databases (or separate clusters) per environment
- Separate object storage buckets per environment
- Separate identity provider apps/clients per environment
- If using VPS:
  - separate VPS per environment where feasible
  - at minimum separate namespaces + secrets

---

## 4) Evidence (what to show)

Examples:
- environment variable sets per env (redacted)
- screenshot/export of IAM/RBAC differences per env
- confirmation that production secrets are not used in dev/test
- staging release validation record before production releases
