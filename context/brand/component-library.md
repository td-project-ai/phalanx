# Slide Deck Component Library

> Master reference for all components available in the Phalanx slide engine. Components work with `base-template.html` and any theme CSS that satisfies [`_contract.md`](_contract.md).

---

## How to Use This File

1. Pick a **slide type** (dark, light, gray, accent) based on content weight
2. Pick a **component** from the library below
3. Copy the HTML snippet into `.slide-inner`
4. Brand-specific components are marked with their theme — only use them with the matching CSS

---

## Slide Types (All Themes)

| Class | Background | Best For |
|---|---|---|
| `.slide-dark` | Primary dark + optional pattern overlay | Hero/title, stats, key metrics, section covers |
| `.slide-light` | White | Tables, dense content, runbooks |
| `.slide-gray` | Light gray (`--light-gray`) | Two-column layouts, supporting/body slides |
| `.slide-accent` | Gradient + overlay | Section divider transitions, chapter breaks |

**Background sequencing rule:** No more than 2 consecutive slides with the same background. Plan variety during outlining.

| Position | Recommended |
|---|---|
| Opening | `.slide-dark` (hero) |
| Body | Alternate `.slide-gray` and `.slide-dark` |
| Dense content | `.slide-light` |
| Chapter breaks | `.slide-accent` (sparingly) |
| Closing | `.slide-dark` |

All slides get a footer gradient bar via `.slide-footer` automatically.

---

## Shared Components

These work on **every theme**. The CSS theming handles color/font adaptation.

### Layout

#### `.two-col`
Two-column 1:1 grid. Wrap columns inside `.slide-inner`.
```html
<div class="two-col">
  <div>
    <div class="two-col-header">Left Column</div>
    <!-- content -->
  </div>
  <div>
    <div class="two-col-header">Right Column</div>
    <!-- content -->
  </div>
</div>
```

---

### Metrics

#### `.stat-grid` / `.stat-item`
Large-number KPI grid. Auto-fits columns with `minmax(140px, 1fr)`.
```html
<div class="stat-grid">
  <div class="stat-item">
    <div class="stat-value">98%</div>
    <div class="stat-label">Uptime SLA</div>
  </div>
</div>
```
- Light/gray slides: white card with drop shadow
- Dark slides: semi-transparent with accent top border

#### `.metric-strip`
Single-row compact stat dashboard. Use when stats need less emphasis than `stat-grid`.
```html
<div class="metric-strip">
  <div class="metric-strip-item">
    <div class="metric-strip-value">99.9%</div>
    <div class="metric-strip-label">Availability</div>
  </div>
</div>
```

---

### Callouts & Highlights

#### `.callout`
Left-border quote or note box. Accent-colored 3px left border.
```html
<div class="callout">
  <div class="callout-label">Key Insight</div>
  <p>Supporting text here.</p>
</div>
```

#### `.highlight-grid` / `.highlight-box`
Auto-fit grid of fact/callout boxes with accent border and background tint.
```html
<div class="highlight-grid">
  <div class="highlight-box">
    <strong>Capability</strong>
    <p>Description of the capability.</p>
  </div>
</div>
```

---

### Cards

#### `.card-grid` / `.card`
Auto-fit card grid (`minmax(200px, 1fr)`). Cards get accent top border.
```html
<div class="card-grid">
  <div class="card">
    <div class="card-body">
      <h4>Card Title</h4>
      <p>Card body text.</p>
    </div>
  </div>
</div>
```

---

### Lists

#### `.program-element-list`
Icon-prefixed feature/principle list. Auto-fit grid, accent `▸` prefix.
```html
<ul class="program-element-list">
  <li>
    <div>
      <strong>Feature Name</strong>
      <p>Brief description of this feature or principle.</p>
    </div>
  </li>
</ul>
```

#### `.pillar-grid` / `.pillar`
Icon + label + text pillar columns. Centered, accent top border.
```html
<div class="pillar-grid">
  <div class="pillar">
    <div class="pillar-icon">⚡</div>
    <h3>Pillar Name</h3>
    <p>Supporting description.</p>
  </div>
</div>
```

