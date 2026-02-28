# Change Management (DEV) — ISO/IEC 27001:2022 A.8.32

Purpose: Ensure changes to code, configuration, and security controls are reviewed, approved, tested, and traceable.

Scope:
- Applies to all changes affecting `apps/*`, `packages/*`, `.github/*`, and any production/staging configuration.
- Docs-only changes are also tracked but with lighter process.

References:
- PR template: `.github/PULL_REQUEST_TEMPLATE.md`
- DoD: `docs/50-operations/definition-of-done.md`
- Audit trail: ADR-0003

---

## 1) Change types

### Standard change
- Low risk
- Routine fixes and improvements
- Requires PR + review + tests

### Significant change
Examples:
- Authentication/RBAC changes
- Tenant isolation logic
- RAG retrieval logic and sources
- Logging/audit schema
- Security disclosures for Legal/Finance/HR

Requires:
- PR + code owner review
- Staging verification
- Clear rollback plan

### Emergency change (pilot only)
Used when:
- security incident or production outage requires quick mitigation

Requires:
- minimal PR with explanation
- post-change review and documentation
- follow-up ticket for permanent fix if needed

---

## 2) Required workflow (default)

1. Create an issue/ticket (or PR description) describing:
   - what, why, risk, scope
2. Implement change in a feature branch
3. Open PR using the PR template
4. Review and approval (code owners for sensitive areas)
5. CI checks pass (tests/scans)
6. Deploy to staging (when applicable)
7. Validate acceptance checklist
8. Merge to main + release note entry

---

## 3) Approvals

Minimum:
- At least 1 review for standard changes
- Code owner review for significant changes

Recommended:
- Require code owner approval for:
  - `docs/adr/*`
  - tenant isolation components
  - security/privacy baselines
  - high-impact AI logic (Legal/Finance/HR)

---

## 4) Traceability requirements

Each change must be traceable via:
- PR link
- issue/ticket reference (optional but recommended)
- release note summary (for user-impacting changes)

For high-impact modules:
- record prompt/model version changes (ADR-0004)
- record data source changes (ADR-0002)

---

## 5) Rollback guidance (minimum)

PR must include one of:
- Revert commit strategy
- Feature flag / config toggle
- Deploy previous version

---

## 6) Evidence (what to keep)

Examples:
- PR with approvals and CI checks
- Release notes / changelog entry
- Staging acceptance checklist
- Incident postmortem notes (if emergency change)
