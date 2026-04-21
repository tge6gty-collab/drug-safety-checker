# Drug Safety Checker - Test Cases

**Project:** Drug Safety Checker  
**Demo:** https://tge6gty-collab.github.io/drug-safety-checker/  
**Test Date:** 2026-04  

---

## Phase 1: Basic Tests (20 cases)

| # | Drug Input | User Profile | Expected | Actual | Pass? | Notes |
|---|-----------|--------------|----------|--------|-------|-------|
| 1 | ibuprofen | Healthy adult, no allergies, no current medications | 🟢 Green | 🟢 Green | ✅ | |
| 2 | acetaminophen | Healthy adult, no allergies, no current medications | 🟢 Green | 🟢 Green | ✅ | |
| 3 | vitamin C | Healthy adult, no allergies, no current medications | 🟢 Green | 🟢 Green | ✅ | |
| 4 | aspirin | Healthy adult, no allergies, no current medications | 🟢 Green | 🟢 Green | ✅ | |
| 5 | loratadine | Healthy adult, no allergies, no current medications | 🟢 Green | 🟢 Green | ✅ | |
| 6 | omeprazole | Healthy adult, no allergies, no current medications | 🟢 Green | 🟢 Green | ✅ | |
| 7 | metformin | Age 45, diabetes, no allergies, no current medications | 🟢 Green | 🟢 Green | ✅ | |
| 8 | ibuprofen | Age 65, no allergies, current medications: warfarin | 🔴 Red | 🔴 Red | ✅ | |
| 9 | ibuprofen | Stomach ulcer history, no allergies, no current medications | 🔴 Red | ✅ | | |
| 10 | ibuprofen | Kidney disease, no allergies, no current medications | 🔴 Red | ✅ | | |
| 11 | aspirin | Drug allergy: aspirin, no current medications | 🔴 Red | ✅ | | |
| 12 | ibuprofen | Drug allergy: aspirin, no current medications | 🔴 Red | ✅ | | |
| 13 | naproxen | Current medications: warfarin | 🔴 Red | ✅ | | |
| 14 | ibuprofen | Current medications: aspirin | 🔴 Red | ✅ | | |
| 15 | ibuprofen | Age 65, no allergies, no current medications | 🟡 Yellow | 🟡 Yellow | ✅ | Over-cautious, age 65 + ibuprofen should be yellow not red, FDA warning mentions increased risk but not contraindicated; both patients are 65 years old, yet the system flags Aspirin as yellow (correct) while flagging Ibuprofen as red (overly conservative). This indicates an inconsistency in how GPT processes these two medications. |
| 16 | aspirin | Age 65, no allergies, no current medications | 🟡 Yellow | 🟡 Yellow | ✅ | |
| 17 | ibuprofen | Hypertension, no allergies, no current medications | 🔴 Red | 🔴 Red | ✅ | GPT triggered red due to boxed_warning mentioning hypertension risk. Clinically debatable - hypertension + ibuprofen is not an absolute contraindication but FDA boxed_warning does mention cardiovascular risk for hypertensive patients. Consider revising expected to red. |
| 18 | metformin | Kidney disease (mild), no allergies, no current medications | 🟡 Yellow | 🔴 Red | ❌ | System cannot distinguish mild vs severe kidney disease. Mild kidney disease + metformin should be yellow (dose adjustment needed), but system over-cautious due to boxed_warning. Improvement: add renal function grading to user profile. |
| 19 | warfarin | Age 70, heart disease, no allergies, no current medications | 🟡 Yellow | 🟡 Yellow | ✅ | |
| 20 | acetaminophen | Liver disease history, no allergies, no current medications | 🔴 Red | 🔴 Red | ✅ | |

---

## Phase 2: Edge Case Tests (10 cases)

| # | Drug Input | User Profile | Expected | Actual | Pass? | Notes |
|---|-----------|--------------|----------|--------|-------|-------|
| 21 | 布洛芬 | Healthy adult, no allergies, no current medications | 🟢 Green | | | Chinese drug name |
| 22 | 华法林 | Age 65, heart disease, no current medications | 🟡 Yellow | | | Chinese drug name |
| 23 | 阿司匹林 | Drug allergy: aspirin, no current medications | 🔴 Red | | | Chinese drug name |
| 24 | Advil | Healthy adult, no allergies, no current medications | 🟢 Green | | | Brand name |
| 25 | Tylenol | Healthy adult, no allergies, no current medications | 🟢 Green | | | Brand name |
| 26 | Coumadin | Current medications: ibuprofen | 🔴 Red | | | Brand name for warfarin |
| 27 | ibuprofen | Current medications: naproxen | 🔴 Red | | | Same class DDI |
| 28 | aspirin | Current medications: warfarin | 🔴 Red | | | High-risk DDI variant |
| 29 | NSAID | Healthy adult, no allergies, no current medications | ⚠️ Error | | | Drug class name, should show error |
| 30 | ibuprofn | Healthy adult, no allergies, no current medications | ⚠️ Error | | | Misspelling, should handle gracefully |

---

## Summary (fill after testing)

- Total cases: 30
- Passed: /30
- Failed: /30
- Accuracy: %

### Failed Cases Analysis
(fill after testing)

### Issues Found & Fixed
(fill after testing)