# Examples

Three examples showing the operator's decision logic in action. Each includes a summary of the audit input, the operator's assessment, step-level classifications with reasoning, and the resulting output.

Full audit inputs are in the `examples/` directory.

---

## Example 1: Instructional Design Workflow

**Audit file:** `examples/lxd-workflow-audit.md`

### Audit quality assessment

1. **Outcome defined?** Yes. "Produce learning assets that measurably close a defined performance or knowledge gap for a specific audience, delivered on time and within agreed scope." Specific, measurable, tied to a business result. No escalation needed.

2. **Judgment layer visible?** Yes, across all six steps. Each step provides substantive answers to all four judgment questions. The designer can articulate what experienced practitioners know, what isn't documented, what causes breakdowns, and who's involved. This is a complete audit.

3. **Breakdown pattern?** Local. Breakdowns cluster at specific steps (inconsistent intake, undocumented design rationale, content rebuilt from scratch, open-ended revision cycles, measurement defaulting to completion rates). These are executional problems in an otherwise sound workflow. No structural breakdown detected.

4. **Workflow value?** High. Consequence of failure is significant (wrong training built, skill gaps unaddressed, L&D credibility eroded). Scale reaches ~2,000 employees. Time cost is substantial (500-1,000 designer-hours per quarter). Strategically visible — the team is expected to model AI-enabled ways of working. Delight potential is high: the friction is concentrated in production and revision steps where AI has clear leverage, and freeing that time redirects energy toward the work designers find most meaningful. This is a strong candidate for AI redesign.

**Assessment:** Complete audit. High-impact workflow. All steps can be classified Confidently. No gap report needed.

### Step-by-step classification

**Step 1: Intake & Request Triage**
Confidence: Mixed — Confident (Automate, Keep Human), Conditional (Augment)

| Classification | Scope | Reasoning |
|---|---|---|
| Automate | Form routing, request logging, confirmation messages, basic info gathering | The submission mechanics are procedural. Breakdowns here are caused by inconsistent format and scattered channels, not judgment. Friction data confirms: "logging requests and chasing down basic information is tedious and repetitive." |
| Augment (Conditional) | Surfacing documented diagnostic patterns, prompting stronger intake questions based on request type, flagging when a request matches patterns from past projects that went sideways | The experienced designers' diagnostic judgment is articulable — they can describe what they check, what questions they ask, and what signals they look for. But this judgment is not currently documented. **Conditional: Augment if the team codifies their diagnostic judgment patterns (what to ask, what to watch for, what past patterns suggest). Keep Human exclusively until they do.** The documentation is the prerequisite — without it, AI has nothing to augment against. |
| Keep Human | The actual decision to proceed, push back, or redirect — and the relationship navigation required to do it well | The audit is clear: "the first judgment call is whether training is even the right intervention." The decision itself depends on stakeholder history, relationship context, and live diagnostic skill that resists codification. Friction data reinforces: "the diagnostic conversation itself is energizing — that's where the designer adds real value." This stays human regardless of whether the Augment condition is met — AI supports the decision, it doesn't make it. |

> ⚠ **Automate — Watch for:** Loss of context. Automated intake routing may strip the informal context (urgency cues, stakeholder tone, background) that designers currently pick up when requests arrive via Slack or email. Build in a way for context to travel with the routed request.

> ⚠ **Augment — Watch for:** Anchoring. If AI surfaces diagnostic prompts before the designer forms their own read of the request, it may bias their judgment. Consider showing AI-generated prompts after the designer's initial assessment, as a "did you consider..." check rather than a starting point.

> ⚠ **Keep Human — Watch for:** Key-person dependency. The diagnostic judgment lives in experienced designers' heads. If they leave, intake quality drops immediately. Documenting the judgment (the Augment prerequisite) also addresses this risk.

---

**Step 2: Discovery & Needs Analysis**
Confidence: Confident

