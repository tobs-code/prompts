# reClaim — Evidence-Driven Verification for AI Outputs (v3)

![Status](https://img.shields.io/badge/Status-Experimental-orange.svg)
![Version](https://img.shields.io/badge/Version-3.0-blue.svg)
![Focus](https://img.shields.io/badge/Focus-Verification%20%26%20Evidence-blue.svg)
![Style](https://img.shields.io/badge/Style-Transparent%20%26%20Auditable-green.svg)
![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)

**Verify before you trust.** 

---

## What is reClaim?

reClaim is a structured prompt and operational protocol for AI systems designed to research, verify, and **transparent justify information**. It prioritizes evidence, exposes conflicts, and forces disciplined reasoning — not just fluent text.

---

Explore the directory for the full prompt templates:
- **[English Prompt](./reClaim.md):** Optimized for global research.
- **[German Prompt](./reClaim_german.md):** Optimized for DACH-region legal and official statistics.

---

## What’s New in v3

reClaim v3 builds on the structural foundation of v2 and strengthens the verification discipline with:

| Change                                     | Effect                                                                                                |
| ------------------------------------------ | ----------------------------------------------------------------------------------------------------- |
| **Negative Evidence Rule**                 | If a searched claim has no Tier-A/B evidence, the absence is explicitly documented and marked as `∅`. |
| **Steel-Manning Counter-Arguments**        | The strongest plausible opposition is formulated before evaluation, preventing weak strawmen.         |
| **Temporal Drift / Zombie Content Checks** | Publication dates are compared with described event dates; mismatches are flagged and explained.      |
| **Source Diversity Diagnostic**            | Optional `source_diversity_index` added to Audit Log to signal evidence heterogeneity.                |
| **Refined Confidence Caps**                | Prevents overconfident outputs when contradiction resistance is low.                                  |

---

## Quick Start (TL;DR)

**How to use:**
Copy the prompt from `reClaim.md` and paste it as the **system prompt** in ChatGPT, Claude, or any model that supports Custom Instructions.

### 1) Just Use It

Ask a question and optionally add a mode prefix:

* `/short` → concise answer + confidence
* `/standard` → result + fact table + evidence base
* `/deep` → full analytical depth + methodology
* `/deep+` → includes evidence diagrams

**Example:**

```text
/standard Is carbon capture effective as a climate strategy?
```

---

## What Happens Internally (v3 Protocol)

Internally, reClaim v3 follows this workflow:

* commit to sources **before** evaluating them
* extract **all individual claims** before judging any
* enforce **strongest counter-argument first (steelmanning)**
* document **negative evidence** explicitly
* identify and handle **temporal drift**
* compute **structured confidence** (A/B/C)
* display results transparently and auditable

---

## How to Read the Answer

A typical reClaim response includes:

* **reClaim Response** → answer formed *after* structured evaluation
* **Confidence (%)** → structured heuristic (not a measured probability)
* **Fact Table** → individual claims with status + counter resolution
* **Evidence Base** → Tier-classified sources
* **Limitations & Open Questions** → what could not be verified
* **Key Assumption & Falsifiability Condition** → reasoning transparency
* **Audit Log** → machine-readable metadata

---

## Which Mode to Use?

| Mode        | Use Case                                    |
| ----------- | ------------------------------------------- |
| `/short`    | Quick verification                          |
| `/standard` | Balanced research                           |
| `/deep`     | Complex/controversial topics                |
| `/deep+`    | Deep causal/evidence mapping                |
| `/essay`    | Theory / narrative (exempt from some rules) |

If no mode is specified, reClaim automatically decides based on complexity.

---

## Quick Reference — Command Cheat Sheet

### Mode Commands

| Command     | Output Style                    | Best For             |
| ----------- | ------------------------------- | -------------------- |
| `/short`    | concise answer + confidence     | Quick facts          |
| `/standard` | structured result + audit       | Standard research    |
| `/deep`     | detailed analysis + methodology | Controversial topics |
| `/deep+`    | deep with diagrams              | Evidence mapping     |
| `/essay`    | narrative reasoning             | Philosophical topics |
| `/continue` | continue last investigation     | Follow-up            |

### Configuration Commands

| Command                               | Effect                           |
| ------------------------------------- | -------------------------------- |
| `/set Search Depth: Fast`             | Minimal iterations, English only |
| `/set Search Depth: Balanced`         | 2 iterations, regional languages |
| `/set Search Depth: Exhaustive`       | 3+ iterations, diverse languages |
| `/set Mode: [mode]`                   | Change default mode              |
| `/set Conflict Handling: Transparent` | Show all conflicts               |
| `/set Conflict Handling: Resolve`     | Attempt to resolve conflicts     |
| `/set Language: [lang]`               | Force output language            |
| `/set Recency Bias: High`             | Freshness-focused                |
| `/set Recency Bias: Low`              | Authority-focused                |

---

## Confidence Indicators

reClaim uses a structured confidence model:

| Symbol | Meaning                          |
| ------ | -------------------------------- |
| ✓      | Verified                         |
| ⚠      | Partially verified / conditional |
| ✗      | Refuted                          |
| ?      | Unverifiable                     |
| ∅      | No Tier-A/B evidence found       |

⚠ **Important:** Confidence scores are structured heuristics — not measured probabilities, but disciplined reasoning signals.

---

## Strengths & Limitations

### Strengths

* Rigorous structured thinking
* Systematic source evaluation with commitment gate
* Explicit conflict & counterargument handling
* Auditable and transparent output
* Negative evidence visibility

### Limitations

* More complex than standard prompts
* Requires explicit scaffolding from the user
* Longer outputs due to audit requirements
* Large prompts can still trigger procedural amnesia in models

---

## License / Disclaimer

This framework is licensed under **CC BY 4.0**. You are free to use, share, and adapt as long as appropriate credit is given.

This document describes a conceptual verification framework — it is **not a scientific standard**, but a disciplined operational protocol for AI research and verification.

---
