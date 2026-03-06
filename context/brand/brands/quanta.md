# Quanta Services — Brand Theme Reference

> Brand-specific tokens, typography, patterns, and guidelines for the Quanta HTML slide theme (`quanta.css`). All shared components from [`../component-library.md`](../component-library.md) work with this theme — this file covers only what is unique to Quanta.

---

## Color Tokens

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

---

## Typography

| Role | Font | Fallback | Notes |
|---|---|---|---|
| Headings | Oswald | Arial, sans-serif | Always uppercase, letter-spacing 0.04em |
| Body | Source Sans 3 | Arial, sans-serif | Weight 300/400/600 |

Official Quanta typefaces: Alternate Gothic Extra Condensed ATF (headings), Proxima Nova (body). Oswald and Source Sans 3 are web substitutes. Fonts load from Google Fonts — requires internet.

---

## Pattern Overlays

`.slide-dark` and `.slide-accent` include automatic diagonal-hatched overlays (`repeating-linear-gradient` at 45°) matching the Quanta brand pattern system. No extra markup needed.

---

## Badge Variants

Quanta extends the shared badge system with brand-named aliases:

| Class | Maps To | Color |
|---|---|---|
| `.badge-bolt` | `.badge-primary` | Bolt Orange |
| `.badge-infrared` | `.badge-danger` | Infrared Red |

---

## Logo Usage

- **Horizontal format** preferred for most applications
- **Vertical format** when layout demands
- **Icon only** for small spaces (social avatars, favicons)
- Never use wordmark alone — always pair with icon
- Clear space: width of "QU" letters minimum
- Minimum size: 70px digital (dimensional), 50px (flat)

---

## Photography Guidelines

- Authentic, spontaneous — real employees, real work
- No posed shots, no stock photos for external use
- Safety-approved for all field operations
- Represent full workforce diversity
- Prioritize clean energy for sustainability content

---

## Sub-Branding

- **Quanta-operated companies**: Quanta icon + company name in brand typeface
- **Independently operated**: "A QUANTA SERVICES COMPANY" below operating company logo

---

## Section Color Strategy

| Position | Recommended Slide Type |
|---|---|
| Opening | `.slide-dark` (hero with pattern overlay) |
| Body | Alternate `.slide-gray` and `.slide-dark` |
| Dense content | `.slide-light` |
| Chapter breaks | `.slide-accent` (pattern overlay, sparingly) |
| Closing | `.slide-dark` |