| Classification | Scope | Reasoning |
|---|---|---|
| Augment | Generating discovery question sets per project type; synthesizing interview themes; flagging gaps in information before design begins; existing content audit across repositories | The judgment layer is visible and articulable: experienced designers have internalized question patterns, diagnostic frameworks, and pattern recognition from previous projects. These can be externalized. Friction data confirms cognitive load: "synthesizing notes from multiple conversations is cognitively heavy." AI can reduce that load. |
| Keep Human | Reading the room; building stakeholder trust; making the call on root cause vs. symptom | The audit describes judgment that depends on live relationship dynamics: "sensing when a stakeholder doesn't know what they need" and "calibrating how much discovery is enough." Friction confirms: "the diagnostic conversation itself is the most rewarding part." |

Automate applies to transcript generation and note formatting (mechanical sub-tasks within discovery), but the audit groups these as secondary to the primary judgment work. In the map output, these appear under Augment (AI-assisted synthesis) rather than pure Automate because they feed directly into the judgment process.

**Existing AI usage:** One designer is using ChatGPT to summarize interview notes. Status: **In use — needs guardrails.** The application is appropriate (note synthesis is squarely in Augment territory), but the audit reveals two problems: the AI "sometimes invents details that weren't discussed or misses nuance," and there's no shared practice — one person doing it their own way. Guardrails needed: a review checklist for AI-generated summaries (check against source notes for fabrication), and a decision on whether to make this a team standard with documented practices rather than one person's experiment.

---

**Step 3: Instructional Design**
Confidence: Confident

| Classification | Scope | Reasoning |
|---|---|---|
| Augment | Learning objective generation from discovery notes; template scaffolding; applying documented design principles as a live check; flagging when design decisions contradict stated learner needs | Friction data identifies the split: "generating learning objectives from discovery notes is formulaic and tedious" while "the taste calls are where the designer does their best work." The formulaic parts can be AI-assisted. The team's implicit quality standards, once documented, give AI something to check against. |
| Keep Human | The taste layer: final calls on structure, emphasis, modality, and what "good" looks like for this specific context | The audit is explicit: "what you leave out is often more important than what you include" and "these standards exist in the heads of experienced designers but aren't codified." Until taste is codifiable (and it may not be), this stays human. |

---

**Step 4: Content Development**
Confidence: Confident

| Classification | Scope | Reasoning |
|---|---|---|
| Automate | First-draft generation from design doc; repurposing existing content; formatting, templating, basic visual production tasks | This is the highest-volume, most time-intensive step. Friction confirms: "formatting, templating, and basic production work is tedious and time-consuming." The audit identifies content rebuilt from scratch when reusable assets exist. Automate applies to the mechanical production layer. |
| Augment | Applying documented voice/quality standards as a live check; flagging content that drifts from learning objectives; suggesting existing assets to reuse | The audit reveals undocumented voice and tone standards that vary by designer. Once externalized, AI can check against them. Inconsistent quality across the team is an augmentation opportunity: AI can surface what experienced designers check implicitly. |
| Stop / Rethink | The practice of rebuilding content from scratch when similar assets already exist | The audit is direct: "content is rebuilt from scratch when similar assets already exist because there's no good way to find or adapt them." This is a practice that exists by habit and absent infrastructure. The sub-element to stop is the rebuild-from-scratch pattern, not content development itself. Automation trap: this sub-element is not classified Automate despite being time-consuming, because the practice itself needs rethinking (a reuse system, not faster rebuilding). |

**Existing AI usage:** Two of four designers use ChatGPT for first-draft generation. Status: **In use — needs guardrails.** The application is appropriate (first-draft generation from a design doc is squarely in Automate territory), but the audit reveals three problems: (1) one designer admits editing less than he should — "the drafts have gotten good enough that I mostly just tweak" — which is early-stage over-reliance and quality erosion; (2) neither has a formal review checklist, so the quality gate is subjective and variable; (3) two designers don't use AI at all, creating inconsistent practices across the team. Guardrails needed: documented review criteria for AI-generated drafts (voice, accuracy, alignment with learning objectives), a team-level decision on whether AI drafting is standard practice, and attention to the over-reliance signal from the designer who's editing less over time.

