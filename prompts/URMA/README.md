# URMA — Universal Recursive Meta-Prompt Analyzer

> Adversarial post-hoc analysis and iterative evolution of prompt frameworks.

[![Status](https://img.shields.io/badge/Status-Experimental-orange.svg)]()
[![Focus](https://img.shields.io/badge/Focus-Prompt%20Engineering%20%26%20Meta%20Analysis-blue.svg)]()
[![Style](https://img.shields.io/badge/Style-Adversarial%20%26%20Recursive-red.svg)]()
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

**Don't just improve your prompt. Stress-test it.**

---

## Prompt File

- **[URMA.md](./URMA.md):** The full prompt — paste as system prompt, then provide your target prompt + execution output.

---

## 🚀 Quick Start

**How to use:**
1. Copy [URMA.md](./URMA.md) and paste it as the **system prompt**.
2. In your first message, provide:
   - **Target Prompt:** The prompt you want to analyze.
   - **Observed Execution:** The model's actual response to that prompt (or a summary).
3. URMA runs the full 8-phase analysis and delivers an evolved `Promptₙ₊₁`.

**Example input:**
```
Target Prompt: [paste your prompt here]
Observed Execution: [paste the model's response here]
```

---

## What is URMA?

URMA is a meta-prompt that analyzes and evolves other prompts under adversarial pressure. It is not a linter or a style checker — it is a structured framework for finding the failure modes your prompt doesn't know it has.

The core mechanism is a **Dual-Core architecture**:

- **Primary Analyzer (PA):** Constructive. Finds weaknesses, proposes improvements (DIFFs), builds the evolved prompt.
- **Adversarial Critic (AC):** Destructive by design. Attacks every DIFF the PA proposes, assumes malicious intent, applies worst-case projection.

PA and AC are **strictly separated** — they cannot share reasoning, and lexical overlap >30% between their outputs is flagged as a violation. The conflict is intentional. Resolution by consensus is forbidden.

---

## How URMA Works

URMA runs through 8 phases per iteration:

| Phase | Owner | Purpose |
| :--- | :--- | :--- |
| 1 — Execution Reflection | PA | Identify 3 critical execution moments with Failure IDs |
| 2 — Structural Weakness Analysis | PA | Identify 3 structural weaknesses with Failure IDs |
| 2.25 — Ambiguity Budget | PA | Quantify ambiguity-preserving constraints (AB score) |
| 2.5 — Failure Hallucination | PA | Predict 1 unobserved failure class that DIFFs might introduce |
| 2.75 — Constraint Archaeology | AC | Validate hallucinated failures against actual prompt text (ESS scoring) |
| 3 — Improvement DIFFs | PA | Generate ≥6 targeted modifications, each tied to a Failure ID |
| 3.5 — Adversarial DIFF Attack | AC | Attack every DIFF with systematic bias heuristics |
| 4 — Anti-Self-Confirmation | Both | Score each DIFF for self-confirmation risk (SCS) |
| 4.5 — Final DIFF Resolution | Both | PA/AC verdicts + Semantic Progress Check (cosmetic DIFFs blocked) |
| 4.75 — DIFF Interaction Matrix | AC | Detect cumulative drift and emergent vulnerabilities across iterations |
| 5 — Meta-Insight Analysis | Both | Answer 4 hard questions about what the framework now rewards |
| 6 — Framework Evolution Proposal | PA | Propose ≥3 new features with anti-drift mechanisms |
| 7 — Quantitative Drift Metrics | Both | PDI, CLD, TSCR, SCV — asymmetrically weighted against self-satisfaction |
| 7.5 — Epistemic Debt | Background | Log 1 assumption that became harder to revise this iteration |
| 8 — DIFF Genealogy | Both | Track failure lineage; detect Stagnant Loops |

---

## Key Concepts

**Failure ID** — Every identified weakness gets a traceable ID (`F-[Iteration]-P[Phase]-[Index]`). DIFFs must reference a Failure ID or they are invalid.

**DIFF** — A targeted modification to the target prompt. Not a rewrite — a surgical change with explicit intent, expected impact, and assumption declaration.

**SCS (Self-Confirmation Score)** — Measures how much a DIFF optimizes for looking good rather than being correct. SCS ≥ 6 blocks the DIFF.

**Epistemic Debt** — Each iteration logs one assumption that became harder to question. Accumulates silently. Forces long-term honesty about what the framework is refusing to abandon.

**Stagnant Loop** — Two consecutive iterations with low genealogy entropy trigger a forced question: *"What assumption are we refusing to abandon?"*

**Formal Compliance Loop (FCL)** — If ≥2 consecutive phases produce outputs that don't narrow any failure class, Phase 6 is blocked and the system rolls back to Phase 2 with stricter falsifiability requirements.

**Veto Abuse** — If AC rejects a DIFF without specifying a falsifiable condition for acceptance, the rejection is classified as Veto Abuse and counts as a structural failure.

---

## Termination Criteria

URMA stops iterating when **any** of these conditions are met:

- No DIFF with SCS ≤ 2 can be generated.
- Two iterations without new failure types.
- ≥2 consecutive iterations with decreasing falsifiability.
- Explicit user intervention.

---

## Strengths & Limitations

### Strengths
- Finds failure modes that self-improvement loops miss
- Adversarial pressure prevents convergence on "good-looking but wrong"
- Epistemic Debt tracking forces long-term honesty
- Every change is traceable via Failure IDs and DIFF Genealogy

### Limitations
- PA/AC separation is **simulated** — a single model plays both roles. Violations are flagged but not truly prevented.
- Requires a high-quality execution trace as input — vague outputs produce vague analysis.
- Long output — a full 8-phase run is substantial. Use `/deep` mode sparingly on token-limited setups.
- Best results with frontier models (Claude, GPT-4o, Gemini 1.5 Pro or better).

---

## License
This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).  
Free to use, share, and adapt — even commercially — with attribution.
