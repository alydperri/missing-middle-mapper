# Audit Quality Checklist

Use this checklist to assess the quality of a workflow audit before classifying. The audit quality determines what the operator can produce: a confident map, a provisional map with gap report, or a structural finding.

---

## Workflow-level checks

Run these first. If the workflow-level framing is missing or broken, step-level assessment may not be warranted.

| Check | Present | Signal if missing |
|---|---|---|
| Workflow name and scope defined | ☐ | Minor — can usually infer from steps |
| Outcome articulated in specific, measurable terms | ☐ | **Critical.** Vague outcome ("keep people informed," "support the team") triggers the escalation rule. Flag before classifying. |
| Frequency / cadence stated | ☐ | Helpful for prioritization but not blocking |
| Owner identified | ☐ | Useful context but not blocking |
| Definition of "good" — what the workflow looks like when it runs well | ☐ | Important. Without this, measurement baseline is speculative. |

**Escalation trigger:** If the outcome field is missing or vague, flag this to the user before attempting step-level classification. An undefined outcome means every downstream classification is speculative.

---

## Workflow value checks

These inform prioritization. Not blocking for classification, but affect the output's contextual guidance.

| Check | Present | Signal if missing |
|---|---|---|
| Consequence of failure — what happens if this workflow breaks? | ☐ | Can't assess organizational impact. Note that value data wasn't provided. |
| Scale — how many people/teams/customers affected? | ☐ | Can't gauge reach of improvement. |
| Time cost — aggregate hours per cycle across all roles | ☐ | Can't quantify current cost or potential savings. |
| Strategic relevance — connected to leadership priorities? | ☐ | Helpful for prioritization, not blocking. |
| Delight potential — would improvement be felt by practitioners? | ☐ | Helps predict adoption and transformation momentum. |

**Assessment rule:** If all five value fields are present, the operator includes a value context section in the HTML output. If value data is absent, the operator maps without it and notes that prioritization data wasn't provided. Value data never blocks classification — it contextualizes it.

**Low-impact signal:** If the consequence of failure is low, scale is small, and delight potential is minimal, include a contextual note in the output: the AI opportunities are real, but a higher-impact workflow might produce better returns.

---

## Per-step checks: formal layer

These establish the basic structure. If these are missing, the input is a description, not an audit.

| Check | Present | Signal if missing |
|---|---|---|
| Step name | ☐ | Can't map without it |
| What triggers the step | ☐ | Sharpening gap — helps identify handoff points |
| What the step produces | ☐ | Important — unclear output means unclear value |

---

## Per-step checks: judgment layer

This is the critical layer. Its presence or absence determines whether a step can be classified confidently.

| Check | Present | Signal if missing |
|---|---|---|
| What a new person would get wrong that an experienced person wouldn't | ☐ | **Key signal.** If answered substantively, the judgment layer is visible. If blank or vague, it's not. |
| What information is used that isn't written down | ☐ | Surfaces tacit knowledge — the core of the missing middle |
| What causes breakdowns when the step goes badly | ☐ | Critical for classification. Breakdown patterns drive Automate vs. Augment vs. Stop / Rethink. |
| Who else is involved and what's needed from them | ☐ | Surfaces handoffs, dependencies, and relationship-dependent judgment |

**Assessment rule:** If two or more judgment layer questions are blank or answered with "it depends" (without specifics), the step is Provisional. If all four are blank, the step has no visible judgment layer — it cannot be classified confidently regardless of how well the formal layer is documented.

---

## Per-step checks: classification signal layer

These provide the data that tips classification in one direction or another.

| Check | Present | Signal if missing |
|---|---|---|
| Checklist vs. judgment — can someone follow a checklist, or does it require judgment? | ☐ | Key Automate vs. Augment signal |
| Output consistency — does this step produce reliable output? | ☐ | Inconsistency signals judgment variance or broken process |
| Error cost — what happens if this step is done wrong? | ☐ | Drives Keep Human vs. Augment threshold |
| Bottleneck status — does this step slow the workflow down? | ☐ | Prioritization signal, not classification-blocking |
| Friction — what parts are tedious, time-consuming, or unpleasant? | ☐ | Direct classification signal: tedious/repetitive → Automate, cognitively heavy → Augment, pointless → Stop / Rethink, difficult but meaningful → Keep Human |

---

## Per-step checks: current AI usage

When present, this enables the operator to assess existing AI usage alongside forward-looking classification.

| Check | Present | Signal if missing |
|---|---|---|
| Whether AI is currently used in this step | ☐ | Can't assess existing usage. Operator classifies forward only (default). |
| What tool and what it does | ☐ | Can't evaluate fit. Status defaults to "not yet applied." |
| How the person reviews/checks AI output | ☐ | Can't assess review quality. If AI is mentioned but review isn't described, flag as "needs guardrails" by default. |

**Assessment rule:** If AI usage is mentioned anywhere in the step (even in other fields, not just the AI usage question) but the review process isn't described, the operator defaults to "In use — needs guardrails" and flags the missing review layer as a risk.

---

## Audit quality tiers

### Complete audit

All workflow-level checks present. Judgment layer visible for every step (at least three of four questions answered substantively per step). Classification signals present. Breakdowns documented with specific patterns.

**Operator output:** Confident map. No gap report.

### Partial audit

Workflow-level framing is present and outcome is clear. Judgment layer is visible for some steps but thin or absent for others. Classification signals may be uneven.

**Operator output:** Mixed confidence map — Confident on well-documented steps, Provisional on thin steps. Gap report produced for Provisional steps.

### Process description (not an audit)

Step names and descriptions are present, but judgment layer is absent across most or all steps. No breakdowns documented. No quality standards. The input reads like a process document, not an audit.

**Operator output:** All steps Provisional. Gap report functions as an audit guide — tells the user what to go find out per step. The gap pattern itself is a diagnostic finding.

### Broken workflow audit

Formally complete, but the content reveals a broken workflow. Signals: vague outcome, breakdowns at every step, steps that can't articulate why they exist, cosmetic quality standards, outputs no one acts on.

**Operator output:** Structural finding. Stop / Rethink dominant. Automation trap rule applied at workflow level. Recommendation to clarify purpose before redesigning.

---

## Quick decision tree

```
1. Is the workflow outcome defined and specific?
   NO  → Flag escalation. Do not classify until user has seen this.
   YES → Continue.

2. Is the judgment layer visible for this step?
   YES (3-4 questions answered substantively) → Confident classification possible.
   PARTIAL (1-2 questions answered) → Provisional. Gap report entry.
   NO (all blank or "it depends") → Provisional. Blocking gap.

3. Is the breakdown pattern local or structural?
   LOCAL (1-2 steps) → Stop / Rethink those steps. Map the rest.
   STRUCTURAL (most/all steps) → Workflow-level finding. Automation trap applies globally.
```