---

### Tables

#### `.data-table`
Full-width bordered table. Accent-colored headers.
```html
<table class="data-table">
  <thead>
    <tr><th>Column A</th><th>Column B</th></tr>
  </thead>
  <tbody>
    <tr><td>Value</td><td>Value</td></tr>
  </tbody>
</table>
```

---

### Badges

#### `.badge` + modifier
Small inline label chips.

| Class | Color | Use |
|---|---|---|
| `.badge-bolt` / `.badge-primary` | Primary accent | Active, featured |
| `.badge-infrared` / `.badge-danger` | Red/danger | Risk, critical, required |
| `.badge-neutral` | Gray | Informational, secondary |
| `.badge-success` | Green | Complete, approved, healthy |

```html
<span class="badge badge-primary">Active</span>
<span class="badge badge-danger">Critical</span>
```

---

### Code

#### `.code-block`
Dark monospace code snippet with accent left border.
```html
<div class="code-block">
  terraform apply -var-file="prod.tfvars"
</div>
```

---

### Visual Flow Components

These components provide structural variety beyond box grids. Match the visual shape to the content shape.

| Content Shape | Component | Avoid |
|---|---|---|
| Sequential steps (3–6) | `.step-flow`, `.step-list` | Numbered card grids |
| Layered architecture | `.layer-stack`, `.annotated-stack` | Two-col bullet lists |
| Central coordinator + satellites | `.hub-spoke` | Card grid around a heading |
| Transformation / improvement | `.before-after` | Two-col with "Before"/"After" |
| Continuous cycle | `.process-loop` | Numbered highlight boxes |
| Growth narrative | `.ascend-timeline` | Bullet list with dates |
| Compact metrics | `.metric-strip` | `stat-grid` when space is tight |

#### `.step-flow` / `.step-node`
Horizontal numbered step nodes with arrow connectors.
```html
<div class="step-flow">
  <div class="step-node">
    <div class="step-num">1</div>
    <div class="step-title">Assess</div>
    <div class="step-desc">Evaluate current state.</div>
  </div>
  <div class="step-arrow"><div class="step-arrow-line"></div></div>
  <div class="step-node">
    <div class="step-num">2</div>
    <div class="step-title">Plan</div>
    <div class="step-desc">Define target architecture.</div>
  </div>
</div>
```

#### `.step-list` / `.step-item`
Vertical numbered steps with large ghost numerals. More text-dense than step-flow. Best for 3–6 steps.
```html
<div class="step-list">
  <div class="step-item">
    <div class="step-num">1</div>
    <div class="step-content">
      <strong>Step Title</strong>
      <p>Step description with supporting detail.</p>
    </div>
  </div>
</div>
```

#### `.before-after`
Side-by-side transformation panels with arrow divider.
```html
<div class="before-after">
  <div class="before-panel">
    <h4>Current State</h4>
    <ul><li>Manual processes</li></ul>
  </div>
  <div class="ba-arrow">→</div>
  <div class="after-panel">
    <h4>Target State</h4>
    <ul><li>Automated pipelines</li></ul>
  </div>
</div>
```

#### `.layer-stack` / `.layer-row`
Stacked tier rows for architecture layers.
```html
<div class="layer-stack">
  <div class="layer-row">
    <div class="layer-item">Presentation Layer</div>
  </div>
  <div class="layer-row">
    <div class="layer-item">Business Logic</div>
    <div class="layer-item">API Gateway</div>
  </div>
  <div class="layer-row">
    <div class="layer-item">Data Layer</div>
  </div>
</div>
```

#### `.hub-spoke`
Radial layout with SVG connector lines.
```html
<div class="hub-spoke">
  <div class="hub-center">Orchestrator</div>
  <div class="hub-spoke-node" style="--angle: 0deg">Service A</div>
  <div class="hub-spoke-node" style="--angle: 90deg">Service B</div>
  <div class="hub-spoke-node" style="--angle: 180deg">Service C</div>
  <div class="hub-spoke-node" style="--angle: 270deg">Service D</div>
</div>
```

