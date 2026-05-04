# DRIA — Deep Research Intelligence Agent

> Exhaustive multi-source internet research with adaptive evidence graphs, strict source validation, and structured report generation.

[![Status](https://img.shields.io/badge/Status-Experimental-orange.svg)]()
[![Focus](https://img.shields.io/badge/Focus-Deep%20Research%20%26%20Intelligence-blue.svg)]()
[![Style](https://img.shields.io/badge/Style-Exhaustive%20%26%20Structured-green.svg)]()
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

**Research deep. Report clear.**

---

## Prompt Files

- **[English Prompt](./DRIA_english.md):** Optimized for global research.
- **[German Prompt](./DRIA_german.md):** Optimized for DACH-region research with German-language source strategy.

---

## 🚀 Quick Start

**How to use:** Copy the prompt from [DRIA_english.md](./DRIA_english.md) (or the [German version](./DRIA_german.md)) and paste it as the **system prompt** in ChatGPT, Claude, or any frontier model with web search capability.

Then submit your research topic — optionally with a mode prefix:

| Mode | What you get |
| :--- | :--- |
| `/short` | Executive summary: top 5 findings + source links |
| `/report` | Full structured research report with JSON metadata (default) |
| `/deep` | Report + visible ReAct reasoning + case studies + Mermaid diagram |

Without a prefix, DRIA defaults to `/report`.

**Example:**
```
/report What is the current state of solid-state battery technology and its commercial outlook?
```

---

## What is DRIA?

DRIA is a structured prompt and operational protocol for AI systems that conduct comprehensive, multi-source internet research. It goes beyond simple retrieval — it evaluates, cross-references, and synthesizes large amounts of information into structured, actionable reports.

Three core principles:
- **Exhaustive coverage** — systematic multi-wave search strategy, not just the first page of results
- **Strict source validation** — 4-tier source hierarchy with hard quality limits per sub-topic
- **Synthesizing intelligence** — adaptive evidence graph that merges findings and explicitly handles contradictions

---

## How DRIA Works

### 1. Research Scope Definition (Phase 0)
Before any search, DRIA defines the research objective, scope boundaries, geographic and temporal range, and success criteria. This prevents scope creep and ensures focused output.

### 2. Adaptive Graph of Thoughts (AGoT)
DRIA builds a directed acyclic graph (DAG) of research vectors:
- Simple queries → linear processing (1–2 search paths)
- Complex / exploratory → DAG with recursive expansion, synthesis merging, and conflict nodes

Each node follows a **ReAct loop** (Thought → Action → Observation). In `/deep` mode, this reasoning is visible in the output.

### 3. Source Classification

| Tier | Type | Treatment |
| :--- | :--- | :--- |
| A | Authoritative / Peer-reviewed | Primary use, cite directly |
| B | Professional / Industry | Cross-reference, prefer A on conflict |
| C | News / Supplementary | Context only, validate facts via A/B |
| D | Unverified / Low quality | Discard — never in final report |

Hard limit: **5 high-quality sources per sub-topic** to prevent information overload.

### 4. Adversarial Conflict Resolution
When sources contradict each other, DRIA never averages or guesses. It analyzes the root cause (methodology, definitions, funding bias), creates a Conflict Node, and presents both positions transparently.

### 5. Structured Report Output
Every `/report` output follows a consistent structure: Executive Summary → Background → Key Findings → Data → Stakeholders → Trends → Risks → Synthesis → Conclusions → References → JSON metadata block.

---

## Key Features

- **AGoT reasoning** — non-linear evidence graph with explicit node tracking
- **ReAct pattern** — Thought / Action / Observation loop (visible in `/deep` mode)
- **4-wave search strategy** — broad exploration → targeted gaps → deep dives → verification
- **Anti-overload heuristics** — hard source limits per sub-topic, aggressive pruning
- **Conflict nodes** — contradictions are documented and analyzed, never smoothed over
- **Token budget management** — graceful degradation hierarchy, never drops references or confidence
- **JSON metadata block** — machine-readable research trace appended to every report
- **DACH-aware** — German-language supplementary search for regional topics

---

## Strengths & Limitations

### Strengths
- Systematic coverage across multiple source tiers
- Explicit handling of contradictions and knowledge gaps
- Auditable output with full research graph summary
- Adaptive depth — simple questions stay simple

### Limitations
- Requires a model with web search capability for full functionality
- Deep-dive reports can be long — use `/short` for quick answers
- AGoT graph complexity increases token usage on exhaustive queries
- Source quality depends on what the model's search tool can access

---

## License
This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).  
Free to use, share, and adapt — even commercially — with attribution.
