# Rules

This file contains the complete decision logic for the Missing Middle Mapper. Every classification, confidence assessment, gap report, and output decision traces back to a rule defined here.

---

## First action: assess the audit

Before classifying anything, read the entire audit and answer four questions:

1. **Can the audit articulate the outcome the workflow is meant to drive?** If the outcome is missing or vague ("keep people informed," "support the team"), flag this immediately. Do not attempt step-level classification until the user has seen this flag. An undefined outcome means every classification downstream is speculative.

2. **Does the audit surface the judgment layer for each step?** The judgment layer is the implicit knowledge that experienced practitioners use but rarely document: what a new person would get wrong, what information isn't written down, what causes breakdowns, where handoffs depend on relationships. If the judgment layer is thin or absent for a step, that step cannot receive a Confident classification.

3. **Is the breakdown pattern local or structural?** If breakdowns cluster at one or two steps, the problem is likely executional — those steps need redesign. If breakdowns appear at every step, or if multiple steps cannot articulate why they exist, the problem is likely definitional. The workflow itself may need to be rethought before any AI opportunity mapping makes sense.

4. **Is this workflow worth investing in?** If the audit includes workflow value data (consequence of failure, scale, time cost, strategic relevance, delight potential), assess whether the workflow is a strong candidate for AI redesign. This is not a gate — the operator still maps whatever it receives. But value context changes the output:
   - **High-impact workflow:** The opportunity map carries a stronger signal. Improvements here move a metric that matters. Note this in the output.
   - **Low-impact workflow:** The operator maps it honestly but includes a contextual note: "The AI opportunities identified here are real, but the workflow's organizational impact is limited. Consider whether a higher-impact workflow would produce better returns on redesign effort."
   - **Value data absent:** The operator maps without a value assessment and notes that prioritization data wasn't provided. No assumption in either direction.

---

## The four classifications

### Automate

The task is repetitive, rule-followable, and low-stakes. A checklist or decision tree could govern it. Error is recoverable, and the cost of getting it wrong is low relative to the cost of doing it manually every time.

**Triggering signals in the audit:**
- The step produces consistent output regardless of who performs it
- The audit describes the step in terms of actions, not decisions
- Breakdowns are caused by volume, inconsistency, or forgetting — not by misjudgment
- The judgment layer for this step is thin because judgment genuinely isn't required, not because it wasn't captured
- The step currently slows the workflow down due to repetition, not complexity
- Friction is described as tedious, repetitive, or draining due to volume — the work itself isn't hard, there's just too much of it

**Disqualifying signals:**
- The step involves reading context that changes case-by-case
- Error is difficult to detect after the fact or expensive to reverse
- The audit uses language like "it depends," "you have to know," or "experience matters" for this step
- The same sub-element is classified Stop / Rethink (see automation trap rule below)

**Common multi-label pairings:**
- Automate + Keep Human: the mechanical parts of the step are automatable, but a human decision gate exists within the same step (e.g., intake form routing is automatable, but the decision to accept the request is human-owned)
- Automate + Augment: parts of the step can run unattended while other parts benefit from AI-assisted judgment

### Augment

The task depends on judgment, but AI can amplify that judgment rather than replace it. AI can prompt better questions, surface relevant context, draft from established principles, check for missed considerations, flag risks, or accelerate the parts of the step that don't require the practitioner's full attention.

**Triggering signals in the audit:**
- The judgment layer is visible and the decisions are articulable — even if complex
- Breakdowns are caused by inconsistency, missed context, or variation in practitioner skill, not by the task being fundamentally unclear
- The step would benefit from a "second set of eyes" or a structured prompt
- Quality standards exist (or could be defined) that AI could check against
- The audit reveals that experienced practitioners have internalized principles that could be externalized
- Friction is described as cognitively heavy — requiring too much context-holding, too many considerations to track, or too much switching between sources

**Disqualifying signals:**
- The judgment involved depends on live relationship dynamics, emotional context, or trust that cannot be captured in an audit
- The step requires taste or aesthetic judgment that resists codification — the practitioner cannot explain why one output is better, only that it is
- The cost of AI producing a plausible-but-wrong output is high and the error would be hard to catch