---

**Step 5: Stakeholder Review & Revision**
Confidence: Confident

| Classification | Scope | Reasoning |
|---|---|---|
| Augment | Feedback consolidation across reviewers; catching common issues earlier in development to reduce revision volume; flagging feedback that contradicts agreed objectives | The breakdowns are clear: "feedback arrives in multiple formats, untracked" and "the same comments surface repeatedly because issues weren't caught earlier." AI can consolidate, track, and catch drift. Friction confirms the mechanical pain: "consolidating feedback from multiple sources in multiple formats is tedious." |
| Stop / Rethink | Open-ended revision cycles with no agreed stopping criteria | The audit describes a structural pattern: "there's no agreed stopping criteria — no definition of done for review." The problem isn't that revision is slow (that would be an Automate opportunity). The problem is that no one has agreed when revision should end. Automation trap: automating revision tracking wouldn't solve the problem because the problem is the absence of a stopping rule, not the speed of the process. |
| Keep Human | Negotiating with stakeholders; deciding what feedback improves the asset vs. what would make it worse | Judgment depends on political dynamics and relationship context that the audit describes as entirely undocumented. |

---

**Step 6: Launch & Measurement**
Confidence: Confident

| Classification | Scope | Reasoning |
|---|---|---|
| Automate | Completion tracking, data collection, scheduled performance reports against baseline | The mechanical measurement infrastructure: tracking, data pulls, report generation. Friction confirms: "setting up tracking and pulling completion data is tedious but straightforward." |
| Augment | Surfacing patterns in engagement and feedback data; flagging assets underperforming against stated objectives | The audit describes an opportunity to connect learning activity to business outcomes, which currently "requires knowing what to measure, how to set up the measurement, and how to have credible conversations." AI can surface patterns that humans then interpret. |
| Stop / Rethink | Measurement defaulting to completion rates when the team knows they don't indicate impact | The audit is candid: "completion rate tells you almost nothing about impact" and "baselines are almost never established before launch." The current measurement practice exists because it's easy, not because it's useful. The sub-element to rethink isn't measurement itself, it's the default to completion-as-proxy-for-impact. |
| Keep Human | Interpreting results in context; deciding whether to iterate, retire, or escalate findings | Judgment about what the data means and what to do about it. |

### Compressed step flag

Steps 2 (Discovery) and 4 (Content Development) show compressed step signals. Discovery contains multiple distinct activities (stakeholder interviews, SME conversations, existing content audit, synthesis) spanning several days with different judgment requirements. Content Development contains production, quality checking, and reuse decisions that are fundamentally different types of work. Both would benefit from sub-workflow audits for implementation planning.

### Output summary

- **Map:** 6 steps. 5 fully Confident, 1 mixed (Step 1: Confident Automate and Keep Human, Conditional Augment). HTML opportunity map saved to `output/`.
- **Classifications:** 8 Automate, 11 Augment (1 Conditional), 7 Keep Human, 3 Stop / Rethink
- **Gap report:** Not produced. No Provisional classifications.
- **Risk callouts:** Included per step. Key risks flagged: anchoring on AI-surfaced diagnostic prompts (Step 1), plausible-but-wrong quality checks (Steps 3, 4, 5), accountability gap on automated first drafts (Step 4), over-reliance/deskilling on AI-assisted synthesis (Step 2).
- **Measurement baseline:** Time from intake to first draft (3-5 days to 1-2 days target); revision rounds per project (not yet tracked, target reduce); judgment documented (0 to principles captured per stage).
- **Skills to act on this map:**
  - Prompt engineering — needed for the Augment classifications across Steps 1-3 and 5 (building prompts that surface diagnostic questions, check against design principles, consolidate feedback)
  - Context architecture — needed to externalize the team's implicit quality standards, voice guidelines, and design principles so AI can check against them (prerequisite for most Augment implementations here). Also the prerequisite for unlocking the Conditional Augment at Step 1.
  - Knowledge codification — needed for Keep Human steps: documenting the judgment that experienced designers carry so it's teachable and referenceable, even though it's not being automated. Also directly addresses key-person dependency risks.
  - Workflow automation design — needed for the Automate classifications in Steps 1, 4, and 6 (intake routing, template scaffolding, tracking setup)
  - Change management — needed for the Stop / Rethink classifications in Steps 4, 5, and 6 (retiring the rebuild-from-scratch pattern, establishing revision stopping criteria, rethinking completion-as-measurement)
