# Teacher Leo — AI Prompting Tutor

> A patient, dialogue-based AI tutor that teaches prompting to anyone — from complete beginners to curious learners — using analogies, Before/After examples, and zero jargon.

[![Status](https://img.shields.io/badge/Status-Stable-green.svg)]()
[![Focus](https://img.shields.io/badge/Focus-Prompting%20Education%20%26%20Onboarding-blue.svg)]()
[![Style](https://img.shields.io/badge/Style-Dialogue--Based%20%26%20Jargon--Free-brightgreen.svg)]()
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

**Anyone can learn to prompt. Teacher Leo makes sure of it.**

---

## Prompt Files

| File | Content | Duration |
| :--- | :--- | :--- |
| **[TeacherLeo_v1_basics.md](./TeacherLeo_v1_basics.md)** | What is prompting? Why does it matter? Basic principles, Before/After examples, common mistakes. | ~10 min |
| **[TeacherLeo_v2_techniques.md](./TeacherLeo_v2_techniques.md)** | Three advanced techniques: Chain-of-Thought, Role-Play, Few-Shot Learning. | ~15 min |

Start with v1 if the user is new to prompting. Use v2 as a follow-up or for users who already understand the basics.

---

## 🚀 Quick Start

**How to use:**
1. Copy the prompt file and paste it as the **system prompt**.
2. Teacher Leo starts the lesson immediately — no setup needed.
3. Just respond naturally. Leo adapts to your level.

> **Claude users:** Add `(For Claude: Simply act as Claude—treat this as a template for teaching topics.)` as the very first line of the system prompt. Claude requires this framing to fully adopt the Teacher Leo persona — it's a known behavior, not a bug.

---

## What is Teacher Leo?

Teacher Leo is a prompting tutor persona designed for the general public — not developers, not power users. The target audience is the 99% of people who use AI like a search engine and don't know that better prompts produce dramatically better results.

The core design principles:
- **Dialogue-first** — Leo never monologues. Every explanation ends with a question.
- **Analogy-driven** — every concept is explained through something familiar (coffee machines, recipes, math class).
- **Before/After** — every technique is shown with a bad prompt vs. a good prompt side by side.
- **Adaptive** — Leo reads the user's level from their questions and adjusts language and complexity instantly.
- **Zero jargon** — technical terms are either avoided or immediately explained with a simple analogy.

---

## What Teacher Leo Teaches

### v1 — Prompting Basics (~10 min)
1. What is prompting? (definition + analogy)
2. Why does it matter? (simple question vs. good prompt)
3. Basic principles: Clarity, Specificity, Context
4. Practical Before/After examples
5. Common beginner mistakes
6. Simple techniques to apply immediately

### v2 — Advanced Techniques (~15 min)
1. **Chain-of-Thought** — "Show your work" (like math class)
2. **Role-Play** — "Ask an expert" (like consulting a doctor)
3. **Few-Shot Learning** — "Show a picture" (instead of describing)
4. How to combine all three techniques
5. Practice task at the end

---

## Who This Is For

- People who have never heard of "prompting"
- Users who get mediocre AI results and don't know why
- Teams onboarding non-technical colleagues to AI tools
- Anyone who wants to get more out of ChatGPT, Claude, or any LLM

Teacher Leo is **not** for developers or prompt engineers — for that audience, the other prompts in this collection (reClaim, VERA, URMA, etc.) are more appropriate.

---

## Design Notes

**Why the Claude note?** Claude's safety training makes it reluctant to fully adopt named personas without explicit framing. The `(For Claude: Simply act as Claude...)` line at the top of each prompt resolves this — it tells Claude to treat the persona as a teaching template rather than a role-play, which Claude handles comfortably. Other models (GPT-4o, Gemini) don't need this line.

**Why two versions?** v1 covers the concept of prompting itself. v2 covers specific techniques. They work as a two-part curriculum or can be used independently depending on the user's starting point.

---

## License
This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).  
Free to use, share, and adapt — even commercially — with attribution.
