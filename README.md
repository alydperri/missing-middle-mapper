# Missing Middle Mapper

## The problem

Most teams are stuck in one of two places with AI.

Some tried it and got burned. They gave people tools, encouraged experimentation, maybe even ran a pilot. Usage went up. Impact didn't. The AI made things faster but not better — or worse, it made things faster and worse at the same time. Now there's skepticism, and no one can explain what went wrong.

Others haven't really started. They know AI matters, they've heard the mandate, but the gap between "use AI more" and knowing *where it actually fits in their work* feels enormous. The learning curve looks steep. The starting point isn't clear.

These feel like different problems. They're not. They're the same problem.

**Both teams skipped the same step: making the work visible before trying to change it.**

AI cannot reliably improve work the organization can't clearly see. The judgment calls, undocumented handoffs, quality bars that only exist in people's heads — that's where the real value lives, and it's invisible. Applying AI without surfacing that layer is how you get fast mediocrity instead of meaningful improvement.

The gap between AI fluency and AI impact has a name. It's the **missing middle**. And closing it starts with one thing: a workflow audit.

## What this operator does

The Missing Middle Mapper reads a workflow audit and produces an AI opportunity map — classifying each step as **Automate**, **Augment**, **Keep Human**, or **Stop / Rethink**.

But it doesn't just label things. It surfaces the hidden judgment layer underneath each step, identifies risks, flags where existing AI usage is working or failing, tells you what skills you need to act, and — when the audit is incomplete — produces a gap report that tells you exactly what to go find out.

If the workflow is broken, the operator says so. It won't help you automate the wrong thing.

## Who this is for

**If you tried AI and it didn't produce outcomes:** the audit is a diagnosis. You applied AI without making the work visible first. The map shows you what you skipped and where to refocus. The gap report tells you what to surface. The risk callouts name the problems you're probably already seeing — over-reliance, quality erosion, inconsistent practices.

**If you haven't started yet:** the audit is your starting point. You don't need AI fluency before you begin. Audit one priority workflow first. The map tells you where AI can help, which tells you what to learn. Fluency becomes just-in-time instead of front-loaded and overwhelming.

**If you're leading AI transformation for a team or org:** the operator is a repeatable diagnostic. Run it on your priority workflows. The maps show where investment creates leverage. The value assessments help you prioritize. The skills sections tell you what capabilities to build. The gap reports tell you where the work isn't visible enough yet — and that visibility gap is the thing standing between your AI fluency numbers and actual business impact.

## How it works

**Want to try it first?** Grab one of the completed example audits in `examples/` and paste it into the operator. The LXD workflow audit (`examples/lxd-workflow-audit.md`) is the most complete — it'll produce a full confident map with risk callouts, skills, and measurement baseline. The status reporting audit (`examples/status-reporting-audit.md`) is the most interesting — it produces a "don't automate this" finding instead of a map.

### 1. Audit your workflow

Two ways to complete your audit:

- **Guided web form** — [Fill out the interactive audit form](https://alydperri.github.io/missing-middle-mapper/audit-form.html). Walks you through each question with built-in guidance. Copy the completed output and paste it into the operator.
- **Markdown template** — Fill out `audit-template.md` directly. Same questions, same help text, more flexibility for editing.

Four things matter most:

- **Define the outcome.** What is this workflow supposed to produce or enable? If you can't answer this clearly, the operator will flag it before doing anything else.
- **Describe the workflow's value.** What happens if it breaks? How many people does it affect? This helps prioritize whether this workflow is worth the investment.
- **Surface the judgment layer.** For each step: what would a new person get wrong? What information isn't written down? What causes breakdowns? These questions reveal where AI can actually help — not at the surface level, but at the level that makes experts expert.
- **Be honest about friction and AI usage.** What's tedious, what's cognitively heavy, what feels pointless. And if you're already using AI, describe how — the operator evaluates whether your current usage is working, needs guardrails, or should be reconsidered.

Completed examples are in `examples/` if you want to see what filled-out audits look like at different quality levels.

### 2. Run the operator

Open this folder in Claude Code. Provide your completed audit:

```
Produce an AI opportunity map from this workflow audit.
```

### 3. Get your output

The operator saves files to `output/`:

- **`{workflow-name}-opportunity-map.html`** — the map itself. Open in a browser. Each step expands to show the hidden judgment layer, classification rationale, risk callouts, and AI usage assessment. Includes measurement baseline and skills needed to act.
- **`{workflow-name}-gap-report.md`** — produced only when the audit is incomplete. A structured checklist of what to go find out, organized by step.

The operator also provides a brief chat summary with classification counts, confidence levels, and key findings.

## What to expect

**Clean audit → confident map.** All steps classified with rationale. Risk callouts, skills, measurement baseline. If any steps are compressed (they're actually sub-workflows), the operator flags them for deeper audits. No gap report — the audit was thorough enough.

**Partial audit → mixed map + gap report.** Well-documented steps get confident classifications. Thin steps get provisional classifications with a gap report explaining exactly what's missing. Address the gaps, re-run the operator, watch the map sharpen.

**Broken workflow → a finding, not a map.** If the audit reveals a workflow with no clear purpose and breakdowns at every step, the operator won't produce a map. It'll explain what the audit reveals and recommend clarifying purpose before redesigning. This is the operator protecting you from investing in the wrong thing.

## What's in the folder

```
missing-middle-mapper/
│
├── index.html                  ← Landing page.
├── audit-form.html             ← Guided web form for completing an audit.
│
├── CLAUDE.md                   ← Claude reads this first. Routes to everything else.
├── README.md                   ← You're here.
│
├── identity.md                 ← Who the operator is, what it owns, what it will and won't do.
├── rules.md                    ← The complete decision logic: classifications, confidence
│                                  states, AI usage assessment, gap report triggers, broken
│                                  workflow detection, edge cases.
│
├── audit-template.md           ← START HERE. Blank audit form with help text.
│
├── examples.md                 ← Three worked examples showing the operator's reasoning
│                                  on a clean, partial, and broken audit.
├── examples/
│   ├── lxd-workflow-audit.md           Complete audit (high quality, some AI in use)
│   ├── content-approval-audit.md       Partial audit (uneven quality, light AI usage)
│   └── status-reporting-audit.md       Broken audit (structurally unsound, no AI)
│
├── reference/
│   ├── classification-rubric.md        Four classifications with triggers, skills, multi-label rules
│   ├── gap-report-criteria.md          Blocking vs. sharpening gaps, when to produce/omit
│   ├── audit-quality-checklist.md      Input quality assessment and decision tree
│   ├── risk-categories.md              Risk patterns per classification + existing AI risks
│   ├── output-spec.md                  HTML output schema, CSS, interactions
│   └── lxd-example-opportunity-map.html  Fully built reference map
│
└── output/                     ← Operator saves all outputs here.
```

## The framework

This operator is built on the Missing Middle framework: the gap between AI fluency (people can use AI tools) and AI impact (AI meaningfully improves the work that matters).

The missing middle is work visibility. Most knowledge work depends on judgment, context, and expertise that lives in people's heads. AI cannot reliably improve work the organization cannot see, describe, or evaluate.

The operator enforces this by refusing to produce confident classifications until the judgment layer is visible. When a workflow step looks simple from the outside — "someone reviews it," "rep prepares" — but carries years of accumulated expertise underneath, the operator surfaces that layer. That's where AI creates real leverage: not by replacing the expert, but by making their judgment available at scale.
