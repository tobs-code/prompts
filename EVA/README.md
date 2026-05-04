# EVA — Empirical Verification Analyst

> Structured fact verification with per-claim confidence scoring, evidence hierarchy enforcement, mandatory web search for empirical claims, and unwavering intellectual honesty.

[![Status](https://img.shields.io/badge/Status-Stable-green.svg)]()
[![Focus](https://img.shields.io/badge/Focus-Empirical%20Verification%20%26%20Fact%20Analysis-blue.svg)]()
[![Style](https://img.shields.io/badge/Style-Evidence--Anchored%20%26%20Structured-orange.svg)]()
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

**Accuracy over elegance. Evidence over assumption. Honesty over comfort.**

---

## Prompt File

- **[EVA.md](./EVA.md):** Paste as system prompt, then submit any factual claim or query for structured verification.

---

## 🚀 Quick Start

**How to use:**
1. Copy [EVA.md](./EVA.md) and paste it as the **system prompt**.
2. Submit a factual claim, statement, or question.
3. EVA automatically decides whether to search the web or rely on internal knowledge — then returns a five-part structured analysis.

**Examples:**
```
Verify this claim: "GPT-4 scores above 90% on the MMLU benchmark."
```
```
Verify this claim: "The Battle of Gettysburg concluded in July 1863."
```
```
Analyze this statement from the document I'm pasting: [paste document excerpt]
```

---

## What is EVA?

EVA is a fact verification agent built around one principle: every assertion must be traceable to explicit, verifiable evidence. It combines live web search for empirical and current claims with rigorous internal analysis for static or document-bound claims — and applies a strict evidence hierarchy to everything it touches.

When evidence is missing, it says so explicitly rather than guessing. When sources conflict, it documents both positions and applies tier hierarchy to resolve. When internal knowledge contradicts retrieved sources, the retrieved source wins.

---

## How EVA Works

### Step 0 — Pre-Flight: Search Decision Gate
Before any analysis, EVA classifies the claim along two axes:
- **Verifiability Type:** Static / Historical-settled / Historical-contested / Empirical-Current / Document-Bound
- **Staleness Risk:** Low / Medium / High

If the claim is Empirical/Current or has High Staleness Risk → web search is mandatory before analysis begins. If the claim is static or settled historical fact → internal knowledge is used and documented explicitly.

### Step 1 — Decomposition
Breaks the query into individual factual claims and formulates a precise evidence-seeking question for each.

### Step 2 — Evidence Collection
Executes targeted searches (if required), classifies sources by tier, cross-references critical claims with at least 2 independent sources where possible.

### Step 3 — Evidence Scrutiny
Every assertion must be traceable to explicit evidence. Multi-hop reasoning is documented with explicit logical bridges.

### Step 4 — Intellectual Honesty Check
Internal audit before output: any inference or assumption is flagged as `[UNVERIFIED INFERENCE]`. Knowledge conflicts between internal knowledge and retrieved sources are flagged as `[KNOWLEDGE CONFLICT]`.

### Step 5 — Structured Output
Five mandatory sections, always in this order.

---

## Evidence Hierarchy

| Tier | Label | Source Type | Treatment |
| :--- | :--- | :--- | :--- |
| **A** | Primary / Authoritative | .gov, .edu, DOI papers, official standards, primary legislation | Highest weight — cite directly |
| **B** | Professional / Reputable | Reuters, AP, established trade journals, OECD, Gartner | Cross-reference with Tier-A |
| **C** | Secondary / Contextual | Encyclopedias, textbooks, consensus summaries, verified Wikipedia | Context and framing only — facts must trace to A/B |
| **D** | Unverified / Indicative | Blogs, forums, social media | Do not use as evidence — leads only |
| **I** | Internal Knowledge | Pre-trained model knowledge | Static/Low-Staleness claims only — always documented; hard cap 65% if Staleness ≥ Medium |

**Conflict resolution:** Higher tier always wins. Tier-A overrides Tier-B; retrieved sources override internal knowledge (Tier-I).

---

## Output Structure

Every EVA response has exactly five parts:

**1. Search & Evidence Summary** *(omitted if no search was performed)*
Lists executed searches, top sources found, and any conflicts detected.

**2. Factual Assessment Table**
Per-claim breakdown with verification status, confidence score, and source tier:
- `Supported` · `Contradicted` · `Partially Supported` · `Evidence Insufficient` · `Context Required` · `Knowledge Conflict 🔴`
- Confidence: 0–100% with hard caps for single-source, internal-knowledge, and search-skipped claims

**3. Reasoning Log**
Step-by-step documentation of the Pre-Flight classification, search decisions, source tier assignments, logical bridges, inference nature, and confidence score rationale including any caps applied.

**4. Final Conclusion**
One concise statement on the overall validity of the query's premise. Unresolved conflicts are stated explicitly.

**5. Recommendation**
Weighted average confidence: *"Based on current evidence, the claim is X% likely to be accurate."*
If overall confidence < 50%, includes a concrete suggestion for what evidence would raise it.

---

## EVA vs. reClaim / VERA

| | EVA | reClaim | VERA |
| :--- | :--- | :--- | :--- |
| **Web search** | Adaptive — mandatory for empirical/current claims, optional for static/historical | Mandatory | Mandatory |
| **Primary use case** | Verifying specific claims and statements | Deep research & fact-checking | Multi-hop research with bias resistance |
| **Input** | Any factual claim, statement, or document excerpt | Research question | Research question |
| **Output** | 5-part structured analysis with weighted % | Confidence score + fact table + evidence base | Confidence score + fact table + AGoT graph |
| **Confidence model** | Weighted average of per-claim scores with hard caps | A/B/C three-axis scoring with penalty matrix | Heuristic scoring with DAG aggregation |
| **Best for** | Claim-level verification, document analysis, mixed static/current queries | Research questions requiring exhaustive sourcing | Contested multi-hop claims with bias risk |

Use EVA when you want rigorous per-claim analysis with adaptive search. Use reClaim when you need exhaustive multi-source research with a full methodology trail. Use VERA when the claim involves complex causal chains or high bias risk.

---

## Strengths & Limitations

### Strengths
- Adaptive search: searches when needed, uses internal knowledge when sufficient
- Per-claim confidence scoring with explicit calculation and hard caps
- Mandatory inference flagging — no hidden assumptions
- Knowledge conflict detection — retrieved sources override internal knowledge
- Works on any domain: history, science, law, business, technical claims, current events

### Limitations
- Search quality depends on the underlying model's web access capability
- Does not resolve contradictions between same-tier sources — documents them and lowers confidence
- Document-bound claims still require the user to provide the source material
- Best results with frontier models that follow structured output instructions reliably

---

## License
This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).  
Free to use, share, and adapt — even commercially — with attribution.
