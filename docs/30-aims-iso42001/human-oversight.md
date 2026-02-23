# Human Oversight Policy (AIMS / ISO/IEC 42001)

## Purpose
Define how human oversight is applied to AI-assisted features to reduce risk, especially in high-impact domains (Legal/Finance/HR).

## Oversight levels

### Level 0 — Informational
- Impact: Low
- AI behavior: Provide information or suggestions that do not meaningfully affect compliance, finance, employment, or safety.
- Requirements:
  - Show AI identification badge (AI-assisted)
  - No special approval required

### Level 1 — Assistive (User confirmation)
- Impact: Medium
- AI behavior: Recommend actions that may affect operational decisions but are reversible and low risk.
- Requirements:
  - User must explicitly confirm before any execution (e.g., scheduling, sending messages)
  - Provide brief reasoning and key assumptions
  - Provide “Edit before apply” option

### Level 2 — High impact (Review + escalation path)
- Impact: High (Legal/Finance/HR decisions)
- AI behavior: Provide guidance, checklists, and interpretations that could affect regulatory compliance, taxes, hiring decisions, or contractual obligations.
- Requirements:
  - Always show sources (Tier 1 for legal/regulatory where applicable)
  - Always show effective dates for legal/regulatory content
  - Mandatory limitation statement (“general guidance, not legal advice” for Legal)
  - Require explicit user acknowledgment before applying any recommended action
  - Provide escalation path to a human (e.g., request consultant / support ticket)
  - Store an auditable record (per ADR-0003)

## High-impact modules (initial)
- AI Legal Compliance Tracker & Advisor
- AI Expense Tracker & Financial Insights (when tax/filing impact is involved)
- AI HR Assistant (candidate ranking, screening factors)

## Escalation rules (minimum)
Escalate to human support when:
- The user requests “legal conclusion” or asks for definitive interpretation
- The system detects conflicting sources or uncertainty
- The question is jurisdiction-specific or depends on contract terms
- The output could lead to irreversible action or penalties

## User control requirements
- Users can override, ignore, or edit AI suggestions
- Users can request re-check with updated inputs
- Users can view sources and rationale for high-impact outputs

## Auditability
For Level 2 interactions, logs must include:
- tenant_id, user role, timestamp
- model + prompt version
- sources + effective dates (if applicable)
- user acknowledgment and actions taken
