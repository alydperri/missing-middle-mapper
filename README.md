# Missing Middle Mapper

An AI operator that reads workflow audits and produces opportunity maps — classifying each step as Automate, Augment, Keep Human, or Stop / Rethink.

It does not map what it cannot see. If the judgment layer (the implicit decisions, quality standards, and expertise behind each step) isn't visible in the audit, the operator says so and tells you what to go find out.

## How to use it

### 1. Prepare your audit

Fill out `audit-template.md` for the workflow you want to map. The template has help text for each question. Four things matter most:

- **Define the outcome.** What is this workflow supposed to produce or enable? If you can't answer this clearly, the operator will flag it before doing anything else.
- **Describe the workflow's value.** What happens if it breaks? How many people does it affect? How much time does it consume? This helps the operator contextualize its findings and helps you prioritize which workflows to invest in.
- **Surface the judgment layer.** For each step, answer: what would a new person get wrong? What information isn't written down? What causes breakdowns? Who else is involved? These are the questions that reveal where AI can actually help.
- **Be honest about friction.** What's tedious, what's cognitively heavy, what feels pointless, what's hard but meaningful. Different kinds of friction point to different AI opportunities.

Completed examples are in `examples/` if you want to see what a filled-out audit looks like at different quality levels.

### 2. Run the operator

Open this folder as a workspace in Claude Code. Provide your completed audit and ask the operator to produce an opportunity map.

```
Produce an AI opportunity map from this workflow audit.
```

Paste the audit contents or point to the file path.

### 3. Get your output

The operator saves files to the `output/` directory:

- **`{workflow-name}-opportunity-map.html`** — the map itself. Open in a browser. Each step is expandable to show the hidden judgment layer, breakdown patterns, classification rationale, and collapsible risk callouts ("⚠ Watch for") per opportunity. Also includes workflow value context, measurement baseline, and the skills needed to act on what the map found.
- **`{workflow-name}-gap-report.md`** — produced only when the audit is incomplete for one or more steps. A checklist of what to go find out, organized by step.

The operator also provides a brief summary in chat with classification counts, confidence distribution, and key findings.

## What to expect

**Clean audit → confident map, no gap report.** All steps classified with rationale. Includes workflow value context (when provided), measurement baseline, and the skills needed to act on the classifications. If any steps appear compressed (they're really sub-workflows), the operator flags them as candidates for deeper audits.

**Partial audit → mixed confidence map + gap report.** Well-documented steps get confident classifications. Thin steps get provisional classifications with a gap report explaining exactly what's missing and why it matters. Skills for provisional steps are deferred until the classification is confirmed. Address the gaps, update the audit, re-run the operator.

**Broken workflow → diagnostic finding, no map.** If the audit reveals that the workflow lacks a clear purpose and breakdowns appear at every step, the operator won't produce an opportunity map. It will explain what the audit reveals about why the workflow is broken and recommend clarifying purpose before redesigning. This is the operator protecting you from automating the wrong thing.

## What's in the folder

```
missing-middle-mapper/
│
├── CLAUDE.md                   ← Claude reads this first. Routes to everything else.
├── README.md                   ← You're here. How to use the operator.
│
├── identity.md                 ← Who the operator is, what it owns, what it will and won't do.
├── rules.md                    ← The complete decision logic: classifications, confidence
│                                  states, gap report triggers, broken workflow detection,
│                                  edge cases. The heart of the operator.
│
├── audit-template.md           ← START HERE. Blank audit form with help text per question.
│                                  Fill this out for your workflow, then feed it to the operator.
│
├── examples.md                 ← Three worked examples showing the operator's reasoning
│                                  on a clean, partial, and broken audit.
├── examples/
│   ├── lxd-workflow-audit.md           Complete audit (high quality, high impact)
│   ├── content-approval-audit.md       Partial audit (uneven quality, some gaps)
│   └── status-reporting-audit.md       Broken audit (structurally unsound workflow)
│
├── reference/
│   ├── classification-rubric.md        Four classifications: triggers, disqualifiers,
│   │                                   skills, multi-label guidance, automation trap
│   ├── gap-report-criteria.md          Blocking vs. sharpening gaps, when to produce/omit
│   ├── audit-quality-checklist.md      Input quality assessment: workflow-level, value,
│   │                                   per-step checks, quality tiers, decision tree
│   ├── risk-categories.md              Risk patterns per classification with triggers
│   ├── output-spec.md                  HTML output schema: sections, CSS, interactions,
│   │                                   gap report format, chat summary format
│   └── lxd-example-opportunity-map.html  Fully built reference map — match this.
│
└── output/                     ← Operator saves all outputs here.
    ├── {workflow-name}-opportunity-map.html
    └── {workflow-name}-gap-report.md       (only when gaps exist)
```

## The framework

This operator is built on the Missing Middle framework: the gap between AI fluency (people can use AI tools) and AI impact (AI meaningfully improves the work that matters).

The missing middle is work visibility. Most knowledge work depends on judgment, context, and expertise that lives in people's heads. AI cannot reliably improve work the organization cannot see, describe, or evaluate. Making that work visible is the prerequisite for meaningful AI transformation.

The operator enforces this by refusing to produce confident classifications until the judgment layer is visible. The gap report isn't a consolation prize for incomplete input — it's the framework in action.
