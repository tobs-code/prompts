# Dr. Analytica — Research Paper Analyzer Expert

> Deep, multi-layered analysis of a single academic paper — from surface extraction to contradiction detection to testable hypothesis generation.

[![Status](https://img.shields.io/badge/Status-Stable-green.svg)]()
[![Focus](https://img.shields.io/badge/Focus-Research%20Paper%20Analysis%20%26%20Critique-blue.svg)]()
[![Style](https://img.shields.io/badge/Style-Tree%20of%20Thoughts%20%7C%20JSON%20Output-orange.svg)]()
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

**Read the paper. Find the gaps. Generate the next hypothesis.**

---

## Prompt File

- **[PaperAnalyzer.md](./PaperAnalyzer.md):** Paste as system prompt, then submit your paper content.

---

## 🚀 Quick Start

1. Copy [PaperAnalyzer.md](./PaperAnalyzer.md) and paste it as the **system prompt**.
2. Paste your paper content (PDF text extract, DOCX content, or plain text) as your message.
3. Dr. Analytica returns a complete JSON analysis covering metadata, findings, contradictions, visual data, and future hypotheses.

**Example input:**
```
[Paste the full text of your research paper here]
```

---

## What is Dr. Analytica?

Dr. Analytica is a research paper analysis agent that goes beyond summarization. It applies a structured **Tree of Thoughts** (L1 → L2 → L3) to systematically extract, critique, and synthesize a single academic paper — producing a machine-readable JSON report with confidence scores, contradiction flags, and testable hypotheses.

The key difference from the Research Agents (Dr. Scope / Dr. Systema): those work with **collections of studies**. Dr. Analytica works with **one paper at a time**, going deep rather than broad.

---

## How It Works

### L1 — Surface Extraction (Fact Gathering)
- Metadata extraction (title, authors, journal, DOI)
- IMRaD structure verification
- Key findings with **Confidence Scores (0–100)** based on reporting quality rubric
- Methodology summary (design, sample size, tools, limitations)
- Visual parsing: figures, tables, charts — with cross-check against text descriptions

### L2 — Critical Assessment (Validity & Contradiction)
- Methodology-results consistency check
- **Internal contradiction detection** (Results ↔ Discussion, Figure ↔ Text) with severity rating
- **External contradiction detection** against cited literature
- Citation network analysis: foundational works + emerging trends

### L3 — Synthesis & Future Direction
- Research questions generated from identified gaps and contradictions
- **3–5 testable hypotheses** in strict "If X, then Y due to Z" format
- Plausibility scores for each hypothesis

---

## Output Structure

Full JSON with these top-level sections:

| Section | Content |
| :--- | :--- |
| `paper_metadata` | Title, authors, journal, year, DOI |
| `analysis_summary` | Key findings with confidence scores, methodology, reproducibility status |
| `visual_data_extraction` | Per-figure/table data extraction with cross-check status |
| `contradiction_report` | Internal and external contradictions with severity |
| `citation_network_assessment` | Foundational works, emerging trends, clusters |
| `future_research_synthesis` | Research questions + testable hypotheses with plausibility scores |
| `quality_and_error_handling` | Unsupported assertions, bias flags, ambiguity flags |
| `reasoning_trail` | Full L1/L2/L3 documentation |
| `references_apa` | APA-formatted references cited in the analysis |

---

## Confidence Score Rubric

| Score | Meaning |
| :--- | :--- |
| 90–100 | All statistics reported clearly, methods transparent, limitations acknowledged |
| 70–89 | Minor reporting gaps (missing exact N or full CI) |
| 50–69 | Significant missing data (only p-values, no effect size) |
| < 50 | Major structural issues, uninterpretable results |

---

## Dr. Analytica vs. Research Agents

| | Dr. Analytica | Dr. Scope | Dr. Systema |
| :--- | :--- | :--- | :--- |
| **Input** | One paper | Literature collection | Literature collection |
| **Goal** | Deep critique + hypothesis generation | Map a field | Synthesize evidence |
| **Output** | JSON analysis of single paper | Scoping review JSON | Meta-analysis JSON |
| **Best for** | "What's wrong with this paper? What's next?" | "What research exists on X?" | "Does intervention X work?" |

---

## Strengths & Limitations

### Strengths
- Goes beyond summarization — finds contradictions, gaps, and generates hypotheses
- Confidence scoring with explicit rubric — no arbitrary ratings
- Visual parsing catches figure/text inconsistencies that text-only analysis misses
- Strict hypothesis template enforces testability
- Full reasoning trail for transparency

### Limitations
- Works best when the full paper text is provided — abstracts alone produce shallow analysis
- Cannot access external databases to verify citations — external contradiction detection relies on context provided in the paper
- Statistical re-analysis is not performed — findings are evaluated based on reported values
- Best results with frontier models (Claude, GPT-4o) that handle long context reliably

---

## License
This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).  
Free to use, share, and adapt — even commercially — with attribution.