#### `.annotated-stack`
Vertical layers with side annotation notes.
```html
<div class="annotated-stack">
  <div class="annotated-stack-layers">
    <div class="layer-row"><div class="layer-item">CDN / WAF</div></div>
    <div class="layer-row"><div class="layer-item">Load Balancer</div></div>
    <div class="layer-row"><div class="layer-item">App Tier</div></div>
  </div>
  <div class="annotated-stack-annotations">
    <div class="annotation">Edge caching reduces origin load by 80%</div>
  </div>
</div>
```

#### `.process-loop`
Circular SVG ring with positioned nodes for continuous cycles.
```html
<div class="process-loop">
  <svg class="loop-ring"><!-- circle path --></svg>
  <div class="loop-center">DevOps</div>
  <div class="loop-node" style="--pos: 0">Plan</div>
  <div class="loop-node" style="--pos: 1">Build</div>
  <div class="loop-node" style="--pos: 2">Deploy</div>
  <div class="loop-node" style="--pos: 3">Monitor</div>
</div>
```

#### `.ascend-timeline`
Ascending columns for growth/maturity narratives.
```html
<div class="ascend-timeline">
  <div class="ascend-node" style="--level: 1">
    <div class="ascend-label">Phase 1</div>
    <div class="ascend-desc">Foundation</div>
  </div>
  <div class="ascend-node" style="--level: 2">
    <div class="ascend-label">Phase 2</div>
    <div class="ascend-desc">Scale</div>
  </div>
  <div class="ascend-node" style="--level: 3">
    <div class="ascend-label">Phase 3</div>
    <div class="ascend-desc">Optimize</div>
  </div>
</div>
```

#### `.funnel` / `.funnel-bar`
Vertical decaying bars for pipeline/conversion visualization.
```html
<div class="funnel">
  <div class="funnel-bar" style="--bar-width: 100%; --bar-color: var(--accent)">
    <span class="funnel-label">Leads: 1,000</span>
  </div>
  <div class="funnel-bar" style="--bar-width: 60%; --bar-color: var(--accent-light)">
    <span class="funnel-label">Qualified: 600</span>
  </div>
  <div class="funnel-bar" style="--bar-width: 25%; --bar-color: var(--accent-dark)">
    <span class="funnel-label">Closed: 250</span>
  </div>
</div>
```

---

### Comparison & Decision

#### `.comparison-card`
Side-by-side two-panel layout with center VS divider.
```html
<div class="comparison-card">
  <div class="comparison-panel">
    <div class="comparison-panel-label">Option A</div>
    <ul><li>Point one</li></ul>
  </div>
  <div class="comparison-divider">
    <span class="comparison-vs">VS</span>
  </div>
  <div class="comparison-panel">
    <div class="comparison-panel-label">Option B</div>
    <ul><li>Point one</li></ul>
  </div>
</div>
```

---

### Timelines

#### `.h-timeline` (Horizontal)
Left-to-right timeline with dot markers. Dot states: `complete`, `active`, `future`.
```html
<div class="h-timeline">
  <div class="timeline-item">
    <div class="timeline-dot complete"></div>
    <div class="timeline-date">Q1 2026</div>
    <div class="timeline-label">Phase Name</div>
    <div class="timeline-desc">Description.</div>
  </div>
  <div class="timeline-item">
    <div class="timeline-dot active"></div>
    <div class="timeline-date">Q2 2026</div>
    <div class="timeline-label">Current Phase</div>
    <div class="timeline-desc">In progress.</div>
  </div>
</div>
```

---

### Operational

#### `.runbook-phases` / `.runbook-phase`
Numbered operational step phase cards. Accent top border, arrow-prefixed list items.
```html
<div class="runbook-phases">
  <div class="runbook-phase">
    <div class="runbook-phase-header">
      <span class="phase-num">01</span>
      <span class="phase-title">Assess</span>
    </div>
    <ul>
      <li>Step one</li>
      <li>Step two</li>
    </ul>
  </div>
</div>
```

