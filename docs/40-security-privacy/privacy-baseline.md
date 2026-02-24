# Privacy Baseline (Pilot)

This document defines minimum privacy practices for the pilot stage of 5SOffice AI Suite.
It complements Security Baseline and AIMS governance documents.

---

## 1) Principles
- Data minimization: collect only what is necessary for the feature
- Purpose limitation: use data only for declared purposes
- Tenant separation: no cross-tenant visibility or reuse of tenant data
- Transparency: users know what data is used and how outputs are generated
- Retention control: define how long data is kept and how deletion is handled

---

## 2) Data categories (pilot)
Typical categories:
- Account data (email, role, tenant_id)
- Usage data (feature usage, timestamps)
- Content data:
  - Legal module: user questions + retrieved Tier-1 sources + generated summaries/checklists
  - Document module (future): uploaded files, OCR text, metadata

High-risk categories (handle carefully):
- Personal data in uploaded documents
- Employment-related information (HR module)
- Finance/tax-related data (Expense module)

---

## 3) Data processing boundaries
- Tenant documents are always tenant-scoped (Tier 2 sources).
- Public authoritative sources are globally shared read-only (Tier 1 sources).
- Derived artifacts (Tier 3) must remain traceable and scoped by tenant unless explicitly global and non-sensitive.

---

## 4) AI/LLM usage
Recommended for pilot:
- Use API-based LLM with strict prompts and governance.
- Avoid using tenant private data for training.
- Apply redaction/minimization before sending to LLM where feasible.
- Ensure outputs follow transparency and human oversight rules for high-impact domains.

---

## 5) Retention (pilot baseline)
Define pilot defaults (to be tuned later):
- Audit metadata logs: 30–90 days (configurable)
- User content (questions/answers): configurable by tenant (default limited)
- Uploaded documents (future): retention by tenant policy

---

## 6) User rights (pilot-level)
For pilot, support basic requests:
- Export: provide basic export of user data (where feasible)
- Deletion: delete user account and associated content per tenant policy
- Correction: allow updating account information

(Advanced DSAR automation can be considered later.)

---

## 7) Access control
- Role-based access within tenant (RBAC)
- Restrict platform admin access
- Log admin actions

---

## 8) Privacy incident handling
Privacy incidents include:
- suspected cross-tenant leakage
- unauthorized access to personal data
- accidental exposure of sensitive documents

Minimum response:
- contain → investigate → notify stakeholders → remediate → document

---

## 9) Next steps (post-pilot)
- Formalize retention policies per module
- Add privacy-by-design review for each new module
- Add DPIA-style assessment for high-impact use cases where applicable
