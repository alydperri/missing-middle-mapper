# Gap Report: Internal Content Approval Process

## Summary

- Steps assessed: 5
- Provisional classifications: 1 (Step 2: Editorial Review)
- Blocking gaps: 0
- Sharpening gaps: 3

The workflow is classifiable at the macro level. The single Provisional step (Editorial Review) is directionally clear — Augment + Keep Human — but the audit gives thin answers in the judgment layer where richer ones would significantly change what the Augment opportunity looks like in practice. No blocking gaps prevent classification; three sharpening gaps would increase confidence and precision.

Skills assessment for Step 2 is deferred until gaps are addressed. The pre-review triage and author revision augmentation recommendations are directionally valid but cannot be scoped precisely without the information below.

---

## Step 2: Editorial Review

**Current classification:** Augment + Keep Human (Provisional)

---

### Gap 1: What does the editorial judgment actually vary by content type?

**Gap type:** Sharpening

**What's missing:**

The audit says "different content types need different levels of review" but cannot describe what those differences are. Blog posts, customer emails, social posts, and partner communications presumably get different treatment — but the criteria for each aren't captured anywhere, including in this audit.

Specifically missing:
- What does the editor check first on a blog post vs. a customer email? What gets less scrutiny on social?
- What's the threshold for "send back" vs. "fix inline and pass"? Does it differ by content type?
- What are the most common reasons a draft fails review for each content type?

**Actionable prompt to take to the editor:**

> "Walk me through the last three drafts you sent back for revision. What was wrong with each one? Now walk me through three you approved quickly. What made those easy? Is the pattern different for blog posts vs. customer emails vs. social?"

**Why it matters:**

The Augment recommendation (AI pre-review against documented standards) can only be scoped once we know what the standards are per content type. Right now the recommendation is "AI checks against the style guide" — which is the mechanical layer. Whether AI can do more (e.g., check for exec-messaging alignment, flag sensitivity signals) depends on whether those criteria can be documented. This gap determines how much of the editorial review can be systematically supported vs. how much must stay with the editor's judgment.

---

### Gap 2: What makes editorial feedback actionable vs. vague?

**Gap type:** Sharpening

**What's missing:**

The audit notes that "the feedback isn't always clear on what needs to change" — but doesn't describe the pattern. What kinds of feedback are too vague? What would make them specific? Is this a format problem (comments in a document), a medium problem (verbal vs. written), or a criteria problem (the editor doesn't have language to articulate what's wrong)?

Specifically missing:
- What does vague editorial feedback look like in practice? An example or two would help.
- What would a well-formed revision request contain? Does a template or format exist anywhere?
- When feedback leads to a second round of revision that still misses the point, what usually happened?

**Actionable prompt to take to the editor:**

> "When you send something back and the author comes back with a revision that still doesn't address it, what went wrong? Can you show me an example of feedback you wrote that was clear vs. one that wasn't? What would have made the unclear one better?"

**Why it matters:**

The revision cycle problem (Step 3) is downstream of this gap. If the editor's feedback format is the root cause of multiplying revision rounds, then the fix is a structured feedback template — not author-side AI revision assistance. If the criteria are clear but authors are missing them, then AI assistance for authors is well-targeted. These are different solutions. This gap determines where the intervention should land.

---

### Gap 3: What triggers comms lead involvement in editorial review?

**Gap type:** Sharpening

**What's missing:**

The audit says "sometimes the comms lead" reviews sensitive pieces, but "sensitive" is undefined. The criteria that determine when a second reviewer enters the editorial pass aren't documented.

Specifically missing:
- What content characteristics cause the editor to pull in the comms lead during editorial review (as opposed to waiting for approval)?
- How often does this happen — is it every launch week, specific content types, topics involving certain stakeholders?
- When the comms lead reviews a piece the editor already reviewed, do they typically find new issues, or are they confirming the editor's judgment?

**Actionable prompt to take to the comms lead:**

> "When do you get pulled into an editorial review before the piece goes to formal approval? What's the pattern — is it the topic, the channel, the author, the timing? And when you review something the editor has already seen, are you usually agreeing with the editor's judgment or changing direction?"

**Why it matters:**

If the comms lead's editorial involvement follows a pattern, that pattern could be documented and used to flag content for dual review automatically — removing the informal "editor's discretion" routing that currently governs it. If the comms lead frequently changes direction from the editor, that's a signal that the editorial criteria differ between the two, which is a training and alignment problem, not an AI opportunity. This gap affects whether the editorial review can be decomposed into a more predictable process.
