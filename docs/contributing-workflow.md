# Contributing & Workflow

This repo follows a docs-first approach. Architecture decisions and governance rules are captured in ADRs and AIMS documents.

## Branching (simple)
- main: stable documentation and releases
- feature/*: new docs or code features
- fix/*: corrections

## Pull Requests
All changes should be made via PR when possible.

PR must include:
- What changed
- Why it changed
- How it was reviewed
- Any AIMS/ISO42001 impact

## Commit message convention (lightweight)
- docs: ...
- adr: ...
- chore: ...
- feat: ...
- fix: ...

## Quality gates (minimum)
Before merging:
- ADR alignment: follow ADR-0001 to ADR-0004
- Tenant isolation: no cross-tenant access patterns introduced
- Transparency: user-facing AI changes include disclosures where required
- Human oversight: Level 2 rules applied for high-impact domains
- Auditability: logging schema considerations noted (when code starts)

## Working with multiple AI assistants (ChatGPT/Grok/etc.)
- Use ADRs as the source of truth for architecture decisions
- Implement changes in small, well-scoped slices
- Avoid large “rewrite everything” commits
- Document new decisions as ADRs rather than changing old ADRs silently

## Repository structure
- docs/: product, governance, architecture
- docs/adr/: architecture decision records
- docs/30-aims-iso42001/: AIMS governance artifacts
- apps/: applications (created after pilot spec)
- packages/: shared libraries (created after pilot)
