# Output Specification

The operator produces up to three outputs, saved to the `output/` directory at the root of the workspace.

A complete working example exists at `reference/lxd-example-opportunity-map.html`. When in doubt about structure, styling, or interaction, match that file.

---

## Primary output: HTML opportunity map

A self-contained HTML file. All CSS is inline in a `<style>` block. All JS is inline in a `<script>` block. No external dependencies except Google Fonts.

**Filename convention:** `{workflow-name}-opportunity-map.html` using lowercase kebab-case.

### Required sections (in order)

1. **Header** — workflow name, subtitle ("What's visible. What can change." in italicized muted text), team/owner, date. Two-column grid: title left, meta right. All header content comes from the audit input (workflow name, owner, current date). Do not carry over company names, team names, or dates from the reference example.

2. **Value context bar** — compact horizontal bar below the header. Flex row of label-value pairs separated by vertical dividers. Consequence of failure uses `.high` class (red) when high. Omit this section entirely when value data is absent.

3. **Legend** — four color-coded dot-label pairs (Automate, Augment, Keep Human, Stop / Rethink) plus a right-aligned hint: "↓ Expand each step to see the judgment layer."

4. **Section label: "Workflow Steps"**

5. **Workflow steps** — expandable rows (see Step Row Structure below)

6. **Section label: "Summary"**

7. **Summary cards** — four-column grid, one card per classification. Each card: colored label, large count (Instrument Serif, 36px), short description.

8. **Section label: "Measurement Baseline"**

9. **Measurement baseline** — header ("How we'll know it worked" / "Baseline → target"), three metric cards in a grid. Each card: metric name, baseline value, arrow, target value (target colored with `--augment` blue).

10. **Section label: "Skills to Act on This Map"**

11. **Skills section** — header label ("Capabilities needed to execute"), then skill entries in a two-column grid: skill name (220px, DM Mono uppercase) + contextual explanation (1fr, DM Sans 12px). Entries separated by border-bottom.

12. **Footer note** — contextual note in DM Mono 10px, muted.

### Conditional sections

13. **Workflow-level finding** — when structural breakdown is detected. Appears before the workflow steps section. States the finding, the evidence, and the recommendation.

14. **Recommended next audits** — when compressed steps are flagged. Appears after the footer note.

---

## Step row structure

### Collapsed state

Four-column grid: step number (40px) | step content (1fr) | tags + badges (auto) | toggle (52px)

```html
<div class="step-top" onclick="toggleStep(this)">
  <div class="step-number">01</div>
  <div class="step-main">
    <div class="step-name">Step Name</div>
    <div class="step-desc">One-line description</div>
  </div>
  <div class="step-tags">
    <span class="tag tag-automate">Automate</span>
    <span class="tag tag-augment">Augment</span>
    <!-- Confidence badges when applicable: -->
    <span class="badge-provisional">Provisional</span>
    <span class="badge-conditional">Conditional</span>
  </div>
  <div class="toggle"><span class="toggle-icon">+</span></div>
</div>
```

Toggle shows `+` when collapsed, rotates 45° to `×` when open.

### Expanded: judgment layer

Hidden by default (`display: none`), toggled to `display: block` via `.open` class.

```html
<div class="judgment-layer">
  <div class="judgment-label">Hidden judgment layer</div>
  <div class="judgment-grid">
    <div class="judgment-col">
      <h4>What actually happens here</h4>
      <ul><li>...</li></ul>
    </div>
    <div class="judgment-col">
      <h4>Where it breaks down</h4>
      <ul><li>...</li></ul>
    </div>
  </div>

  <!-- Conditional note (when step has Conditional classification): -->
  <div class="conditional-note">
    <strong>Conditional:</strong> Description of the condition and both paths.
  </div>

  <!-- Provisional note (when step has Provisional classification): -->
  <p class="provisional-note">
    This classification is provisional — see gap report for what's missing.
  </p>

  <div class="opportunity-row">
    <!-- One opp-block per classification -->
  </div>
</div>
```

### Expanded: opportunity blocks

Flex row (`flex-wrap: wrap`, `gap: 12px`). Each block uses `flex: 1 1 200px` so they adapt to the number of classifications.