#### `.process-flow` / `.process-step`
Horizontal arrow-connected steps. More compact than runbook phases — suited for 4–6 quick steps.
```html
<div class="process-flow">
  <div class="process-step">
    <div class="process-step-arrow"></div>
    <div class="process-step-num">Step 01</div>
    <div class="process-step-title">Step Name</div>
    <p>Short description.</p>
  </div>
</div>
```
Last step auto-hides the arrow via `:last-child`.

---

### Quotes

#### `.quote-block`
Oversized decorative pull quote with attribution. Decorative `"` glyph renders automatically.
```html
<div class="quote-block">
  <p class="quote-text">The quote text goes here.</p>
  <div class="quote-attribution">Person Name</div>
  <div class="quote-role">Title · Organization</div>
</div>
```

---

### Maturity & Progress

#### `.maturity-scale`
5-level horizontal capability scale. States: `complete`, `active`, `future`.
```html
<div class="maturity-scale">
  <div class="maturity-track">
    <div class="maturity-level complete">
      <div class="maturity-num">1</div>
      <div class="maturity-label">Aware</div>
    </div>
    <div class="maturity-level active">
      <div class="maturity-num">2</div>
      <div class="maturity-label">Building</div>
    </div>
    <div class="maturity-level future">
      <div class="maturity-num">3</div>
      <div class="maturity-label">Scaling</div>
    </div>
  </div>
  <div class="maturity-desc">Current state description.</div>
</div>
```
Scale supports 3–6 levels via `auto-fit`.

---

### Data Visualization

#### `.icon-grid` / `.icon-item`
Grid items with prominent emoji/icon prefix. Use for tool stacks, capabilities, feature lists.
```html
<div class="icon-grid">
  <div class="icon-item">
    <span class="icon-glyph">🤖</span>
    <div class="icon-label">Tool Name</div>
    <div class="icon-desc">Short description.</div>
  </div>
</div>
```

#### `.split-stat`
Single large metric left-aligned with explanatory text right.
```html
<div class="split-stat">
  <div class="split-stat-figure">
    <span class="split-stat-value">40+</span>
    <span class="split-stat-unit">OpCos</span>
  </div>
  <div class="split-stat-divider"></div>
  <div class="split-stat-body">
    <span class="split-stat-label">Metric label</span>
    <p class="split-stat-desc">Supporting context.</p>
  </div>
</div>
```

#### `.kpi-grid` / `.kpi-card`
Metric cards with trend indicators. Use `kpi-trend-up` (green), `kpi-trend-down` (red), `kpi-trend-flat` (gray).
```html
<div class="kpi-grid">
  <div class="kpi-card">
    <div class="kpi-value">94%</div>
    <div class="kpi-trend kpi-trend-up">↑ +6pts</div>
    <span class="kpi-label">Metric Name</span>
    <div class="kpi-context">Baseline comparison.</div>
  </div>
</div>
```

#### `.tag-cluster` / `.tag-group`
Flexible pill tags in multiple color variants.
```html
<div class="tag-cluster">
  <div class="tag-group">
    <div class="tag-group-label">Category</div>
    <span class="tag tag-primary">Primary</span>
    <span class="tag tag-accent">Alert</span>
    <span class="tag tag-success">Certified ✓</span>
    <span class="tag">Neutral</span>
  </div>
</div>
```

| Variant | Use |
|---------|-----|
| `tag-primary` | Key skills, confirmed items |
| `tag-accent` | Required, critical, blockers |
| `tag-success` | Completed, certified, passed |
| *(no modifier)* | Baseline, neutral, pending |

---

## Navigation & JS Conventions (All Themes)

- `.nav-link` must have `data-slide="N"` (0-indexed)
- Non-clickable section labels: `.nav-section-label`
- Visual separators: `.nav-divider`
- `const TOTAL_SLIDES = N` in `<script>` must match slide count
- `goToSlide(index)` is the only navigation function
- Keyboard: Arrow keys, Space/PageDown, Home/End
- Touch swipe threshold: 50px · Wheel debounce: 50ms

---

## Creating a New Presentation (All Themes)

