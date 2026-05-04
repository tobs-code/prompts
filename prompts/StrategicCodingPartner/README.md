# Strategic Coding Partner — Hierarchical Cognitive Framework

> An autonomous development agent with structured strategic planning, multi-perspective tactical consultation, and research-first execution — built for complex software tasks.

[![Status](https://img.shields.io/badge/Status-Stable-green.svg)]()
[![Focus](https://img.shields.io/badge/Focus-Autonomous%20Development%20%26%20Strategic%20Planning-blue.svg)]()
[![Style](https://img.shields.io/badge/Style-HGD%20%7C%20IAS%20%7C%20RRC%20Framework-orange.svg)]()
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

**Think like a senior engineer. Plan before acting. Complete what you start.**

---

## Prompt File

- **[StrategicCodingPartner.md](./StrategicCodingPartner.md):** Paste as system prompt in any frontier model or coding assistant.

---

## 🚀 Quick Start

1. Copy [StrategicCodingPartner.md](./StrategicCodingPartner.md) and paste it as the **system prompt**.
2. Describe your task — the agent will decompose it into phases, consult its internal perspectives, and execute with full transparency.

**Example:**
```
Implement a user export feature with CSV download, admin-only access, and PII filtering.
```

---

## What is the Strategic Coding Partner?

A general-purpose autonomous development agent built around a three-layer cognitive framework. It doesn't just execute — it plans, consults, verifies, and learns. Every decision is documented in a `[META]` block so you can see exactly why the agent is doing what it's doing.

The core principle: **Research first, act second, complete task chains fully.**

---

## The Three Layers

### Layer 1 — HGD: Strategic Planning
Decomposes any task into a logical phase sequence with a confidence score. If confidence drops below 0.5, it stops and asks rather than guessing.

Built-in mission templates:
- Bug Fix · New Feature · Refactoring · Performance · Security Audit

### Layer 2 — IAS: Tactical Consultation
Before each phase, simulates an internal 4-perspective consultation:

| Perspective | Focus |
| :--- | :--- |
| Security | Risks, vulnerabilities, access control |
| Efficiency | Fastest path, minimal overhead |
| Robustness | Edge cases, failure handling |
| Integration | Compatibility, existing system fit |

Weights adjust dynamically based on context (security audit → security weight increases) and are re-normalized. If consensus < 0.5 or risk > 0.7 → escalates to user.

### Layer 3 — RRC: Research, Review, Commit
Four-step execution protocol:
1. **Discovery** — research internal docs, code, and external sources before acting
2. **Verification** — confirm understanding, check for blockers
3. **Execution** — 3-stage risk check before any autonomous action
4. **Learning** — update docs, note insights

**3-Stage Risk Check (all must pass for autonomous execution):**
- Level 1: HGD confidence ≥ 0.5
- Level 2: IAS consensus ≥ 0.5 AND risk < 0.7
- Level 3: Research complete AND no blockers

---

## Key Behaviors

**Trust Code Over Docs**
When documentation conflicts with the actual code, the code wins. Docs describe intent; code describes reality.

**Complete Task Chains**
If Task A reveals Problem B, both get fixed before marking anything done. No partial completions.

**Transparent [META] Blocks**
For complex tasks, the agent outputs a monitoring block showing current confidence, consensus, risk, and whether it's acting autonomously or asking for input.

**Research-First**
No action without a research basis. The agent checks existing code, docs, and external sources before making decisions.

---

## When It Asks vs. Acts Autonomously

**Acts autonomously when:**
- Research → Implementation (task implies action)
- Discovery → Fix (problem found, cause understood)
- Phase → Next Phase (chain complete)
- Error → Solution (cause understood)

**Stops and asks when:**
- Requirements are unclear
- Multiple valid architectural paths exist
- Security or risk concerns arise
- Any confidence level is too low
- Action has irreversible consequences (deploys, deletions, secrets)

---

## Optional: Framework Health Tracking

If you have a memory system (e.g., a note-taking tool or MCP memory server), the agent can track session health metrics:

```
Framework Health = mean(HGD confidence, IAS consensus, 1 - IAS risk, RRC confidence)

🟢 HEALTHY ≥ 0.7 | 🟡 DEGRADED 0.6–0.69 | 🔴 CRITICAL < 0.6
```

Without a memory system: the agent focuses on updating documentation instead.

---

## Strengths & Limitations

### Strengths
- Structured decision-making — no silent assumptions
- Dynamic risk assessment adapts to context
- Full transparency via [META] blocks
- Research-first prevents premature action
- Works for any software task — not domain-specific

### Limitations
- More verbose than a simple assistant — the [META] blocks add overhead for trivial tasks
- Confidence scores are heuristic estimates, not ground truth
- Best results with frontier models (Claude, GPT-4o) that reliably follow multi-layer instructions
- For very simple one-liner tasks, the framework overhead may feel excessive

---

## License
This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).  
Free to use, share, and adapt — even commercially — with attribution.
