# Transparency & User Disclosures (AIMS / ISO/IEC 42001)

## Purpose
Ensure users understand when AI is used, what it can/cannot do, and what sources and limitations apply—especially for high-impact domains.

## Mandatory disclosure rules

### D-01: AI identification
All AI-generated or AI-assisted content must clearly indicate it is AI-assisted.

### D-02: Source visibility (high-impact)
For high-impact domains (Legal/Finance/HR), the system must provide:
- Sources used (at least for Tier 1 public authoritative content)
- Effective dates where applicable (especially legal/regulatory)
- A short explanation of scope/limitations

### D-03: Limitations and non-reliance statement (Legal)
Legal-related responses must include a concise limitation statement:
- The system provides general guidance and checklists
- It is not a replacement for professional legal advice
- Users should verify critical decisions, and the platform provides escalation options

### D-04: Confidence and uncertainty
If the system is uncertain, conflicting sources exist, or the user request is ambiguous:
- Explicitly state uncertainty
- Ask for required missing inputs OR provide multiple interpretations with clear labeling
- Encourage verification for high-impact actions

### D-05: No hidden cross-tenant content
User-facing outputs must not include any other tenant’s private information.
If the system cannot answer without risking leakage, it must refuse and propose safe alternatives.

## UI/UX guidance (minimum)
- Show a small “AI-assisted” badge
- Provide a “View sources” section for high-impact outputs
- Provide “Request human support” / escalation option for Legal/Finance/HR

## Auditability
For high-impact outputs, logs must capture:
- model + prompt version
- sources used
- disclosure template version (if applicable)

(Reference: ADR-0003 and ADR-0004)
