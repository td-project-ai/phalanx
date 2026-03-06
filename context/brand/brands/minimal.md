# Minimal — Default Theme Reference

> Brand-agnostic default theme (`minimal.css`). Uses system fonts and a neutral slate/blue palette. Clone this CSS to scaffold a new brand theme.

---

## Color Tokens

| Token | Value |
|---|---|
| `--primary` | `#0F172A` (Slate 900) |
| `--accent` | `#2563EB` (Blue 600) |
| `--accent-light` | `#60A5FA` (Blue 400) |
| `--light-gray` | `#F1F5F9` (Slate 100) |

---

## Typography

System fonts only — no external dependencies, works fully offline:
- Headings: `'Segoe UI', system-ui, sans-serif`
- Body: Same stack

---

## Notes

- No brand-specific components — all shared components from the component library work as-is
- No theme variants
- Use as a starting point for new brand themes: copy `minimal.css`, update custom properties, add brand-specific selectors per [`../_contract.md`](../_contract.md)