**Common multi-label pairings:**
- Augment + Keep Human: AI assists with part of the step (drafting, checking, surfacing) while a human retains the final call. This is the most common pairing.
- Augment + Automate: some sub-tasks within the step are fully automatable while others benefit from AI-assisted judgment

### Keep Human

The task depends on relationship, taste, contextual judgment, or stakes that mean it cannot be safely delegated to AI — even in an assistive role. The value of the step comes from human presence, human accountability, or human judgment that resists codification.

**Triggering signals in the audit:**
- The step involves navigating relationships, building trust, or reading emotional cues
- The judgment layer reveals "taste" — decisions where the practitioner can identify quality but cannot fully explain the criteria
- Error is high-stakes, hard to detect, or irreversible
- The step serves a governance function: it exists so a human is accountable for the outcome
- The audit describes the step in terms of "knowing when," "sensing," or "reading the room"
- Friction is described as difficult but meaningful — the practitioner finds it hard but recognizes it as where they add the most value. This is an inverse signal: it reinforces Keep Human rather than pointing toward automation

**Disqualifying signals:**
- The step can be fully described as a sequence of actions with clear criteria
- The "human judgment" described in the audit is actually pattern recognition that AI handles well (e.g., categorization, anomaly detection)
- The step is classified Keep Human only because no one has tried to articulate the judgment — not because the judgment resists articulation. In this case, the classification is Provisional, not Confident.

### Stop / Rethink

The step exists by habit, inertia, or unclear mandate. The audit reveals that no one can articulate why it creates value, or the breakdown pattern suggests the problem is structural rather than executional. Redesigning or automating this step would preserve or scale a problem rather than solve one.

**Triggering signals in the audit:**
- The step cannot articulate its purpose in terms of a specific outcome or decision it enables
- Breakdowns at this step are described as "it's always been this way" or "no one really uses the output"
- The same work is being done in multiple places with no coordination
- The quality standard for this step is cosmetic ("it looks complete") rather than substantive ("it enables X decision")
- The judgment layer reveals that practitioners skip or shortcut this step without consequence
- Follow-up or downstream action from this step rarely happens
- Friction is described as pointless or resentful — the practitioner finds the work painful and cannot articulate what value it creates. "I do this but I'm not sure why" is a strong Stop / Rethink signal

**Disqualifying signals:**
- The step has a clear purpose and measurable output, even if the execution is poor. Poor execution is a redesign problem, not a Stop / Rethink problem.
- The step is important but under-documented. That's a gap report issue, not a reason to recommend stopping.

---

## The automation trap rule

**Stop / Rethink and Automate are mutually exclusive on the same sub-element.**

This rule operates at three scopes:

**Sub-task level (default):** If a sub-element of a step is classified Stop / Rethink, that same sub-element does not also receive Automate. You do not automate the broken thing. Automating a practice that exists by habit or unclear mandate scales the problem.

**Step level:** Automate and Stop / Rethink can coexist on the same step when they refer to different sub-elements. For example, Content Development might have Automate (first-draft generation from design docs) and Stop / Rethink (rebuilding content from scratch when reusable assets exist) — those are different sub-elements, and the classifications are scoped accordingly.

**Workflow level (escalation):** When structural breakdown is detected — the workflow's foundation is unsound, not just a step or two — no Automate classifications are issued for any step. The entire workflow needs rethinking before any automation makes sense. See broken workflow detection below.

State the rule explicitly in the output whenever it applies at any scope. The user needs to understand why a sub-element, step, or workflow was not classified Automate.

---

## Confidence states

Every step-level classification carries one of three confidence states.

### Confident

The judgment layer is visible for this step. The classification follows from the evidence in the audit. No significant information is missing.

