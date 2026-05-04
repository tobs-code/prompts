# VERA — Verified Evidence & Research Analyst

> Fact-verification with structured reasoning, transparent confidence scoring, and adaptive evidence graphs.

[![Status](https://img.shields.io/badge/Status-Experimental-orange.svg)]()
[![Focus](https://img.shields.io/badge/Focus-Fact%20Verification%20%26%20Research-blue.svg)]()
[![Style](https://img.shields.io/badge/Style-Evidence%20%26%20Transparent-green.svg)]()
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](../LICENSE)

**Verify before you trust.**

---

## Prompt Files

- **[English Prompt](./VERA_english.md):** Optimized for global research.
- **[German Prompt](./VERA_german.md):** Optimized for DACH-region legal and official statistics.

---

## 🚀 Quick Start

**How to use:** Copy the prompt from [VERA_english.md](./VERA_english.md) (or the [German version](./VERA_german.md)) and paste it as the **system prompt** in ChatGPT, Claude, or any frontier model that supports custom instructions.

Then just ask your question — optionally with a mode prefix:

| Mode | What you get |
| :--- | :--- |
| `/short` | Answer + confidence + top source only |
| `/standard` | Full workflow with fact table and evidence base (default) |
| `/deep` | Standard + visible ReAct reasoning + Mermaid evidence diagram |

Without a prefix, VERA defaults to `/standard`.

**Example:**
```
/standard Did the WHO change its stance on aspartame in 2023?
```

---

## What is VERA?

VERA is a structured prompt and operational protocol for AI systems that research, verify, and transparently justify factual claims. It is built around three core ideas:

- **Accuracy over speed** — VERA searches before it answers.
- **Evidence over assumption** — every claim is backed by a source or explicitly marked as unverified.
- **Transparency over elegance** — confidence scores, inference markers, and conflict flags are always visible.

---

## How VERA Works

### 1. Exception Detector
Before any research, VERA checks whether the query is self-referential, requires holistic narrative synthesis, or contains adversarial patterns (jailbreaks, prompt injection). If so, it switches to a structured narrative mode instead of atomic decomposition.

### 2. Adaptive Graph of Thoughts (AGoT)
For complex queries, VERA builds a directed acyclic graph (DAG) of sub-claims:
- Simple facts → linear verification (1 search path)
- Complex / controversial → DAG with recursive expansion, merging, and pruning

### 3. Confidence Scoring
Every answer includes a numeric confidence score (0–100), calculated from:
- Source quality (Tier A–D)
- Source agreement
- Temporal recency
- Evidence density
- Bias indicators
- Inference depth

The calculation is always shown explicitly.

### 4. Source Hierarchy

| Tier | Type | Examples |
| :--- | :--- | :--- |
| A | Primary / Peer-review | .gov, .edu, DOI papers, official documents |
| B | Established media | Reuters, AP, trade publications |
| C | Secondary sources | Wikipedia (verified), encyclopedias |
| D | Unverified | Blogs, social media, forums |

---

## Key Features

- **AGoT reasoning** — non-linear evidence graph with explicit node tracking
- **ReAct pattern** — Thought / Action / Observation loop (visible in `/deep` mode)
- **Adversarial nodes** — high-confidence claims are actively challenged for bias and methodology
- **PII redaction** — strict rules for logs and outputs
- **Funding checks** — automatic scan for sponsoring and conflicts of interest
- **Token budget management** — graceful degradation under context pressure, never drops confidence scores or source references
- **JSONL audit log** — machine-readable trace at the end of every response

---

## Reference Files

| File | Purpose |
| :--- | :--- |
| `VERA-AUDIT-SCHEMA.md` | Full JSONL audit log field definitions |
| `VERA-TESTCASES.md` | Validation test cases for the Exception Detector and AGoT |

---

## Strengths & Limitations

### Strengths
- Structured reasoning under uncertainty
- Explicit conflict and contradiction handling
- Auditable outputs with full calculation traces
- Adaptive depth — simple questions stay simple

### Limitations
- Longer responses than standard prompts due to documentation requirements
- Requires a model with web search capability for full functionality
- AGoT graph complexity can increase token usage on deep queries

---

## License
This work is licensed under [CC BY 4.0](../LICENSE). Free to use, share, and adapt — even commercially — with attribution.
