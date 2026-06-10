# Classification Rubric

Quick reference for the four classifications. For full decision logic, see rules.md.

---

## Automate

**Definition:** Repetitive, rule-followable, low-stakes. A checklist or decision tree could govern it. Error is recoverable.

**Triggering signals:**
- Consistent output regardless of who performs it
- Described in terms of actions, not decisions
- Breakdowns caused by volume, inconsistency, or forgetting
- Judgment layer is thin because judgment genuinely isn't needed
- Bottleneck is repetition, not complexity
- Friction: tedious, repetitive, draining due to volume — not hard, just too much of it

**Disqualifying signals:**
- Context changes case-by-case
- Error is hard to detect or expensive to reverse
- Audit language: "it depends," "you have to know," "experience matters"
- The same sub-element is classified Stop / Rethink (automation trap — see below)

**Examples:** form routing, request logging, confirmation messages, completion tracking, data collection, template scaffolding, transcript generation, formatting tasks

**Skills to act on this:**
- Workflow automation design (mapping triggers, conditions, and actions)
- Integration/API skills (connecting tools and systems)
- Agent building (for more complex multi-step automation)
- Basic prompting (for simpler AI-driven tasks)

---

## Augment

**Definition:** Judgment-dependent, but AI can amplify that judgment. AI prompts, checks, drafts, surfaces, or flags — the human still decides.

**Triggering signals:**
- Judgment layer is visible and decisions are articulable
- Breakdowns caused by inconsistency or variation in practitioner skill
- Would benefit from a "second set of eyes" or structured prompt
- Quality standards exist or could be defined for AI to check against
- Experienced practitioners have internalized principles that could be externalized
- Friction: cognitively heavy — too much context-holding, too many considerations, too much source-switching

**Disqualifying signals:**
- Judgment depends on live relationship dynamics or emotional context
- Requires taste that resists codification (knows quality but can't explain criteria)
- Plausible-but-wrong AI output would be high-cost and hard to catch

**Examples:** AI-generated discovery questions per project type, flagging when output drifts from stated objectives, applying documented quality standards as a live check, synthesizing interview themes, surfacing patterns in engagement data

**Skills to act on this:**
- Prompt engineering (building prompts and assistants that reliably augment judgment)
- Context architecture (structuring the principles, standards, and knowledge AI needs to check against)
- Quality evaluation design (defining what "good" looks like in terms AI can assess)
- Knowledge codification (externalizing the tacit expertise that experienced practitioners carry)

---

## Keep Human

**Definition:** Relationship, taste, contextual judgment, or stakes that cannot be safely delegated — even in an assistive role.

**Triggering signals:**
- Navigating relationships, building trust, reading emotional cues
- "Taste" decisions — can identify quality but can't fully explain criteria
- High-stakes, hard-to-detect, or irreversible error
- Governance function — human accountability required
- Audit language: "knowing when," "sensing," "reading the room"
- Friction: difficult but meaningful — the practitioner finds it hard but recognizes it as high-value (inverse signal, reinforces Keep Human)

**Disqualifying signals:**
- Step can be fully described as a sequence of actions with clear criteria
- "Human judgment" is actually pattern recognition AI handles well
- Classified Keep Human only because no one tried to articulate the judgment (not because it resists articulation) — this is Provisional, not Confident Keep Human

**Examples:** decision to proceed/redirect a request, stakeholder negotiation, root cause vs. symptom diagnosis, final quality calls requiring taste, interpreting results in context

**Skills to act on this:**
- Knowledge codification (documenting the judgment for teaching and onboarding, even though it's not being automated)
- Mentorship and knowledge transfer (ensuring the expertise scales through people, not tools)
- No AI-specific skills required for this classification — the value is in protecting human judgment, not augmenting it

---

## Stop / Rethink

**Definition:** Exists by habit, inertia, or unclear mandate. Redesigning or automating would preserve or scale a problem.

**Triggering signals:**
- Cannot articulate purpose in terms of a specific outcome
- "It's always been this way" or "no one really uses the output"
- Same work done in multiple places with no coordination
- Quality standard is cosmetic ("it looks complete") not substantive
- Practitioners skip or shortcut the step without consequence
- Downstream action from this step rarely happens
- Friction: pointless or resentful — painful and practitioner can't articulate what value it creates

**Disqualifying signals:**
- Step has a clear purpose and measurable output, even if execution is poor (that's a redesign problem)
- Step is important but under-documented (that's a gap report issue)

**Examples:** reporting no one acts on, revision rounds with no stopping criteria, manual formatting that duplicates automated output, data collection that overlaps with other steps

**Skills to act on this:**
- Change management (navigating the politics of stopping or fundamentally redesigning work people are attached to)
- Stakeholder communication (explaining why something should change, especially to the person who created the current process)
- Process design (if the step is being redesigned rather than stopped)

---

## Multi-label guidance

Steps often warrant more than one classification. The question is not "what is this step?" but "what are the different parts of this step?"

**Allowed combinations:**
- Automate + Augment
- Automate + Keep Human
- Augment + Keep Human (most common)
- Automate + Augment + Keep Human (three distinct layers)
- Any classification + Stop / Rethink for a different sub-element within the same step
- Automate + Stop / Rethink on the same step when scoped to different sub-elements (e.g., "Automate first-draft generation; Stop / Rethink rebuilding from scratch when reusable assets exist")

**Prohibited:**
- Automate + Stop / Rethink on the same sub-element (automation trap rule)
- Four labels on one step — signal to decompose the step, not quad-label it

**Scoping requirement:** Each label must state what specific part of the step it applies to. "Automate + Keep Human" is not useful. "Automate the routing and logging; Keep Human the decision to accept or redirect" is.

---

## The automation trap rule

**Stop / Rethink and Automate are mutually exclusive on the same sub-element.**

Three scopes:

- **Sub-element level (default):** If a sub-element is Stop / Rethink, that same sub-element does not also receive Automate. You do not automate the broken thing.
- **Step level:** Automate and Stop / Rethink can coexist on the same step when they refer to different sub-elements.
- **Workflow level (escalation):** When structural breakdown is detected, no Automate classifications anywhere.

State this rule explicitly in the output whenever it applies at any scope.
