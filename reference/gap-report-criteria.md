# Gap Report Criteria

Quick reference for when and how to produce a gap report. For full decision logic, see rules.md.

---

## When to produce a gap report

Produce a gap report when one or more steps carry a **Provisional** classification. The gap report is a separate markdown file saved alongside the HTML map in `output/`.

## When not to produce a gap report

Do not produce a gap report when all steps are classified **Confident** or **Conditional**. The absence of a gap report is a meaningful signal: the audit was thorough enough for the operator to commit.

Conditional classifications do not trigger a gap report. Conditional means the judgment layer is visible but the correct classification depends on an organizational variable — that's a decision for the team, not missing information.

---

## Two types of gaps

### Blocking gaps

Prevent confident classification. The operator cannot determine the right classification because the evidence isn't there.

**Signals:**
- Judgment layer entirely absent for a step
- No information about what happens when the step goes wrong
- The audit says "this step is important" but cannot explain what it produces or who uses the output
- Handoffs or escalation paths referenced but not described
- The step's relationship to the workflow outcome is unclear

**Gap report language:** "Cannot classify this step confidently. Missing: [specific information]. This is a blocking gap — the classification could change substantially with this information."

### Sharpening gaps

Would increase confidence or precision but don't prevent classification. The operator can make a reasonable call, but acknowledges it might shift with better information.

**Signals:**
- Judgment layer is present but thin — one-line answers where more detail would help
- Breakdowns described but root causes not diagnosed
- Quality standard implied but not explicitly stated
- "It depends" answers without specifics on what it depends on
- Handoffs mentioned but the nature of the dependency isn't clear

**Gap report language:** "Classified as [X] based on available evidence. This would sharpen with: [specific information]. The classification is unlikely to change category but may shift in scope or confidence."

---

## Writing actionable gap entries

Each gap entry should read as a prompt the user can act on — something they can take to a practitioner and ask. Avoid abstract descriptions.

**Weak:** "The judgment layer for this step is incomplete."
**Strong:** "What does an experienced person check before approving content that a new person would miss? What makes them send something back vs. let it through?"

**Weak:** "Quality standards are not documented."
**Strong:** "What's the difference between content that gets approved on the first round and content that goes through three revision cycles? Is there a pattern?"

**Weak:** "Escalation paths are unclear."
**Strong:** "When a review stalls or a stakeholder disagrees with the direction, what happens? Who decides, and based on what?"

---

## When the gap pattern is diagnostic

If the judgment layer is absent across most or all steps, that is not a collection of individual gaps. It is a finding.

State this directly at the top of the gap report: "The judgment layer is absent or thin across [X of Y] steps. This suggests the workflow has not been made visible enough for AI opportunity mapping. The gap report below identifies what to surface for each step, but the broader finding is that a structured audit — not a process description — is needed before this map can be trusted."

This is the operator enforcing the missing middle framework: you cannot map AI opportunity on a workflow you can only see the surface of.

---

## Gap report structure

```
# Gap Report: {Workflow Name}

## Summary
- Steps assessed: X
- Provisional classifications: Y
- Blocking gaps: Z
- Sharpening gaps: W

[If diagnostic pattern detected:]
**Finding:** The judgment layer is absent or thin across [X of Y] steps...

## Step: {Step Name}
**Current classification:** {classification} (Provisional)
**Gap type:** Blocking / Sharpening

**What's missing:**
- [Specific missing information, written as an actionable prompt]

**Why it matters:**
- [How this gap affects the classification — what might change]

[Repeat per Provisional step]
```

---

## Relationship to the HTML map

The gap report is a separate file. The HTML map shows Provisional badges on affected steps with brief inline pointers (e.g., "This classification is provisional — see gap report for what's missing"). The full gap analysis lives in the markdown file, not the map.

This separation is intentional. The map is the presentation artifact. The gap report is the working document. When the user addresses the gaps and re-runs the operator, the new map should come out cleaner — fewer Provisional badges, smaller or absent gap report.
