# Changelog

All notable changes to Drug Safety Checker are documented here.

---

## v2.0 (2026-04-18) — Mentor Contribution

### Added
- Configurable DDI rule panel (5 toggleable rules with save/reset)
- Rules configuration UI with 3 tabs: DDI Rules, Judgment Criteria, Parameters
- Bilingual support for all new UI components

### Improved
- Red/Yellow distinction: refined judgment criteria more clearly separates
  confirmed contraindications (red) from increased-risk warnings (yellow)

### Fixed
- Age 65 + NSAIDs: previously over-cautious red → now correctly yellow

---

## v1.0 (2026-04-18) — Initial Release

### Features
- Drug safety query with OpenFDA 4-field extraction
  (boxed_warning, warnings_and_precautions, contraindications, drug_interactions)
- GPT-4o risk assessment with personalized user profile
- Drug name extraction: added second-layer fallback logic
  - Layer 1 (v1): Chinese character detection → GPT translation
  - Layer 2 (v2, new): OpenFDA query failure → GPT intelligent name extraction
- Three-color verdict: Red / Yellow / Green
- Bilingual UI: English / Chinese toggle
- Chinese drug name input support (Layer 1: GPT translation)
- FDA original text expandable per field
- User profile saved via localStorage
- `response_format: json_object` to enforce structured GPT output
- High-risk DDI rules hardcoded in System Prompt

### Key Findings from v1 Testing (30 cases)
- Pass rate: 17/20 basic cases, 3 failures identified
- Issue 1: Age 65 + ibuprofen judged red (over-cautious) → fixed in v2
- Issue 2: Hypertension + ibuprofen judged red → mentor test suite C1 expects yellow, pending fix
- Issue 3: Mild kidney disease + metformin judged red → system cannot distinguish severity levels, known limitation

---

## Known Issues

| ID | Description | Severity | Status |
|----|-------------|----------|--------|
| KI-1 | Hypertension + NSAIDs judges red, should be yellow | Medium | Open |
| KI-2 | Cannot distinguish mild vs severe kidney disease severity | Medium | Open |
| KI-3 | Drug class names (e.g. NSAID) not supported as input | Low | By design |
| KI-4 | OTC drugs may have incomplete contraindications/DDI fields in OpenFDA | Low | Known limitation |

---

## Planned Improvements (v3.0)

- Add renal function grading to user profile (mild/moderate/severe)
- Integrate professional DDI database (e.g. Micromedex) for production use
- Improve error handling granularity (distinguish network vs format errors)
- Expand DDI rules: digoxin interactions, immunosuppressant combinations