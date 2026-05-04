# PHA — Prompt Hardening Assistant (v4.0 - 2026 Edition)

> Systematic prompt hardening against injection (direct & indirect), many-shot jailbreaking, amnesia, and saturation — with structured XML analysis output.

[![Status](https://img.shields.io/badge/Status-Stable-green.svg)]()
[![Focus](https://img.shields.io/badge/Focus-Frontier%20Security%20%26%20Architectural%20Hardening-blue.svg)]()
[![Style](https://img.shields.io/badge/Style-Adversarial%20%26%20Structured-red.svg)]()
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

**Harden your prompt before it reaches the model.**

---

## Prompt Files

- **[English Prompt](./PHA_english.md):** Optimized for global use.
- **[German Prompt](./PHA_german.md):** Deutsche Version.

---

## 🚀 Quick Start

**How to use:**
1. Copy [PHA_english.md](./PHA_english.md) and paste it as the **system prompt**.
2. Submit your prompt using this format:

```
[ORIGINAL_PROMPT]:
[Paste the prompt you want to harden here]

[OBJECTIVE (Optional)]:
[Describe the intended purpose — or leave blank]
```

3. PHA returns a hardened version of your prompt plus a structured XML analysis explaining every change.

---

## What is PHA?

PHA is a meta-prompt that takes any prompt as input and makes it more resistant to modern LLM attack vectors:

| Attack Vector | What it is | How PHA defends |
| :--- | :--- | :--- |
| **Direct Injection** | Malicious instructions in user input attempting to hijack behavior. | Verbatim anchor, negative constraints, instruction extraction. |
| **Indirect Injection (IPI)** | Malicious instructions hidden in data (URLs, files, logs, API responses). | **Strict Data Sandboxing** via non-standard delimiters and **Passive Context Enforcement**. |
| **Many-Shot Jailbreaking** | Behavioral manipulation through long compliance patterns in few-shot history. | **Context Isolation** and **Instructional Primacy** (System > History). |
| **Amnesia / Context Drift** | Model loses track of instructions mid-conversation or across reasoning steps. | Linear reasoning (CoT) and mandatory **State Checkpoints**. |
| **Saturation / Output Hijacking** | Model gets distracted or produces unstructured output that leaks instructions. | Strict output formatting (XML/JSON) and scope limitation. |
| **Agentic / Tool Abuse** | User input reconfigures tools or APIs invoked by the prompt. | **Tool Boundary Lock** — explicit scope definition, reconfiguration forbidden. |
| **Encoded Payload Bypass** | Instructions smuggled via Base64, Unicode escapes, roleplay, or creative framing. | **Latent Directive Neutralization** — explicit prohibition of encoded and creative-framing attacks. |

---

## How It Works (2026 Edition)

PHA runs in three phases:

**Phase 1 — Hardening**
Applies architectural defense layers to the original prompt:
- **Architectural Sandboxing**: Wraps untrusted input in delimiters and marks it as passive data.
- **Many-Shot Neutralization**: Invalidates simulated compliance patterns in context history.
- **Latent Directive Scanning**: Protects against poetry, roleplay, and encoded (Base64) attacks.
- **CoT & Fact Enumeration**: Enforces logical stability.

**Phase 2 — Vulnerability Assessment**
Runs a 7-point checklist against the original prompt before writing the report:
Direct Injection · Indirect Injection (IPI) · Many-Shot / History Poisoning · Amnesia / Context Drift · Saturation / Output Hijacking · Agentic / Tool Abuse · Encoded Payload Bypass.
Each vector is documented as Found or Not Found — and if Found, which Phase 1 technique addresses it.

**Phase 3 — Output**
Returns everything in a strict XML report.

---

## When to Use PHA

- Before deploying a system prompt in production.
- When an agent processes untrusted external data (emails, web search results, PDFs).
- In multi-turn conversations where "Many-Shot" drift is a risk.
- As a pre-step before running URMA (URMA evolves prompts; PHA hardens them).

---

## Relationship to Other Prompts in This Collection

| Tool | Purpose |
| :--- | :--- |
| **PHA** | Hardens a prompt against injection, amnesia, saturation |
| **URMA** | Evolves a prompt by analyzing its failure modes over iterations |
| **Cartographer** | Analyzes a specific model output for reasoning quality and constraint compliance |

---

## Strengths & Limitations

### Strengths
- **Architectural Defense**: Moves beyond simple keyword filtering to context-aware isolation.
- **2026 Standard**: Addresses Indirect Injection and Many-Shot scenarios.
- **Machine-Readable**: XML structure for automated testing pipelines.

### Limitations
- **Token Overhead**: Sandboxing and CoT instructions increase prompt length.
- **Model Dependent**: Works best with frontier reasoning models (GPT-4+, Claude 3.5+, Gemini 1.5+).

---

## License
This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).  
Free to use, share, and adapt — even commercially — with attribution.