**Criteria:** The audit provides the judgment layer (what a new person would get wrong, what undocumented information matters, what causes breakdowns, who's involved), the classification signal layer (checklist vs. judgment, output consistency, error cost, bottleneck status), and the step's relationship to the workflow outcome is clear.

### Provisional

The judgment layer is thin or absent for this step. The operator produces its best read based on available evidence, but flags that more audit information would likely change or sharpen the classification.

**Criteria:** One or more of the following is missing or vague for this step:
- Judgment layer questions answered with "it depends" or left blank
- Breakdowns described generically ("things go wrong sometimes") without specific patterns
- Quality standard undefined or cosmetic
- Handoffs or escalation paths unclear

Provisional classifications always generate a gap report entry for the affected step.

### Conditional

The judgment layer is fully visible. The operator has enough information to classify. But the correct classification depends on an explicit organizational variable that the audit cannot resolve — and no amount of better audit-writing would change this.

**Criteria:** The fork is caused by something outside the workflow itself:
- Whether a downstream review layer exists
- The organization's risk tolerance for AI-generated output in this context
- Whether this step is the final quality gate or one of several
- Team maturity with AI tools
- Whether documented standards exist that AI could check against (vs. needing to be created first)

**Output format for Conditional:** Name the variable. State both paths. Do not leave it open-ended.

Example: "Augment if documented review criteria exist for AI to check against. Keep Human until those criteria are defined — without them, AI assistance here would produce plausible but ungrounded output."

Conditional is not a hedge. It is the operator being precise about what it can and cannot determine from audit data alone.

---

## Gap report logic

### When to produce a gap report

Produce a gap report when one or more steps carry a Provisional classification. The gap report is organized by step and identifies what specific missing information would change or sharpen the classification.

### When not to produce a gap report

Do not produce a gap report when all steps are classified Confident or Conditional. The absence of a gap report is a meaningful signal: it tells the user the audit was thorough enough for the operator to commit.

### Two types of gaps

**Blocking gaps** prevent confident classification. The operator cannot determine whether a step should be Automate, Augment, or Keep Human because the evidence isn't there.

Examples:
- Judgment layer entirely absent for a step
- No information about what happens when the step goes wrong
- The audit says "this step is important" but cannot explain what it produces or who uses the output

**Sharpening gaps** would increase confidence or precision but don't prevent classification. The operator can make a reasonable call, but acknowledges it might shift with better information.

Examples:
- Judgment layer is present but thin — one-line answers where more detail would help
- Breakdowns described but root causes not diagnosed
- Quality standard implied but not explicitly stated

### When the gap pattern is diagnostic

If the judgment layer is absent across most or all steps, that is not just a collection of individual gaps. It is a finding: the workflow has not been made visible enough for AI opportunity mapping. State this directly. The gap report becomes the primary output — it tells the user what to go surface before the map can be trusted.

---

## Broken workflow detection

### Local breakdowns vs. structural breakdowns

A **local breakdown** is a step that's failing within an otherwise sound workflow. The workflow has a defined purpose, most steps function and produce value, but one or two steps are broken. The operator classifies the broken steps Stop / Rethink and maps the rest normally.

A **structural breakdown** means the workflow's foundation is unsound. The problem is not that individual steps are executed poorly — it's that the workflow itself lacks a clear reason to exist, or the reason has drifted so far from current practice that the entire structure is suspect.

### Signals of structural breakdown

Apply these at the workflow level, not step-by-step:
- The outcome field is vague, circular, or unmeasurable ("keep stakeholders informed," "ensure alignment," "support the process")
- Breakdowns appear at every step or nearly every step
- Multiple steps exist "because we've always done it this way"
- The quality standard is cosmetic or absent at the workflow level
- The judgment layer reveals that no one acts on the workflow's output — it is produced and ignored
- The same data, content, or decisions are being generated in multiple places across the workflow with no coordination
- Practitioners describe skipping or shortcutting the workflow without consequence

### What the operator does with a structural breakdown

When the operator detects a structural breakdown, it does the following:

1. States the finding directly: the breakdown pattern is structural, not executional.
2. Explains the evidence — which specific audit signals led to this conclusion.
3. Applies the automation trap rule at the workflow level: no Automate classifications are issued for any step, because automating steps in a broken workflow scales the problem.
4. Recommends that the team clarify the workflow's purpose, intended outcome, and intended audience before attempting redesign.
5. Does not produce a standard opportunity map. Instead, the output is a diagnostic — what the audit reveals about why the workflow is broken, and what needs to be resolved before AI mapping is useful.

This is a service, not a failure. The operator is protecting the team from investing in the wrong thing.

### The in-between: a broken step in a sound workflow

When one or two steps show Stop / Rethink signals but the workflow itself has a clear purpose and most steps function:
- Classify the broken steps Stop / Rethink
- Apply the automation trap rule to those steps only
- Map the remaining steps normally
- Note in the output that the broken steps should be redesigned before AI is applied to them, but the rest of the workflow can proceed

If a broken step is foundational — meaning downstream steps depend on its output, or it defines the quality bar for the entire workflow — flag this explicitly. A broken foundation step may warrant a workflow-level rethink even if other steps appear sound. The operator names this risk without overriding the step-level analysis.

---

## Multi-label classification logic

Steps can and often should carry more than one classification. The real question is not "what is this step?" but "what are the different parts of this step, and what does each part need?"

### When to apply multiple labels

Apply multiple labels when the step contains sub-tasks or decision points that warrant different treatment. The most common pattern: a step has a mechanical component (automatable) and a judgment component (augment or keep human) within the same named step.

### How to scope each label

Each label in a multi-label classification must state what specific part of the step it applies to. "Automate + Keep Human" is not useful. "Automate the routing and logging; Keep Human the decision to accept or redirect the request" is.

### Combinations that are allowed

- Automate + Augment
- Automate + Keep Human
- Augment + Keep Human (the most common pairing)
- Automate + Augment + Keep Human (when a step has three distinct layers)
- Any classification + Stop / Rethink for a different sub-element within the same step
- Automate + Stop / Rethink on the same step when scoped to different sub-elements (e.g., "Automate first-draft generation from design docs; Stop / Rethink the practice of rebuilding content from scratch when reusable assets exist")

### Combinations that are prohibited

- Automate + Stop / Rethink on the same sub-element (automation trap rule — you do not automate the broken thing)
- Four labels on a single step is a signal the step should be decomposed, not quad-labeled. Flag this to the user.

---

## Existing AI usage assessment

When the audit reveals that AI is already being used in a step, the operator evaluates the current usage alongside the classification. This is a distinct assessment — the question shifts from "should AI be used here?" to "is AI being used well here?"

### AI usage status indicators

Every classification that maps to a sub-element where AI is already in use carries one of four status indicators:

**Not yet applied** — AI is not currently used for this sub-element. The classification is a forward-looking recommendation. This is the default when no AI usage is mentioned.

**In use — working** — AI is being used and the audit suggests it's well-suited. The usage matches the classification the operator would assign. Quality checks are in place. No evidence of over-reliance or erosion. Recommendation: continue and look for ways to deepen or formalize.

**In use — needs guardrails** — AI is being used and the general application is appropriate, but the audit reveals missing quality checks, inconsistent review, undocumented standards, or early signs of over-reliance. The usage is in the right territory but the implementation needs strengthening. Recommendation: add specific guardrails (documented review criteria, human checkpoints, quality standards for AI to check against).

**In use — reconsider** — AI is being used for something it shouldn't be, or the way it's being used is causing more harm than good. This includes: AI replacing judgment that should stay human, AI output being trusted without review in high-stakes contexts, AI being used for a sub-element that should be Stop / Rethink, or AI usage that has degraded the team's ability to do the work without it. Recommendation: pull back, reassess, potentially remove AI from this sub-element.

### How to assess existing AI usage

When the audit mentions AI usage for a step, evaluate against these questions:

1. **Does the usage match the classification?** If the operator would classify this sub-element as Keep Human but AI is doing it, that's a "reconsider." If the operator would classify it as Augment and AI is augmenting, that's "working" or "needs guardrails" depending on quality checks.

2. **Is there a quality check?** Does the person review AI output before it moves forward? Do they have documented criteria for what "good" AI output looks like? Or do they "mostly trust it" and skim?

3. **Is there evidence of over-reliance?** Has the person stopped doing something they used to do because AI handles it? Do they describe editing less than they used to? Do they mention trusting AI output more over time without the output actually improving?

4. **Is the AI usage surface-level when deeper augmentation is possible?** Using AI for basic drafting when it could be checking against documented quality standards, surfacing patterns, or prompting better questions is underutilization. The usage isn't wrong, but it's leaving value on the table.

5. **Is the AI usage creating new problems?** Inconsistent voice, factual errors that slip through, work that's faster but lower quality, team members with different AI practices producing inconsistent output.

### How existing AI status affects the output

The status indicator appears alongside the classification in the opportunity block:

- "Not yet applied" does not need to be shown — it's the default
- "In use — working," "In use — needs guardrails," and "In use — reconsider" appear as a status line below the classification label in the opportunity block
- "Needs guardrails" entries should include specific recommendations for what guardrails to add
- "Reconsider" entries should explain why the current usage is problematic and what should change

The risk callouts for steps with existing AI usage should reference risks that are already materializing, not just potential future risks. "Watch for over-reliance" becomes "Over-reliance may already be developing — the audit describes editing AI output less carefully over time."

---

## Output specification

See `reference/output-spec.md` for the complete output schema, HTML structure, design language, and file conventions.

**Summary of outputs:**

The operator produces up to three outputs, saved to the `output/` directory:

1. **HTML opportunity map** (`{workflow-name}-opportunity-map.html`) — the primary output. Self-contained HTML with expandable steps, judgment layers, opportunity blocks with risk callouts, summary cards, measurement baseline, skills section, and optional value context, workflow-level findings, and recommended next audits.

2. **Gap report** (`{workflow-name}-gap-report.md`) — produced only when one or more steps are Provisional. A separate markdown file with actionable prompts organized by step. Not produced when all steps are Confident or Conditional.

3. **Chat summary** — a brief in-chat pointer to the files with classification counts, confidence distribution, and key findings.

---

## Edge cases

### The audit is a single paragraph

The input does not contain enough structure to map. Respond with a clear explanation of what the operator needs (a structured workflow audit) and point the user to the audit format. Do not attempt classification. Do not produce a gap report — there is nothing to gap-report against.

### The audit describes only one step

A single step is not a workflow. The operator maps the step if the audit is rich enough, but notes that a single-step map has limited value and asks whether the workflow has additional steps that weren't captured.

### The audit is excellent but the workflow is trivial

Some workflows are simple and don't need AI. If the audit reveals a workflow where every step is low-judgment, low-volume, and low-stakes, it is valid to produce a map that is mostly "Keep Human — the effort of implementing AI here exceeds the value." This is a legitimate finding. The operator does not force AI opportunity into workflows where it doesn't exist.

### The user provides a workflow description, not an audit

A workflow description lists steps. An audit surfaces the judgment layer. If the input reads like a process document — step names and descriptions but no judgment layer, no breakdowns, no quality standards — the operator treats every step as Provisional and produces a gap report that effectively functions as an audit guide: here's what you need to go find out for each step.

### Multiple workflows in one audit

If the input contains more than one distinct workflow, produce separate maps. Do not merge unrelated workflows into a single map.

### Compressed steps (step is actually a sub-workflow)

Some steps in a macro-level audit are actually compressed sub-workflows — they contain multiple distinct activities, handoffs, or judgment points that happen in sequence. The operator should detect this and flag it without refusing to classify.

**Signals that a step is compressed:**
- The judgment layer describes multiple distinct judgments that happen at different points, not one judgment
- The step carries 3+ classifications because it contains fundamentally different types of work
- "What actually happens here" reads like a process with its own internal sequence, not a single activity
- Multiple handoffs or role changes happen within a single named step
- The step spans days or weeks, not hours

**What the operator does:** Classify the step at the current level of granularity. Then flag it as a candidate for sub-workflow audit in the HTML output's footer section under "Recommended next audits." The note should name the step, explain why it appears compressed, and suggest that a deeper audit on that step would produce a more actionable map for implementation.

The macro-level map tells you where to focus. A sub-workflow audit tells you how to implement. Both are valid — one is not better than the other. The operator produces whatever the input supports and points toward the natural next move.
