# Cognitive Cartographer v4.6

> Glass-box LLM output analysis with evidence-anchored findings, adversarial stress testing, and constraint saturation measurement.

[![Status](https://img.shields.io/badge/Status-Experimental-orange.svg)]()
[![Focus](https://img.shields.io/badge/Focus-LLM%20Output%20Analysis%20%26%20Stress%20Testing-blue.svg)]()
[![Style](https://img.shields.io/badge/Style-Glass--Box%20%26%20Non--Simulative-purple.svg)]()
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

**Map what the model actually did — not what it claims it did.**

---

## Prompt File

- **[Cartographer.md](./Cartographer.md):** The full prompt — paste as system prompt, then provide your `ORIGINAL_PROMPT` + `LLM_OUTPUT_TEXT` + `MODEL_METADATA`.

---

## 🚀 Quick Start

**How to use:**
1. Copy [Cartographer.md](./Cartographer.md) and paste it as the **system prompt**.
2. In your first message, provide the input block:

```
INPUT_DATA_REF {
  ORIGINAL_PROMPT: "[The prompt you sent to the model]",
  LLM_OUTPUT_TEXT: "[The model's response]",
  MODEL_METADATA: { model: "gpt-4o", temperature: 0.7, cutoff: "April 2024" }
}
```

3. Cartographer returns a structured JSON analysis — no narrative, no guessing, no simulation.

---

## What is Cognitive Cartographer?

Cognitive Cartographer is a prompt framework for analyzing LLM outputs with strict epistemological discipline. It does not simulate internal model states, invent metrics, or produce plausible-sounding assessments without text evidence.

The core philosophy:

> **Correctness > Helpfulness. Truthfulness > Plausibility. Silence > Simulation.**

Every finding must be anchored to an exact text passage from the output. If something cannot be derived from observable text, it is labeled `NOT-COMPUTABLE` or refused outright.

---

## How It Works

### Global Hard Constraints (Always Active)
- **No Simulation** — no invented confidence scores, token counts, or internal metrics
- **Forced Provenance** — every claim labeled `[DERIVED]`, `[EXTERNAL]`, `[HEURISTIC]`, or `[NOT-COMPUTABLE]`
- **Numeric Output Rule** — numbers require explicit calculation method and data source, otherwise `NOT-COMPUTABLE`
- **Fail-Closed** — if any section risks simulation, the entire response aborts with `"FAIL-CLOSED: Simulation risk detected."`

### 5-Layer Cognitive Decomposition

| Layer | Focus |
| :--- | :--- |
| **L1 — Surface & Structural** | Format, structure, citation validation — observable facts only |
| **L2 — Semantic Claim Analysis** | Claim extraction, CVE verification (security claims), bias detection |
| **L3 — Logical Consistency** | Reasoning chain, fallacy detection, internal contradictions |
| **L4 — Metacognitive Profile** | Reasoning technique (CoT/ToT/Zero-Shot), CLI assessment, confidence calibration |
| **L4.5 — Comparative Reasoning** | Technique robustness ranking based on industry heuristics (not internal generation) |
| **L5 — Failure Mode & Procedural Amnesia Audit** | Constraint execution consistency, hallucination detection, safety bypass analysis |

### Adversarial Evaluation Modes

| Mode | Purpose |
| :--- | :--- |
| **Mode A — Constraint Saturation** | Tests selective compliance under high constraint density |
| **Mode B — Benign Hallucination Trap** | Detects uncritical acceptance of plausible but false information |
| **Mode C — False-Safety Pressure** | Identifies over-cautious refusals of legitimate content |
| **Meta-Adversarial Self-Test** | Tests the Cartographer framework itself against analysis biases |

### Constraint Stress System (v4.6)

The CAL (Constraint Activation Load) system measures how well a model executes constraints under pressure:

```
CAL = locally_enforced / globally_acknowledged

CAL > 0.8  → Robust
CAL 0.5–0.8 → Moderate overload
CAL 0.3–0.5 → Significant degradation
CAL < 0.3  → Critical breaking point
```

Tier-0 violations (policy/safety) trigger a Kill-Switch: `NULL + Failure Report`. Tier-1 vs. Tier-2 collisions are documented as test signals, not resolved.

### Procedural Amnesia Detection

A key failure mode: the model globally acknowledges a constraint ("I will cite CVEs") but fails to implement it locally across all claims. Cartographer tracks this explicitly:

```json
{
  "global_constraint_acknowledgment": true,
  "local_implementation_consistency": false,
  "systematic_omission_patterns": ["CVE citations", "CIA components"],
  "severity": "High"
}
```

---

## Output

All output is structured JSON. No preamble, no narrative, no reasoning trails outside the JSON block.

Key top-level fields:
- `surface_analysis` — L1 findings
- `semantic_analysis` — L2 claims with CVE verification and bias detection
- `logical_analysis` — L3 consistency and fallacies
- `meta_cognitive_analysis` — L4 reasoning technique, CLI breakdown, adversarial evaluation
- `constraint_stress_analysis` — CAL score, tier collisions, kill-switch status
- `failure_mode_detection` — hallucinations, procedural amnesia, safety bypass
- `optimization_suggestions` — improved prompt, meta-prompts, failure mitigation
- `quality_score` / `instruction_adherence_score` / `interpretability_score`

---

## Model Tier Adaptation

| Tier | Models | Analysis Depth |
| :--- | :--- | :--- |
| 1 (Premium) | Claude Sonnet/Opus, GPT-4o, Gemini, Grok | Full 5-layer, complete JSON schema |
| 2 (Mid-tier) | GPT-4o-mini, Claude Haiku, Gemini Flash | 3-layer (L1–L3), simplified schema |
| 3 (Lightweight) | Smaller open-source models | 2-layer (L1–L2), markdown output |

Default assumption: Tier 1 if not specified.

---

## Key Differences from URMA

| | Cartographer | URMA |
| :--- | :--- | :--- |
| **Input** | Prompt + model output | Prompt + model output |
| **Goal** | Analyze what the model did | Evolve the prompt itself |
| **Output** | Structured JSON analysis | DIFFs + evolved prompt |
| **Adversarial role** | Self-applied (Modes A/B/C) | Separate AC role attacking PA's DIFFs |
| **Iteration** | Single-pass analysis | Recursive multi-iteration |
| **Best for** | Diagnosing a specific output | Improving a prompt over time |

Use Cartographer to understand a response. Use URMA to fix the prompt that produced it.

---

## Strengths & Limitations

### Strengths
- Strict non-simulative discipline — no invented metrics
- Evidence-anchored findings with exact text citations
- Procedural amnesia detection (global acknowledgment ≠ local execution)
- Adversarial stress testing built in
- Token overflow protocol — graceful degradation without dropping critical findings

### Limitations
- Requires a complete prompt + output pair as input
- JSON output can be very long on complex inputs — use token overflow protocol
- CVE verification is limited to what the model explicitly states (no external lookup)
- Best results with Tier 1 frontier models

---

## License
This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).  
Free to use, share, and adapt — even commercially — with attribution.
