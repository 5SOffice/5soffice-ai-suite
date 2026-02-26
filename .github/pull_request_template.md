## What
Describe what this PR changes.

## Why
Explain the motivation / problem being solved.

## Scope
- [ ] Docs-only
- [ ] Code change
- [ ] Infra/ops change

## How to test
Steps to validate the change locally/staging.

## Architecture & Governance checks (required)
- [ ] ADR alignment checked (ADR-0001 → ADR-0004)
- [ ] Tenant isolation enforced (tenant_id scoped in all relevant paths)
- [ ] No cross-tenant access patterns introduced
- [ ] Logging/audit fields considered (ADR-0003)

## AIMS / ISO/IEC 42001 checks (if AI user-facing)
- [ ] Transparency disclosures included where required
- [ ] High-impact domain rules applied (Legal/Finance/HR)
- [ ] Human oversight / escalation path implemented where required
- [ ] Sources + effective dates provided for Legal outputs (Tier 1)

## Security & Privacy checks
- [ ] No secrets committed (keys/tokens/passwords)
- [ ] Data minimization applied (do not send unnecessary data to LLM)
- [ ] Prompt injection considered (treat retrieved content as untrusted)
- [ ] Backup/restore impact considered (if DB/schema changes)

## Rollback plan
How to revert safely if the change causes issues.

## Notes
Anything else reviewers should know.
