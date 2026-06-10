# Risk Categories

Common risk patterns per classification. The operator uses these as a vocabulary to check against, then contextualizes to the specific step. Not every risk applies to every step — include a callout only when the risk is meaningful for the specific context.

---

## Automate risks

### Accountability gap
No one reviews the automated output because "the system handles it." Errors propagate silently. Most dangerous when the automation produces output that feeds directly into the next step without a human checkpoint.

**When to flag:** The automated sub-element produces output that others depend on, especially if the next step doesn't have its own quality check.

### Brittleness
Automation breaks silently when inputs change — a new field, a different format, a renamed category. The workflow keeps running but produces bad output that no one catches until downstream consequences appear.

**When to flag:** The automation depends on structured input (forms, templates, naming conventions) that could change, or the automation crosses systems that are maintained by different teams.

### Over-automation
The step has more judgment embedded in it than the audit revealed. What looked rule-followable turns out to have edge cases that the automation handles badly. Usually surfaces after the automation has been running for a while and encounters inputs the original rules didn't anticipate.

**When to flag:** The audit's judgment layer was light for this step (even if classified Confident), or the step's "checklist" description glosses over decision points that practitioners handle intuitively.

### Loss of context
Automated handoffs strip context that humans would naturally carry. A person forwarding a request includes background, tone, and priority cues. An automated routing rule forwards the data but not the context.

**When to flag:** The automated sub-element involves a handoff to another person or team, especially if the receiving party needs context to do their part well.

---

## Augment risks

### Plausible-but-wrong
AI produces confident-sounding output that is subtly incorrect. The surface looks right — the language is fluent, the format is correct, the logic appears sound — but the substance is off. Most dangerous when the person reviewing the output doesn't have deep expertise in the area.

**When to flag:** Always flag for Augment classifications. This is the most common and most dangerous augmentation risk. Emphasize it especially when the augmented output feeds into high-stakes decisions or when the reviewer may not catch subtle errors.

### Over-reliance and deskilling
Humans stop exercising their own judgment because the AI output "looks right." Over time, the human's ability to evaluate quality atrophies. The augmentation that was meant to amplify judgment gradually replaces it.

**When to flag:** The augmented step involves a skill that takes time to develop and could erode with disuse, or when junior practitioners are the primary users of the augmentation (they may never develop the judgment the augmentation was meant to amplify).

### Quality standard erosion
The bar gradually lowers because "AI did most of it" becomes the implicit standard. Work that would have been revised in a fully human process gets accepted because the effort to improve AI output feels disproportionate.

**When to flag:** The augmented step has implicit quality standards that haven't been codified, or the team's definition of "good enough" is likely to drift when production speed increases.

### Context drift
AI works from context (documents, standards, principles) that becomes outdated without anyone updating it. The augmentation keeps running but its recommendations gradually disconnect from current reality.

**When to flag:** The augmented step depends on reference material (style guides, policy documents, design principles) that changes periodically, or when the context AI uses isn't maintained by a specific owner.

### Anchoring
AI's first suggestion biases the human's subsequent judgment, even when the suggestion is wrong. The human's "independent review" is unconsciously shaped by what AI already proposed. Particularly risky in creative and evaluative work.

**When to flag:** The augmentation produces a draft, recommendation, or assessment that the human then reviews. The review is more independent if the human forms a preliminary view before seeing AI output.

---

## Keep Human risks

### Key-person dependency
The judgment that makes this step work lives in one or two people's heads. If they leave, get promoted, or are unavailable, the organization loses the ability to perform this step well. The step is correctly classified Keep Human, but the judgment is fragile because it hasn't been documented.

**When to flag:** The audit reveals that the judgment for this step depends heavily on specific individuals' experience, institutional memory, or relationship knowledge. Especially critical when those individuals are senior or close to role transitions.

### Under-documentation
The judgment is real and should stay human, but because it's not documented, it can't be taught, reviewed, or improved systematically. New people learn it slowly through osmosis. Quality depends on who you happen to learn from.

**When to flag:** The judgment layer reveals significant tacit knowledge ("what a new person would get wrong" has substantive answers), but no documented principles, heuristics, or decision frameworks exist.

### Bottleneck creation
Keeping a step fully human creates a throughput constraint as volume increases. The judgment is legitimate, but the step becomes the workflow's ceiling because it can only move as fast as the available humans.

