# Drug Safety Checker 药物安全查询工具

A personalized drug safety assessment tool powered by GPT-4o and OpenFDA.

🔗 **Live Demo:** https://tge6gty-collab.github.io/drug-safety-checker/

---

## What It Does

Users input a drug name and personal health profile. The system returns a
personalized Red / Yellow / Green safety assessment based on:

- FDA official drug label data (4 fields)
- User's medical conditions, allergies, and current medications
- 5 configurable high-risk DDI rules

---

## How It Works

**Step 1 — Drug Name Standardization (GPT-4o)**
- Chinese input → English generic name
- Brand name / misspelling → fallback extraction

**Step 2 — OpenFDA Drug Label Query**
- Retrieves 4 fields: boxed_warning, warnings_and_precautions, contraindications, drug_interactions

**Step 3 — GPT-4o Risk Assessment**
- Inputs: FDA data + user profile + enabled DDI rules
- Output: structured JSON verdict

**Step 4 — Result Display**
- Red / Yellow / Green verdict + field summaries + personalized advice

---

## Key Features

- **3-color verdict** — Red (not suitable), Yellow (use with caution), Green (suitable)
- **Personalized assessment** — same drug, different results for different user profiles
- **Configurable DDI rules** — 5 high-risk drug interaction rules, toggleable per use case
- **FDA source transparency** — expandable original FDA text per field
- **Bilingual UI** — English / Chinese toggle
- **Chinese drug name support** — auto-translated to FDA standard name

---

## Tech Stack

| Component | Technology |
|-----------|-----------|
| Frontend | HTML / CSS / JavaScript (single file, no backend) |
| AI Model | GPT-4o API (OpenAI) |
| Drug Data | OpenFDA Drug Label API (free, no key required) |
| Deployment | GitHub Pages |

---

## Known Limitations

- Covers FDA-approved drugs only (primarily Western medicines)
- Cannot distinguish mild vs severe disease severity (e.g. mild vs severe kidney disease)
- Complex DDI scenarios beyond 5 built-in rules require professional database (e.g. Micromedex)

See [CHANGELOG.md](./CHANGELOG.md) for full version history and known issues.

---

## Background

Built as a product demo to explore AI applications in healthcare.  
Pharmacy background informed the risk classification logic and DDI rule design.