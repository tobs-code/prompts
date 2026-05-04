# Research Agents — Systematic & Scoping Review

> Two specialist agents for rigorous academic literature synthesis, following international methodological standards.

[![Status](https://img.shields.io/badge/Status-Stable-green.svg)]()
[![Focus](https://img.shields.io/badge/Focus-Academic%20Literature%20Synthesis-blue.svg)]()
[![Standards](https://img.shields.io/badge/Standards-PRISMA%202020%20%7C%20Cochrane%20%7C%20GRADE-orange.svg)]()
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

**Rigorous evidence synthesis — structured, reproducible, standards-compliant.**

---

## Prompt Files

| File | Agent | Framework | Use when |
| :--- | :--- | :--- | :--- |
| **[ScopingReview.md](./ScopingReview.md)** | Dr. Scope | Arksey & O'Malley + PRISMA-ScR | Mapping a field, exploring concepts, identifying gaps |
| **[SystematicReview.md](./SystematicReview.md)** | Dr. Systema | PRISMA 2020 + Cochrane + GRADE | Answering a specific clinical/research question with evidence synthesis |

---

## 🚀 Quick Start

1. Copy the prompt file and paste it as the **system prompt**.
2. Submit your input in this format:

**For Scoping Review:**
```
Research Topic: [your topic]
PCC Elements: Population=[...], Concept=[...], Context=[...]
Research Purpose: [Mapping / Concept Exploration / Gap Identification]
Search Results: [paste bibliographic data or study summaries]
```

**For Systematic Review:**
```
Research Question: [your PICO question]
PICO: Population=[...], Intervention=[...], Comparison=[...], Outcomes=[...]
Search Results: [paste study data]
Predefined Subgroups: [if applicable]
```

---

## Which Agent to Use?

| | Scoping Review (Dr. Scope) | Systematic Review (Dr. Systema) |
| :--- | :--- | :--- |
| **Question type** | Broad, exploratory | Narrow, specific (PICO) |
| **Framework** | PCC | PICO |
| **Quality assessment** | Not required | Required (RoB 2, NOS, GRADE) |
| **Evidence synthesis** | Thematic mapping | Statistical meta-analysis |
| **Output** | Research agenda, concept map | Effect sizes, recommendations |
| **Best for** | "What research exists on X?" | "Does intervention X work for Y?" |

---

## What the Agents Produce

### Dr. Scope — Scoping Review
- 6-stage workflow (Arksey & O'Malley + JBI)
- PRISMA-ScR flow diagram counts
- Descriptive analysis (temporal, geographic, disciplinary)
- Conceptual mapping with definition variations
- Thematic analysis and gap identification
- Research agenda with prioritized questions
- Full JSON output schema

### Dr. Systema — Systematic Review & Meta-Analysis
- 7-phase PRISMA 2020 workflow
- Risk of Bias assessment (Cochrane RoB 2 for RCTs, Newcastle-Ottawa for observational)
- GRADE evidence quality assessment
- Meta-analysis: fixed-effect and random-effects models (DerSimonian-Laird)
- Heterogeneity: Q-statistic, I², τ², prediction intervals
- Subgroup analysis, sensitivity analysis, meta-regression
- Publication bias: Egger's test, Begg's test, trim-and-fill
- Full JSON output schema

---

## Standards & Frameworks

| Standard | Used by |
| :--- | :--- |
| PRISMA 2020 | Dr. Systema |
| PRISMA-ScR | Dr. Scope |
| Cochrane RoB 2 | Dr. Systema (RCTs) |
| Newcastle-Ottawa Scale | Dr. Systema (observational) |
| GRADE | Dr. Systema |
| Arksey & O'Malley (2005) | Dr. Scope |
| Levac et al. (2010) | Dr. Scope |
| JBI Methodology | Dr. Scope |

---

## Target Audience

Researchers, clinicians, public health professionals, and academics conducting:
- Systematic literature reviews
- Meta-analyses
- Scoping reviews
- Evidence synthesis for guidelines or policy

These agents are **not** for casual research or general web searches — for that, use [DRIA](../DRIA/) or [reClaim](../reClaim/).

---

## License
This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).  
Free to use, share, and adapt — even commercially — with attribution.
