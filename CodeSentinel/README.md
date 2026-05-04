# CodeSentinel v3.0 — Production-Grade Python Code Review Agent

> Authoritative, security-first Python code review with Big O analysis, PEP 8 enforcement, and structured findings.

[![Status](https://img.shields.io/badge/Status-Stable-green.svg)]()
[![Focus](https://img.shields.io/badge/Focus-Python%20Code%20Review-blue.svg)]()
[![Style](https://img.shields.io/badge/Style-Security--First%20%26%20Structured-orange.svg)]()
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

**Production-ready or not — CodeSentinel will tell you.**

---

## Prompt File

- **[CodeSentinel.md](./CodeSentinel.md):** Paste as system prompt, then submit your Python code for review.

---

## 🚀 Quick Start

**How to use:**
1. Copy [CodeSentinel.md](./CodeSentinel.md) and paste it as the **system prompt** in ChatGPT, Claude, or any frontier model.
2. Submit your Python code — snippet or full file.
3. Receive a structured review report with critical issues, performance analysis, and corrected code snippets.

**Example:**
```
Review this function:

def get_user(id):
    query = "SELECT * FROM users WHERE id = " + id
    return db.execute(query)
```

---

## What is CodeSentinel?

CodeSentinel is a Python code review agent operating at Principal Software Architect level. It is not a linter — it reasons about security, performance, and maintainability, explains every finding, and provides corrected code for every issue it raises.

The review always follows a fixed chain:
1. **Focus & Context** — sets Review Profile, Strictness, and Mechatronics Mode
2. **Diagnostic Simulation** — internal edge-case testing before output
3. **Security & Logic** — critical issues first, always
4. **Style & Idiom** — PEP 8, naming, idiomatic Python
5. **Performance** — Big O analysis, bottleneck identification
6. **Documentation** — docstring completeness and format

---

## 🛠️ New in v3.1: Advanced Diagnostics

### Focus Profiles
Tailor the review to your specific needs:
- **Profiles:** `SECURITY_FIRST`, `PERFORMANCE_FIRST`, `MAINTAINABILITY_FIRST`
- **Strictness:** `STRICT`, `BALANCED`, `RELAXED`

### Internal Diagnostic Simulation
CodeSentinel now simulates your code against critical edge cases before finalizing the report:
- Input Null/Empty handling
- Resource exhaustion (memory/loops)
- Failure propagation (system stability)

### Mechatronics Check (Optional)
A specialized mode for hardware-near Python development, focusing on:
- Resource leaks in long-running systems
- Blocking loops and real-time concerns
- Hardware-logic robustness

---

## What CodeSentinel Checks

### Security
- Command injection (`os.system` with user input)
- SQL injection (string concatenation in queries)
- Insecure deserialization (`pickle`, `yaml.load`)
- Hardcoded secrets and credentials
- Insecure dependency usage

### Error Handling
- Bare `except:` blocks — always flagged as critical
- Missing specific exception types
- Silent error swallowing

### Performance
- O(N²) loops where O(N) is achievable
- Unnecessary repeated computations
- Excessive I/O inside loops
- Big O complexity table for every reviewed function

### Style & Maintainability (PEP 8)
- Line length > 79 characters
- Naming conventions (`snake_case`, `PascalCase`)
- Whitespace around operators
- Unused imports
- Missing or incomplete docstrings (NumPy or Google style)

### Context Management
- File handles without `with` statements
- Resource leaks

---

## Output Format

Every review is structured as:

```
### Code Review Report: [description]

CRITICAL ISSUES: N
PERFORMANCE ISSUES: N
COMPLEXITY ANALYSIS: [table]
STYLE & MAINTAINABILITY ISSUES: [list]
ERROR HANDLING ISSUES: N
```

Each issue includes:
- **Finding** — what is wrong and why it matters
- **Correction** — what to change
- **Corrected Snippet** — the fixed code

---

## Scope & Limitations

**CodeSentinel does:**
- Review Python code for security, performance, style, and documentation
- Explain every finding with a principle reference (security, PEP 8, etc.)
- Provide corrected code for every issue

**CodeSentinel does not:**
- Suggest proprietary or non-public libraries
- Provide system design advice beyond the submitted code
- Alter core business logic unless a critical security flaw requires it

---

## Target Audience

Mid-to-Senior Software Engineers who want rigorous, production-focused feedback — not a style checker, but a full review from a security-aware architect perspective.

---

## License
This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).  
Free to use, share, and adapt — even commercially — with attribution.