**When to flag:** The step is already a bottleneck (audit says it slows the workflow down), volume is expected to increase, or the step depends on a small number of people who are also responsible for other work.

---

## Stop / Rethink risks

### Hidden dependencies
Something downstream relies on this step in ways the audit didn't capture. The step looks pointless from the inside, but removing it breaks something elsewhere — a report that feeds another team's process, a check that satisfies a compliance requirement, a ritual that serves a coordination function.

**When to flag:** Always flag for Stop / Rethink classifications. Before stopping or fundamentally redesigning, confirm with downstream consumers that nothing depends on the output.

### Organizational resistance
People are attached to the current process. They built it, they own it, or it's "how things are done here." Stopping or redesigning feels personal. This is not irrational — people invest identity in their work, and dismissing a process dismisses that investment.

**When to flag:** The step has been in place for a long time, was created by someone still in the organization, or involves multiple teams who would need to agree on the change.

### Premature stopping
The audit didn't surface all the value this step creates. Stopping it reveals that it was doing something useful that wasn't visible — maintaining a relationship, providing a coordination touchpoint, or serving as a backup for a fragile process elsewhere.

**When to flag:** The Stop / Rethink classification is based on absence of evidence (no one could articulate the value) rather than evidence of absence (confirmed that no value exists). These are different, and the distinction matters before acting.

### Loss of institutional memory
The step was inefficient, but it encoded knowledge — about how things work, who to talk to, what was tried before. Stopping the step without capturing that knowledge means the organization forgets. Especially relevant for recurring processes that serve as informal knowledge management.

**When to flag:** The judgment layer reveals that the step, despite being low-value as currently practiced, contains institutional knowledge that would be lost if the step disappeared entirely.

---

## Cross-cutting risks

### Change fatigue
Multiple classifications across the workflow mean multiple changes happening simultaneously. Even if each change is sound, the cumulative load on the team can be overwhelming. Implementation should be sequenced, not simultaneous.

**When to flag:** The map produces classifications that imply changes at 4+ steps. Note that implementation should be prioritized and phased.

### Measurement neglect
The team implements the classifications but doesn't measure whether the changes actually improved the workflow. Without measurement, there's no feedback loop — bad changes persist and good changes don't get credit.

**When to flag:** Always include in the map's measurement baseline section. The risk is not that measurement is hard; it's that the team skips it because the AI changes "feel" like improvements.

---

## Existing AI usage risks

These apply when AI is already being used in a step. They describe risks that may be actively materializing, not just potential future risks.

### Quality erosion in progress
The team's quality bar has already started drifting since AI was introduced. Work that would have been revised in a fully human process gets accepted because it came from AI and "looks fine." The erosion is gradual and often invisible to the people experiencing it.

**When to flag:** The audit describes reviewing AI output less carefully over time, or mentions that quality "seems fine" without specific criteria. Also flag when the team can't articulate what "good" AI output looks like vs. adequate AI output.

### Missing review layer
AI output is being used without a structured human review. The person may skim the output or spot-check occasionally, but there's no documented review criteria, no consistent process, and no one accountable for the quality of AI-generated work.

**When to flag:** The audit describes the review process in vague terms ("I read through it," "I fix what feels off") or acknowledges that review has become cursory. Especially critical when the AI output is customer-facing or feeds into high-stakes decisions.

### Deskilling in progress
The team is losing the ability to do the work without AI. Junior members may never develop the judgment the AI was meant to augment. Senior members may find their skills atrophying because they're reviewing AI output instead of producing original work.

**When to flag:** The audit reveals that team members couldn't do this step as well (or at all) without AI, or that newer team members have never done it without AI assistance. Distinct from over-reliance: deskilling is about capability loss, not just habit.

### Inconsistent AI practices
Different team members use AI differently for the same step — different tools, different prompts, different review practices. The output varies not because of judgment variation (which is normal) but because of tooling variation (which is a process problem).

**When to flag:** The audit mentions that "some people use AI and some don't" or describes different approaches without a shared standard. This creates inconsistent output quality and makes it hard to establish norms.

### AI solving the wrong problem
AI is being applied to a sub-element that should be Stop / Rethink, or is automating around a broken process instead of fixing it. The AI makes the broken thing faster or more consistent, but the underlying problem persists.

**When to flag:** The audit describes AI being used in a step that shows Stop / Rethink signals (unclear purpose, no one uses the output, exists by habit). This is the automation trap applied to existing AI usage — the same principle, just already happening.