1. Copy `base-template.html` → `workspace/<project>/presentation.html`
2. Change the `<link>` theme to the desired CSS (`minimal.css`, `credera.css`, `quanta.css`)
3. For variants, add `data-variant` to `<html>` (e.g., `data-variant="sage"`)
4. Update `<title>`, `.nav-brand`, and `TOTAL_SLIDES`
5. Replace placeholder slides — keep `data-index` sequential from 0
6. Update `.nav-list` — one `.nav-link[data-slide]` per navigable slide
7. Set `progress-fill` initial width: `(1 / TOTAL_SLIDES * 100)%`

---

## Component Variety Rule

No more than 2 consecutive slides may use the same component category:

| Category | Components |
|---|---|
| Box grids | `card-grid`, `highlight-grid`, `icon-grid`, `kpi-grid` |
| Flows | `step-flow`, `process-flow`, `process-loop`, `funnel` |
| Structure | `layer-stack`, `annotated-stack`, `hub-spoke` |
| Comparison | `before-after`, `comparison-card` |
| Process | `runbook-phases`, `step-list` |
| Metrics | `stat-grid`, `metric-strip`, `split-stat` |
| Timeline | `h-timeline`, `ascend-timeline`, `maturity-scale` |

Plan the component sequence during outlining, not during slide generation.

---

# Brand-Specific Extensions

## Quanta Brand

### Color Tokens

| Token | Value | Name |
|---|---|---|
| `--bolt` | `#F0941C` | Bolt Orange — primary brand |
| `--bolt-light` | `#FFAE4D` | Bolt tint |
| `--infrared` | `#CD0A1B` | Infrared Red — accent/danger |
| `--carbon` | `#221F1F` | Carbon Black — primary dark |
| `--carbon-light` | `#3A3535` | Carbon +1 |
| `--carbon-lighter` | `#575454` | Carbon +2 |
| `--carbon-lightest` | `#8B8A8A` | Carbon +3, muted |

Contract aliases: `--primary` → Carbon, `--accent` → Bolt, `--accent-dark` → Infrared.

### Typography

| Role | Font | Fallback | Notes |
|---|---|---|---|
| Headings | Oswald | Arial, sans-serif | Always uppercase, letter-spacing 0.04em |
| Body | Source Sans 3 | Arial, sans-serif | Weight 300/400/600 |

Official Quanta typefaces: Alternate Gothic Extra Condensed ATF (headings), Proxima Nova (body). Oswald and Source Sans 3 are web substitutes.

### Pattern Overlays

`.slide-dark` and `.slide-accent` include automatic diagonal-hatched overlays matching the Quanta brand pattern system. No extra markup needed.

### Logo Usage

- **Horizontal format** preferred for most applications
- **Vertical format** when layout demands
- **Icon only** for small spaces (social avatars, favicons)
- Never use wordmark alone — always pair with icon
- Clear space: width of "QU" letters minimum
- Minimum size: 70px digital (dimensional), 50px (flat)

### Photography

- Authentic, spontaneous — real employees, real work
- No posed shots, no stock photos for external use
- Safety-approved for all field operations
- Represent full workforce diversity
- Prioritize clean energy for sustainability content

### Sub-Branding

- **Quanta-operated companies**: Quanta icon + company name in brand typeface
- **Independently operated**: "A QUANTA SERVICES COMPANY" below operating company logo

---

## Credera Brand

### Color Tokens

Colors extracted from the 2024 Credera Global PowerPoint Accelerator PPTX theme.

| Token | Value | Role |
|---|---|---|
| `--credera-red` | `#E55F4C` | Brand mark, logo, bookend backgrounds |
| `--accent` | `#E55F4C` | Interactive accent (borders, highlights, badges) |
| `--accent-light` | `#F08878` | Hover states, light accents |
| `--accent-dark` | `#C94A38` | Pressed states, emphasis |
| `--navy` | `#3A3A3A` | Primary dark / text |
| `--slate-blue` | `#496986` | Extended palette |
| `--sky-blue` | `#5CA2D1` | Charts, secondary highlights |
| `--warm-gold` | `#E9A867` | Callouts, Sage variant accent |
| `--sage` | `#6A9E98` | Subtle accents, Sage variant |
| `--light-gray` | `#F8F5F2` | Page backgrounds, covers |
| `--ice-blue` | `#D7ECF3` | Light info backgrounds |