```html
<div class="opp-block automate">
  <div class="opp-label">Automate</div>
  <div class="opp-text">Scope description — what sub-element this applies to</div>

  <!-- AI usage status (when AI is already in use for this sub-element): -->
  <div class="ai-status status-working">In use — working</div>
  <!-- or: -->
  <div class="ai-status status-guardrails">In use — needs guardrails</div>
  <!-- or: -->
  <div class="ai-status status-reconsider">In use — reconsider</div>
  <!-- Omit entirely when AI is not yet applied (the default) -->

  <!-- Risk callout (when applicable): -->
  <span class="risk-toggle" onclick="toggleRisk(this)">
    <span class="risk-icon">⚠</span> Watch for
  </span>
  <div class="risk-content">
    Contextualized risk description.
  </div>
</div>
```

Risk callouts: collapsed by default. On click, the `.risk-content` toggles to `.open` (display: block) and the toggle text changes to "⚠ Watch for ↑". `event.stopPropagation()` prevents triggering the parent step toggle.

Not every opportunity block needs a risk callout. Include only when the risk is specific and actionable for this step. See `reference/risk-categories.md` for the risk vocabulary.

---

## CSS variables

```css
:root {
  /* Backgrounds */
  --bg: #0e0f11;
  --surface: #15171a;
  --surface2: #1c1f23;

  /* Borders */
  --border: #2a2d32;
  --border-light: #323640;

  /* Text */
  --text: #e8e9eb;
  --text-muted: #7a7f8a;
  --text-dim: #4a4f5a;

  /* Classifications */
  --automate: #4ade80;
  --automate-bg: #0d2b1a;
  --automate-border: #1a4a2e;

  --augment: #60a5fa;
  --augment-bg: #0d1e35;
  --augment-border: #1a3555;

  --human: #f59e0b;
  --human-bg: #2a1f08;
  --human-border: #4a3510;

  --stop: #f87171;
  --stop-bg: #2a0f0f;
  --stop-border: #4a1a1a;

  /* Accents */
  --accent: #a78bfa;       /* purple — Conditional badges, labels, skills header */
  --warning: #f97316;      /* orange — risk ⚠ icon */
}
```

### Typography

| Role | Font | Size | Weight | Style |
|---|---|---|---|---|
| Labels, metadata, tags | DM Mono | 9-10px | 400 | uppercase, letter-spaced |
| Headings (h1, h3) | Instrument Serif | 18-32px | 400 | normal or italic |
| Body, descriptions | DM Sans | 11-14px | 300-400 | normal |
| Large counts | Instrument Serif | 36px | 400 | — |

Google Fonts import:
```
DM Mono:ital,wght@0,300;0,400;0,500;1,300
Instrument Serif:ital@0;1
DM Sans:wght@300;400;500
```

### Classification tags

```css
.tag { font-family: 'DM Mono'; font-size: 9px; letter-spacing: 0.08em;
       text-transform: uppercase; padding: 3px 8px; border-radius: 3px; }

.tag-automate { background: var(--automate-bg); color: var(--automate); border: 1px solid var(--automate-border); }
.tag-augment  { background: var(--augment-bg);  color: var(--augment);  border: 1px solid var(--augment-border); }
.tag-human    { background: var(--human-bg);    color: var(--human);    border: 1px solid var(--human-border); }
.tag-stop     { background: var(--stop-bg);     color: var(--stop);     border: 1px solid var(--stop-border); }
```

### Confidence badges

```css
.badge-provisional {
  /* Same base as .tag */
  color: var(--text-muted);
  border: 1px dashed var(--border-light);
  background: transparent;
}

.badge-conditional {
  color: var(--accent);
  border: 1px solid var(--accent);
  background: transparent;
}
```

Confident steps have no badge. Confidence is the default state.

### Conditional note

```css
.conditional-note {
  margin-top: 14px;
  padding: 10px 14px;
  border-left: 2px solid var(--accent);
  background: rgba(167, 139, 250, 0.05);
  border-radius: 0 3px 3px 0;
  font-size: 12px;
  color: var(--text-muted);
  line-height: 1.55;
}

.conditional-note strong {
  color: var(--accent);
  font-weight: 500;
}
```

### Provisional note

```css
.provisional-note {
  font-family: 'DM Mono', monospace;
  font-size: 9px;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--text-dim);
  margin-top: 14px;
}
```

### Risk callouts

```css
.risk-toggle {
  display: block;
  margin-top: 8px;
  font-family: 'DM Mono', monospace;
  font-size: 9px;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  color: var(--text-dim);
  cursor: pointer;
  padding: 6px 0 2px;
  border-top: 1px solid rgba(255,255,255,0.04);
  user-select: none;
}

.risk-toggle .risk-icon {
  color: var(--warning);    /* #f97316 orange */
}

.risk-toggle:hover {
  color: var(--text-muted);
}

.risk-content {
  display: none;
  font-size: 11px;
  color: var(--text-muted);
  line-height: 1.55;
  padding: 8px 0 4px 12px;
  border-left: 1px solid var(--border);
  margin-top: 4px;
}

.risk-content.open {
  display: block;
}
```

