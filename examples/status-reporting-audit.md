# Workflow Audit: Weekly Cross-Functional Status Report

## Workflow-level framing

**Workflow name:** Weekly Cross-Functional Status Report

**Outcome:** Keep leadership informed about project status across teams.

**Frequency:** Weekly. Every Monday, distributed by end of day Tuesday.

**Owner:** Program Management Office, but in practice a rotating coordinator handles assembly.

**What "good" looks like:** The report goes out on time and looks complete.

---

## Workflow value

**What happens if this workflow breaks down or runs badly?** Honestly, we're not sure. The report has gone out late several times and no one followed up. The coordinator has tested this. If the report stopped entirely, it's unclear whether anyone would ask where it went. The theoretical consequence is that leadership loses visibility into project status, but the practical consequence appears to be nothing.

**How many people are affected?** The distribution list has about 20 people — leadership and senior managers. On the input side, 6-8 team leads are asked to contribute. The coordinator assembles it. So roughly 30 people are touched by this workflow. But "touched" and "affected" might be different — we don't have evidence that recipients act on the content.

**How much time does this workflow consume?** The coordinator spends 4-5 hours per week (chasing submissions, consolidating, formatting, reviewing, distributing). Team leads collectively spend 3-4 hours per week on submissions (when they actually submit). Total: roughly 7-9 person-hours per week, or 350-450 hours per year, on a report whose impact is unclear.

**Is this connected to something leadership cares about?** It was started by a previous VP who wanted cross-functional visibility. That VP left two years ago. No current leader has championed it or asked for changes. It continues because no one has decided to stop it.

**If AI made this significantly better, would the people doing the work feel it?** The coordinator would feel it — they'd get hours back. But the improvement they actually want isn't a better report. It's permission to stop producing a report no one reads. Making this workflow faster or more consistent would reduce the coordinator's pain, but it wouldn't create value if the output still isn't used.

---

## Step 1: Data Collection

**What triggers it:** A recurring Monday morning Slack reminder sent to team leads asking them to submit their status updates by noon.

**What it produces:** Individual status updates from each team lead (typically 6-8 teams), submitted via a shared Google Sheet or email or Slack (format varies by person).

### Judgment layer

**What would a new person get wrong?**
They wouldn't know who actually responds and who has to be chased. There's a distribution list but some people always respond, some never do, and some respond with one-liners that aren't usable. A new coordinator would spend all Monday afternoon figuring out who to follow up with.

**What information is used that isn't written down?**
Which team leads take the report seriously and which treat it as an annoyance. The coordinator knows to pre-write status for two teams whose leads never submit on time, pulling from Slack channels and project boards instead. This workaround is not documented and has never been questioned.

**What causes breakdowns?**
Late or missing submissions. Every single week, at least 2-3 teams submit late or not at all. The coordinator chases them, or just fills in based on what they can find. The format of submissions varies: some people send bullets in Slack, some fill in the Google Sheet, some send a paragraph in email. Reconciling these formats adds time.

**Who else is involved?**
6-8 team leads as submitters. The coordinator as assembler. No one else until distribution.

### Classification signals

**Checklist or judgment?** Could be a checklist if submissions were consistent. In practice, requires judgment about what to include when submissions are absent or unclear.

**Output consistency?** Low. The quality of input varies dramatically week to week. The coordinator compensates by normalizing everything, but this is invisible labor.

**Error cost?** Low. If a status is slightly wrong, no one has ever noticed or followed up.

**Bottleneck?** Yes. Chasing submissions is the most time-consuming part of the entire workflow.

**Friction:** This step is deeply frustrating. The coordinator spends 2-3 hours every Monday chasing people who don't want to do this. "It feels like pulling teeth for something nobody reads."

### Current AI usage

Not currently using AI in this step. The Slack reminder is a scheduled message, not AI.

---

## Step 2: Consolidation & Formatting

**What triggers it:** Enough submissions have arrived (or been fabricated from other sources) to assemble the report.

**What it produces:** A single formatted document consolidating all team updates into the standard report template.

### Judgment layer

**What would a new person get wrong?**
The template hasn't been updated in over a year. Some sections reference projects that have been completed or cancelled. A new person would try to fill every section; an experienced coordinator knows which sections to skip and which to repurpose for current priorities.

**What information is used that isn't written down?**
The coordinator knows what the report template should look like based on what leadership has complained about in the past. The template itself is outdated, so the coordinator informally adjusts it. There's also an unspoken length expectation: too short and it looks like no work was done, too long and no one reads it.

**What causes breakdowns?**
This step is pure manual labor. Copy-pasting from various sources, reformatting to match the template, reconciling conflicting information between teams, and making everything look consistent. The same data often appears in multiple tools (project board, Slack updates, the status sheet), and the coordinator has to decide which version is current.