### Theme Variants

| Variant | `data-variant` | Dark Tone | Accent | Usage |
|---|---|---|---|---|
| Coral + Charcoal | *(default)* | `#3A3A3A` | `#E55F4C` | Default, most versatile |
| Sage + Gold | `"sage"` | `#2A3D36` | `#E9A867` | Sustainability, growth, advisory |
| Warm + Slate | `"warm"` | `#4A3728` | `#496986` | Understated, enterprise, finance |

Apply via `data-variant="sage"` or `data-variant="warm"` on `<html>`.

### Typography

- **Headlines**: Source Serif Pro SemiBold, uppercase, letter-spacing +2px
- **Subheadlines**: Source Serif Pro, regular, uppercase, letter-spacing +1px
- **Labels**: Lato Bold, all-caps, character spacing +0.5
- **Body**: Lato, line height 1.6
- **Icons**: Font Awesome 6 — never emojis

### Logo (SVG)

Nav sidebar — place inside `.nav-brand`:
```html
<div class="nav-brand">
  <svg class="nav-logo" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 32" fill="none">
    <!-- 8 path elements: brand mark + "Credera" letterforms -->
    <!-- Use fill="currentColor" to inherit text color -->
  </svg>
</div>
```

Cover/bookend — place inside `.cover-logo` with `opacity: 0.12` for watermark:
```html
<div class="cover-logo">
  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 32" fill="none">
    <!-- Same paths, fill="var(--accent)" -->
  </svg>
</div>
```

### Credera-Only Components

These components are **only available** with `credera.css`:

| Component | Classes | Purpose |
|---|---|---|
| Cover slide | `.slide-cover`, `.cover-date`, `.cover-title`, `.cover-logo` | Branded cover with logo watermark |
| Callout accent | `.callout-accent` | Red-branded callout (uses `--credera-red`) |
| Success highlight | `.success-highlight`, `.highlight-text` | Large gradient callout with accent heading |
| Question items | `.question-item`, `.question-number`, `.question-text` | Discussion prompt rows |
| Program elements | `.program-elements`, `.program-element` | Horizontal dark-slide panels |
| Capabilities band | `.capabilities-band`, `.capabilities-grid` | Full-width dark capability showcase |
| Equation layout | `.equation-layout`, `.equation-column`, `.equation-operator` | Visual A + B = C equations |
| Materials grid | `.materials-grid`, `.material-section`, `.material-thumbs` | Thumbnail sections for deliverables |
| Participants grid | `.participants-grid`, `.participant-group` | Stakeholder group cards |
| Card variants | `.card-dark`, `.card-clickable`, `.card-arrow`, `.card-icon`, `.card-type`, `.card-img` | Extended card styles |
| Status badge | `.status-badge` | Accent-bg inline badge |

### Credera Section Color Strategy

- **Title/closing**: Bookend with `.slide-dark` or Credera Red backgrounds (sparingly)
- **Dark sections**: `.slide-dark`, `.slide-accent` for high-impact
- **Content**: `.slide-light` or `.slide-gray` for text-heavy slides
- **Never mix** accent colors within the same section

---

## Minimal Theme

The Minimal theme is brand-agnostic — system fonts, slate/blue palette. Clone `minimal.css` to create a new brand theme.

### Color Tokens

| Token | Value |
|---|---|
| `--primary` | `#0F172A` (Slate 900) |
| `--accent` | `#2563EB` (Blue 600) |
| `--accent-light` | `#60A5FA` (Blue 400) |
| `--light-gray` | `#F1F5F9` (Slate 100) |

### Typography

System fonts only — no external dependencies:
- Headings: `'Segoe UI', system-ui, sans-serif`
- Body: Same stack

No brand-specific components. All shared components work with the Minimal theme.

---

## Known Limitations

- Quanta fonts (Oswald, Source Sans 3) load from Google Fonts — requires internet
- Credera uses Font Awesome 6 from CDN — requires internet
- Minimal theme uses system fonts — works offline
- Font sizes use `clamp()` for responsive scaling; works at standard desktop resolutions