### AI usage status indicators

```css
.ai-status {
  font-family: 'DM Mono', monospace;
  font-size: 9px;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  padding: 3px 8px;
  border-radius: 3px;
  margin-top: 8px;
  display: inline-block;
}

.status-working {
  color: var(--automate);              /* green */
  background: var(--automate-bg);
  border: 1px solid var(--automate-border);
}

.status-guardrails {
  color: var(--warning);               /* orange */
  background: rgba(249, 115, 22, 0.08);
  border: 1px dashed var(--warning);
}

.status-reconsider {
  color: var(--stop);                  /* red */
  background: var(--stop-bg);
  border: 1px solid var(--stop-border);
}
```

"Not yet applied" is the default and gets no indicator — same principle as Confident getting no badge.

### Value context bar

```css
.value-bar {
  background: var(--surface);
  border-bottom: 1px solid var(--border);
  padding: 14px 20px;
  display: flex;
  flex-wrap: wrap;
  gap: 28px;
  align-items: center;
}

.value-item { display: flex; align-items: baseline; gap: 8px; }
.value-label { font-family: 'DM Mono'; font-size: 9px; letter-spacing: 0.14em; text-transform: uppercase; color: var(--text-dim); }
.value-value { font-family: 'DM Mono'; font-size: 10px; letter-spacing: 0.06em; color: var(--text-muted); }
.value-value.high { color: var(--stop); }      /* red for high-consequence */
.value-divider { width: 1px; height: 14px; background: var(--border); flex-shrink: 0; }
```

### Layout

- Max width: 960px, centered
- Page padding: 48px 32px 80px (mobile: 32px 16px 60px)
- Steps: 3px gap, 6px border-radius
- Section labels: DM Mono 10px uppercase, `--text-dim`, 20px bottom margin

### Animations

```css
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(12px); }
  to   { opacity: 1; transform: translateY(0); }
}
```

Staggered per step: 0.15s, 0.22s, 0.29s, 0.36s, 0.43s, 0.50s (0.07s increment).
Summary: 0.6s delay. Measurement: 0.75s. Skills: 0.85s. Footer: 0.95s.

### Responsive (max-width: 640px)

- Body padding: 32px 16px 60px
- Header: single column
- Header meta: left-aligned
- Step top: 36px first column
- Judgment grid: single column
- Opportunity row: single column (blocks stack)
- Skill entries: single column
- Summary grid: 2 columns
- Metrics grid: single column
- Value bar: 16px gap, dividers hidden

---

## JavaScript

Two functions, both inline in a `<script>` block at the end of `<body>`:

```javascript
function toggleStep(topEl) {
  const step = topEl.closest('.step');
  const layer = step.querySelector('.judgment-layer');
  const toggle = topEl.querySelector('.toggle');
  const isOpen = layer.classList.contains('open');
  layer.classList.toggle('open', !isOpen);
  toggle.classList.toggle('open', !isOpen);
}

function toggleRisk(el) {
  event.stopPropagation();   // prevent triggering parent step toggle
  const content = el.nextElementSibling;
  const isOpen = content.classList.contains('open');
  content.classList.toggle('open', !isOpen);
  el.innerHTML = isOpen
    ? '<span class="risk-icon">⚠</span> Watch for'
    : '<span class="risk-icon">⚠</span> Watch for ↑';
}
```

---

## Secondary output: gap report (when warranted)

A separate markdown file produced only when one or more steps carry a Provisional classification.

**Filename convention:** `{workflow-name}-gap-report.md`. Saved alongside the HTML map in `output/`.

**Structure:**
- Brief summary: how many steps are Provisional, how many gaps are blocking vs. sharpening
- Per-step entries for each Provisional step:
  - Step name and current provisional classification
  - What specific information is missing
  - Whether the gap is blocking or sharpening
  - Actionable prompts for what to find out
- If the gap pattern is diagnostic, state this as a finding at the top
- For Provisional steps, note that skills assessment is deferred

Not produced when all steps are Confident or Conditional.

---

## Tertiary output: chat summary

Brief in-chat pointer after saving files:
- Steps mapped and classification distribution
- Confidence distribution
- Whether a gap report was produced and critical gaps
- Whether a workflow-level finding was issued
- File paths where outputs were saved
