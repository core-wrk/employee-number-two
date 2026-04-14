# Brand Adherence Checklist

Internal reference for `ux-design-reviewer`. Walk through these categories only if `global/context/brand-identity.md` exists. For each category, check the UI against the corresponding section of the brand identity.

If `brand-identity.md` exists but a given category is not specified there (e.g., no iconography guidance), skip that category and note it in the review.

---

## Color

Read from `brand-identity.md`: primary, secondary, accent, neutral, and semantic colors (success, warning, error, info).

Check:
- [ ] Primary actions use the brand primary color
- [ ] Secondary actions use the specified secondary or neutral, not a random shade
- [ ] Semantic states (success, warning, error) use the specified semantic colors
- [ ] No off-brand colors appear in the UI (ad-hoc hex values that don't appear in the brand palette)
- [ ] Color combinations meet the accessibility contrast ratios the brand specifies (or WCAG AA as a fallback)

**Finding format:** "The delete button uses #DC2626 but `brand-identity.md` specifies semantic error color as #B91C1C. Fix: update to #B91C1C or add #DC2626 to the brand palette if intentional."

---

## Typography

Read from `brand-identity.md`: font families, weights, sizes, line heights.

Check:
- [ ] Brand primary font is used for body and UI text
- [ ] Brand display font (if specified) is used for headings per the typography hierarchy
- [ ] Font weights in use match the specified weight scale
- [ ] Heading size hierarchy matches (H1 > H2 > H3 — both visually and semantically)
- [ ] Line height, letter spacing, and line length feel coherent with the specified typography rules
- [ ] No system fonts are sneaking in (e.g., `font-family` fallback that's different from the brand spec)

**Finding format:** "Body text uses Helvetica; `brand-identity.md` specifies Inter. Fix: confirm Inter is loaded and the CSS reset doesn't fall back to Helvetica."

---

## Logo

If the logo appears in the UI:

Check:
- [ ] Correct logo variant for the context (mark-only vs. full wordmark, dark vs. light)
- [ ] Clear space around the logo per brand spec
- [ ] Minimum size respected
- [ ] Not distorted (stretched, squashed, recolored)
- [ ] Placement consistent with where the logo appears elsewhere in the product

**Finding format:** "The navbar logo is displayed at 16px height; `brand-identity.md` specifies a minimum of 24px. Fix: increase to at least 24px or use the mark-only variant."

---

## Spacing and Layout

Read from `brand-identity.md`: spacing scale, grid system, border radius, elevation/shadow rules.

Check:
- [ ] Spacing between elements follows the brand spacing scale (not arbitrary pixel values)
- [ ] Grid alignment is consistent with the brand grid
- [ ] Border radius is consistent (one radius on buttons, a possibly different consistent radius on cards — but not random)
- [ ] Shadows and elevation follow the specified layer system

**Finding format:** "Card corners use 4px border-radius; `brand-identity.md` specifies 8px for card surfaces. Fix: update to 8px."

---

## Imagery and Iconography

If brand identity specifies an icon set or imagery style:

Check:
- [ ] Icons are from the specified set (e.g., Lucide, Heroicons, custom set)
- [ ] Icon weight and style are consistent (no mix of outlined and filled from different sets)
- [ ] Imagery (if any) matches the brand's visual tone — illustration vs. photography, color treatment, subject matter

**Finding format:** "The settings gear icon is from Font Awesome; every other icon on this screen is from Lucide. Fix: replace with Lucide's Settings icon for consistency."

---

## Voice in UI Copy

If `global/context/brand-voice.md` exists, evaluate every piece of visible copy against it. The highest-leverage UI copy surfaces are:

- Button labels
- Error messages
- Empty states
- Form field labels and placeholders
- Helper/instructional text
- Loading state text
- Confirmation dialogs
- Success toast messages

Check:
- [ ] Every piece of copy sounds like the brand would say it — not like the framework default
- [ ] Tone matches the situation (warm on empty states, precise on errors, never condescending)
- [ ] Vocabulary matches the brand's vocabulary (if brand voice avoids jargon, UI avoids jargon)
- [ ] Copy length matches brand (if brand is concise, error messages are concise)

**Finding format:** "Error message reads 'An error occurred. Please try again.' `brand-voice.md` specifies the brand is specific and warm. Fix: rewrite to name what went wrong and what the user should do — e.g., 'We couldn't save your changes. Check your connection and try again.'"

---

## Category Is Not Specified in Brand Identity

If `brand-identity.md` simply doesn't cover a category (e.g., no guidance on iconography), skip the category and note in the review:

> "Iconography: `brand-identity.md` does not specify an icon system; no brand finding possible. If icons become a more prominent part of the product, consider adding an icon system to the brand guide."

This is honest about what the brand guide covers and doesn't pretend to enforce rules that don't exist.

---

## Recording Brand Findings

Every brand finding follows the same shape as heuristic findings: element, violation (with specific brand-identity.md citation), severity, fix.

Severity guide for brand findings:
- **Blocker** — logo misuse, wrong logo, explicitly prohibited color combo, copy that contradicts brand voice values (not just tone)
- **Important** — wrong primary/accent color on load-bearing elements, wrong typography on headings, copy that drifts from voice
- **Nit** — minor spacing inconsistency, one off-palette shade on a low-prominence element