**Who else is involved?**
Just the coordinator.

### Classification signals

**Checklist or judgment?** Mostly mechanical. Some judgment in reconciling conflicting information and deciding what to cut for length.

**Output consistency?** Moderate. The output looks consistent because one person normalizes everything, but the underlying data quality varies.

**Error cost?** Very low. "Honestly, if I got a number wrong, I don't think anyone would notice."

**Bottleneck?** Yes, in terms of time. This takes 1-2 hours every week and is entirely manual.

**Friction:** "This is the most mindless part of my job. I'm basically a human copy-paste machine for two hours every Tuesday morning."

### Current AI usage

Not currently using AI in this step. Consolidation is entirely manual.

---

## Step 3: Review & Cleanup

**What triggers it:** The consolidated draft is complete.

**What it produces:** A "reviewed" version ready for distribution. In practice, this means the coordinator re-reads it once and fixes obvious errors.

### Judgment layer

**What would a new person get wrong?**
There's nothing to get wrong because there's no review criteria. The coordinator reads it through once, fixes typos, and makes sure nothing looks obviously wrong. There's no substantive review — no one checks whether the status updates are accurate, meaningful, or actionable.

**What information is used that isn't written down?**
Nothing. This step is a habit, not a quality gate. The coordinator described it as "I skim it to make sure nothing embarrassing is in there."

**What causes breakdowns?**
This step doesn't break down because it doesn't do anything meaningful. It's a cursory pass that wouldn't catch a substantive error because no one is checking against ground truth.

**Who else is involved?**
No one. The coordinator reviews their own work.

### Classification signals

**Checklist or judgment?** Neither. It's a skim.

**Output consistency?** Consistently superficial.

**Error cost?** Theoretically medium (errors in the report could misinform leadership), but in practice low because the report doesn't inform decisions.

**Bottleneck?** No. This takes 15-20 minutes.

**Friction:** "It's not painful. It's just pointless. I'm proofreading a document I'm not sure anyone reads."

### Current AI usage

Not currently using AI in this step.

---

## Step 4: Distribution

**What triggers it:** The coordinator considers the report "done."

**What it produces:** The report sent to the distribution list via email, with a Slack notification in the #leadership channel.

### Judgment layer

**What would a new person get wrong?**
They might not know who's on the distribution list, which hasn't been updated since the last reorg. Some people on it have left the company. Some people who should be on it aren't.

**What information is used that isn't written down?**
The coordinator BCCs two people who asked to be added informally but were never added to the official list. The coordinator also knows to send it before 4 PM Tuesday because the CEO checks email around that time and once mentioned liking to see it.

**What causes breakdowns?**
Occasionally the report goes out late because steps 1-2 ran long. When it's late, no one follows up or asks where it is — the coordinator has tested this by sending it Wednesday a few times with no response.

**Who else is involved?**
No one. The coordinator sends it.

### Classification signals

**Checklist or judgment?** Pure checklist. Attach file, send to list, post in Slack.

**Output consistency?** High. Sending an email is sending an email.

**Error cost?** Very low. "If I sent it to the wrong list, I think it would take a week for anyone to notice."

**Bottleneck?** No. This takes 5 minutes.

**Friction:** Minimal. But the coordinator noted: "It's the easiest step, but also the one that makes me question the whole thing. I'm sending a report to people who may not open it."

### Current AI usage

Not currently using AI in this step.

---

## Step 5: Follow-Up & Action

**What triggers it:** The report has been distributed and leadership has (theoretically) read it.

**What it produces:** Actions, decisions, or follow-up conversations driven by the report contents.

### Judgment layer

**What would a new person get wrong?**
They would expect follow-up to happen. It doesn't. The coordinator described this step as: "There is no follow-up step. I listed it because the report is supposed to drive follow-up, but it doesn't. No one has ever come back to me with a question about the report. No one has ever referenced it in a meeting that I know of."

**What information is used that isn't written down?**
Nothing, because nothing happens.

**What causes breakdowns?**
The step itself is a breakdown. It exists as a concept (the report should inform decisions) but not as a practice.

**Who else is involved?**
Theoretically, leadership. In practice, no one.

### Classification signals

**Checklist or judgment?** N/A. The step doesn't happen.

**Output consistency?** N/A.

**Error cost?** The absence of follow-up means the report has no feedback loop. If the report contained incorrect or misleading information, no one would know.

**Bottleneck?** No. You can't bottleneck a step that doesn't happen.

**Friction:** "The friction isn't in this step. The friction is knowing that all the work in steps 1-4 leads to nothing."

### Current AI usage

Not currently using AI in this step. The step doesn't happen.