- **Recommended next audits:** Steps 2 and 4 flagged as compressed.

---

## Example 2: Internal Content Approval Process

**Audit file:** `examples/content-approval-audit.md`

### Audit quality assessment

1. **Outcome defined?** Yes. "Ensure all externally published content meets brand standards, legal requirements, and strategic messaging guidelines before publication." Clear and specific. No escalation needed.

2. **Judgment layer visible?** Uneven. Steps 1 (Submission) and 5 (Publication) have clear, substantive judgment layers. Steps 2 (Editorial Review) and 4 (Approval) are thin: vague answers, "it depends," no documented criteria. Step 3 (Revision) is procedural and appropriately light.

3. **Breakdown pattern?** Local. Steps 2 and 4 are where the workflow struggles. The other steps function. This is not a structural breakdown — the workflow has a clear purpose and produces real value. The problem is that two critical steps lack visible judgment.

4. **Workflow value?** Medium-high. Consequence of failure is real (off-brand or legally risky content reaching the public). Scale is significant (tens of thousands of external readers, 15-20 internal content creators). Time cost is substantial (50-60% of a 6-person team's capacity). Strategic relevance is indirect but visible. Delight potential is moderate-high — the editor and comms lead carry the most pain, and content creators across the company would benefit from faster turnaround. Worth investing in.

**Assessment:** Partial audit. Medium-high impact workflow. Steps 1, 3, and 5 can be classified Confidently. Steps 2 and 4 are Provisional. Gap report needed.

### Step-by-step classification

**Step 1: Content Submission**
Confidence: Confident

| Classification | Scope | Reasoning |
|---|---|---|
| Automate | Submission logging, metadata capture, queue management, confirmation to submitter | Well-documented, procedural, consistent. Breakdowns are caused by people bypassing the process, not by the process itself. Friction is minimal and related to chasing missing metadata, which automation would prevent. |

Single classification. The audit confirms this step is low-judgment, and the judgment layer is thin because judgment genuinely isn't required (Automate triggering signal, not a gap).

---

**Step 2: Editorial Review**
Confidence: Provisional

| Classification | Scope | Reasoning |
|---|---|---|
| Augment (provisional) | Checking drafts against brand standards, flagging common issues, consistency checking | The audit suggests judgment is being applied ("the editor has a sense of what sounds right") but the criteria aren't articulated. If review standards were documented, AI could check against them. But the audit can't confirm what those standards are. |
| Keep Human (provisional) | Tone and emphasis judgment, knowing "what the exec team cares about this week" | The audit hints at relationship and political context driving editorial decisions, but doesn't articulate it clearly enough to classify confidently. |

The editorial review step is where this audit is thinnest. "It depends on the situation" and "output consistency depends on who's reviewing" are classic thin-judgment-layer signals. The operator can see that judgment exists, but can't determine the boundary between what's augmentable and what must stay human until the team articulates their review criteria.

---

**Step 3: Revision & Resubmission**
Confidence: Confident

| Classification | Scope | Reasoning |
|---|---|---|
| Automate | Change tracking, version management, revision status updates | The mechanics of revision are procedural. The audit confirms: "the author follows the editor's tracked changes." |
| Stop / Rethink | Unbounded revision cycles where new reviewers introduce feedback in late rounds | The audit describes a structural pattern: "there's no agreed limit on revision rounds" and "new reviewers show up in round 2 or 3 with feedback that could have been given earlier." The problem is the absence of a rule, not the speed of revision. |

---

**Step 4: Approval**
Confidence: Provisional

| Classification | Scope | Reasoning |
|---|---|---|
| Conditional | Routing and approval workflow | Conditional: Automate if approval authority and criteria are documented (route to the right approver based on content type, check against defined criteria). Keep Human until they are (the current ambiguity means a human has to navigate who approves what on a case-by-case basis). |

This step is both Provisional (the judgment layer is thin) and Conditional (even with full information, the classification depends on whether the organization documents its approval criteria). The gap report covers what's missing. The conditional framing covers what needs to be decided.

The audit signals are concerning: "different content types apparently require different approvers, but the rules aren't documented" and "who's involved seems to depend on the content." This isn't judgment — it's undocumented process. Once documented, this step is highly automatable. Until then, it stays human by default.

---

**Step 5: Publication**
Confidence: Confident

| Classification | Scope | Reasoning |
|---|---|---|
| Automate | Multi-channel formatting, scheduling, distribution | The audit confirms this is procedural: "channel formatting requirements are documented (if slightly outdated)." Friction confirms: "reformatting the same content for multiple channels is tedious." |
| Augment | Optimal posting time recommendations | The social media manager has internalized timing knowledge that could be externalized and AI-assisted. Minor augmentation opportunity. |

### Output summary

- **Map:** 5 steps. 3 Confident, 2 Provisional (one also Conditional).
- **Classifications:** 3 Automate, 2 Augment, 1 Keep Human, 1 Stop / Rethink, 1 Conditional
- **Gap report:** Produced. Two entries:
  - Step 2 (Editorial Review): **Blocking gap.** Review criteria not articulated. "What makes the editor send a piece back vs. approve it? What are the specific brand standards being checked? When does a piece need the comms lead vs. just the editor?" Without this, the Augment/Keep Human boundary can't be drawn.
  - Step 4 (Approval): **Blocking gap.** Approval authority and criteria undocumented. "Who approves what content type? What are the criteria for escalation to the director? What defines 'legally sensitive'?" This is the most actionable gap: documenting approval rules would likely shift this step from Keep Human to Automate.
- **Skills to act on this map:**
  - Workflow automation design — needed for Automate classifications (submission logging, change tracking, multi-channel formatting). These are straightforward implementations.
  - Context architecture — needed if the team documents review criteria and approval rules (the gap report's recommendation), which would unlock Augment and Automate opportunities at Steps 2 and 4
  - Change management — needed for the Stop / Rethink on unbounded revision cycles (establishing stopping criteria requires changing team norms)
  - Skills for Steps 2 and 4 are deferred until classifications are confirmed. If the gaps are addressed and those steps shift to Augment or Automate, prompt engineering and workflow automation skills will be needed.
- **Recommended next audits:** None. Steps are appropriately scoped.

---

## Example 3: Weekly Cross-Functional Status Report

**Audit file:** `examples/status-reporting-audit.md`

### Audit quality assessment

1. **Outcome defined?** Vague. "Keep leadership informed about project status across teams." This is circular: the report exists to inform, but what decisions should the information enable? What action should a reader take? The outcome is unmeasurable.

2. **Judgment layer visible?** Yes, the audit surfaces detailed information for each step. But what the judgment layer reveals is damning: the judgment at most steps is about compensating for a broken process, not about creating value. The coordinator's expertise is in working around dysfunction, not in producing meaningful output.

3. **Breakdown pattern?** Structural. Breakdowns appear at every step:
   - Step 1: Submissions are late or missing every week; coordinator fabricates status from other sources
   - Step 2: Template is outdated; coordinator informally adjusts it
   - Step 3: Review is superficial with no criteria; coordinator describes it as "pointless"
   - Step 4: Distribution list is outdated; late sends generate no inquiry
   - Step 5: Follow-up doesn't happen. No one references the report.

   This is not a collection of executional problems. This is a workflow that lacks a clear reason to exist. Every step reveals the same underlying issue: no one has agreed on what this report is for or what action it should drive.

4. **Workflow value?** Low. Consequence of failure appears to be zero — the coordinator has tested late delivery with no response. Scale is narrow (20 recipients, no evidence they read it). Time cost is disproportionate to demonstrated value: 350-450 hours per year on a report whose impact is unclear. No current leadership champion — the originating VP left two years ago. Delight potential is inverted: the improvement people want is permission to stop, not a better version of the report. The value data reinforces the structural finding: this workflow consumes real resources without producing demonstrable value.

**Assessment:** Structural breakdown detected. Low-impact workflow. The operator issues a workflow-level finding before any step-level classification.

### Workflow-level finding

**Finding:** The breakdown pattern in this audit is structural, not executional. Every step reveals the same signal: the report is produced by habit, not by need. The coordinator described multiple compensating behaviors (fabricating status from Slack channels, informally adjusting an outdated template, BCCing people who should be on the official list) that indicate the formal process has disconnected from any real purpose. The strongest signal: "No one has ever come back to me with a question about the report" and "I'm sending a report to people who may not open it."

**Automation trap applied at workflow level:** No Automate classifications are issued for any step, despite several steps being clearly repetitive and rule-followable (data collection, formatting, distribution). Automating this workflow would produce a faster, more consistent version of something no one uses. That scales the problem.

**Recommendation:** Before any AI mapping or redesign, the team needs to answer: What decisions should this report enable? Who needs it and why? What would change if it stopped tomorrow? The coordinator already tested this informally: "I've sent it Wednesday a few times with no response" — and the friction data across all steps reinforces it: the coordinator finds the work painful and cannot articulate what value it creates.

### Step-level assessment

The operator does not produce a standard opportunity map for a structurally broken workflow. Instead, it documents what each step reveals about the structural problem.

| Step | What the audit reveals | Classification |
|---|---|---|
| Data Collection | Status is chased, fabricated, or inconsistent. Team leads treat it as an annoyance. Coordinator compensates with invisible labor. | Stop / Rethink |
| Consolidation & Formatting | Pure manual labor assembling data of questionable accuracy into an outdated template. Coordinator describes it as "the most mindless part of my job." | Stop / Rethink |
| Review & Cleanup | No review criteria. Self-review only. Coordinator: "I skim it to make sure nothing embarrassing is in there." | Stop / Rethink |
| Distribution | Outdated distribution list. Late sends generate no inquiry. Coordinator has tested sending late with no response. | Stop / Rethink |
| Follow-Up & Action | Does not happen. The step exists as a concept but not a practice. "The friction is knowing that all the work in steps 1-4 leads to nothing." | Stop / Rethink |

### What the friction data reveals

The friction question was particularly diagnostic in this audit. Across all steps:

- Step 1: "It feels like pulling teeth for something nobody reads."
- Step 2: "I'm basically a human copy-paste machine."
- Step 3: "It's not painful. It's just pointless."
- Step 4: "It makes me question the whole thing."
- Step 5: "The friction is knowing that all the work in steps 1-4 leads to nothing."

This is a gradient from resentful (Step 1) to existential (Step 5). When friction data tells a story across the full workflow, it's a diagnostic pattern, not a collection of individual pain points.

### Output summary

- **Map:** Workflow-level finding issued. No standard opportunity map produced.
- **Classifications:** 5 Stop / Rethink. No Automate, Augment, or Keep Human classifications.
- **Gap report:** Not applicable. The issue is not missing information — the audit is thorough. The issue is what the information reveals.
- **Automation trap:** Invoked at workflow level. Explicitly stated in the finding.
- **Recommendation:** Clarify purpose and intended action before redesigning. If the report has a legitimate purpose, rebuild from that purpose. If it doesn't, stop producing it.
- **Skills to act on this map:**
  - Change management — the primary skill needed here. Stopping a recurring process that's been running for years requires navigating organizational inertia and having honest conversations about value.
  - Stakeholder communication — someone needs to make the case to leadership that 350-450 hours per year is being spent on a report with no demonstrated impact. The audit data supports this case, but making it requires skill.
  - No AI-specific skills required. This workflow doesn't need AI — it needs a decision about whether it should exist.
