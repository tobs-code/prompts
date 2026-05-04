# ROVA v2 — Robotics Output Validation Agent

> Multi-layer safety validation for LLM outputs destined for robotic execution — with configurable constraints, IAS consensus scoring, and hard-fail/self-correction logic.

[![Status](https://img.shields.io/badge/Status-Stable-green.svg)]()
[![Focus](https://img.shields.io/badge/Focus-Robotics%20Safety%20%26%20Output%20Validation-blue.svg)]()
[![Style](https://img.shields.io/badge/Style-Safety--First%20%26%20Non--Bypassable-red.svg)]()
[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

**Never send an unvalidated command to a robot.**

---

## Prompt File

- **[ROVA.md](./ROVA.md):** Paste as system prompt. Configure your robot's constraints at the top, then submit commands for validation.

---

## 🚀 Quick Start

1. Copy [ROVA.md](./ROVA.md) and paste it as the **system prompt**.
2. Set your robot's constraints in the configuration block at the top:

```
[ROVA Configuration]
MAX_VELOCITY:   2.0 m/s
JOINT_LIMITS:   [-170°, 170°]
OUTPUT_FORMAT:  YAML
DEFAULT_HOME:   [0, 0, 90, 0, 90, 0]
```

3. Submit any robotics command or request. ROVA validates it through 4 layers and returns either a validated output or a structured error report.

**Example:**
```
Move the end-effector to joint angles (45, -20, 90, 0, 0, 0) at nominal speed.
```

---

## What is ROVA?

ROVA is a safety validation layer that sits between an LLM and a robotic execution system. It intercepts every output, runs it through a multi-layer validation protocol, and either releases it as `<ROVA_VALIDATED_OUTPUT>` or blocks it with a `<ROVA_VALIDATION_ERROR>` — never silently passing unsafe commands.

The key design principle: **validation is non-bypassable**. Every output goes through all layers, every time.

---

## How It Works

### Execution Sequence

```
User Request
    ↓
Layer 0: IAS Pre-Check (consensus + risk scoring)
    ↓ [HALT if consensus < 0.5 or risk > 0.7]
Layer 1: Intent & Domain Check
    ↓
Layer 2: Safety & Syntax Validation
    ↓ [HARD-FAIL: safety violations, natural language]
Layer 3: Self-Correction (if eligible) → Final Output or Error Report
```

### Layer 0 — IAS Module (Internal Simulation & Assessment)
Before each layer, ROVA runs a 4-perspective internal consultation:

| Perspective | Default Weight | Focus |
| :--- | :--- | :--- |
| Security | 0.30 | Injection risks, unauthorized access |
| Efficiency | 0.20 | Minimal computation, shortest command path |
| Robustness | 0.20 | Edge cases, parameter completeness |
| Integration | 0.30 | Schema compatibility, API alignment |

Weights adjust dynamically based on context (emergency stop, path planning, tool operation, diagnostics) and are re-normalized after each adjustment. If `weighted_consensus < 0.5` or `assessed_risk > 0.7` → immediate HALT.

### Layer 1 — Intent & Domain Check
Identifies the task type and maps it against configured constraints (MAX_VELOCITY, JOINT_LIMITS, SAFETY_ZONES).

### Layer 2 — Safety & Syntax Validation
Three checks:
1. **Syntax** — output must match configured OUTPUT_FORMAT (JSON/YAML/XML). Natural language = HARD-FAIL.
2. **Safety** — no violations of MAX_VELOCITY, JOINT_LIMITS, or SAFETY_ZONES. Violations = HARD-FAIL.
3. **Completeness** — all required parameters present.

### Layer 3 — Self-Correction & Final Output
- **Eligible for self-correction:** Missing parameters (uses configured defaults), wrong format (reformats to correct schema).
- **Hard-fail — no correction:** Safety violations, natural language output.
- Corrected outputs are re-verified through Layer 2 before release.

---

## Configuration

All constraints are set in the configuration block at the top of the prompt. Key parameters:

| Parameter | Description | Example |
| :--- | :--- | :--- |
| `MAX_VELOCITY` | Maximum TCP/joint velocity | `1.5 m/s` |
| `JOINT_LIMITS` | Per-axis angle limits | `[-180°, 180°]` |
| `SAFETY_ZONES` | Restricted workspace zones | `[]` |
| `OUTPUT_FORMAT` | Expected command format | `JSON` / `YAML` / `XML` |
| `TOOL_IDS` | Valid tool identifiers | `["gripper_1", "tool_2"]` |
| `NOMINAL_SPEED` | Default speed profile label | `"nominal"` |
| `DEFAULT_HOME` | Default home joint configuration | `[0,0,0,0,0,0]` |

Override at runtime: `/set MAX_VELOCITY: 2.0`

---

## Output Format

Every response is exactly one of:

```xml
<ROVA_VALIDATED_OUTPUT>
  [machine-readable command in configured format]
</ROVA_VALIDATED_OUTPUT>
```

or

```xml
<ROVA_VALIDATION_ERROR>
  <violation_phase>...</violation_phase>
  <violated_parameter>...</violated_parameter>
  <constraint_violated>...</constraint_violated>
  <output_rejected>...</output_rejected>
  <guidance>...</guidance>
</ROVA_VALIDATION_ERROR>
```

Nothing else. No preamble, no explanation outside these blocks.

---

## Strengths & Limitations

### Strengths
- Non-bypassable validation — every output goes through all layers
- Configurable constraints — adapts to any robot platform
- Hard-fail/self-correction distinction — safety violations are never "corrected around"
- Structured error reports — machine-readable, actionable
- IAS consensus scoring — catches ambiguous or high-risk requests before they reach execution

### Limitations
- Constraint values are only as good as the configuration — incorrect setup leads to incorrect validation
- Does not have access to real-time robot state (joint positions, sensor data) — relies on provided context
- Self-correction uses defaults, not live system state — verify corrected outputs before execution
- Best results with frontier models that reliably follow complex multi-layer instructions

---

## Target Audience

- Robotics researchers using LLMs for command generation
- Industrial automation engineers integrating AI into control pipelines
- Safety engineers validating LLM outputs before robotic execution
- Anyone building LLM-to-robot interfaces who needs a structured safety layer

---

## License
This work is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).  
Free to use, share, and adapt — even commercially — with attribution.
