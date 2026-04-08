# Design Tokens Schema

This is an internal reference for the `brand-identity-synthesizer` skill. It specifies the exact shape of the Design Tokens JSON block that appears in `brand-kit-instructions.md` and `global/context/brand-identity.md`. **Do not show this document to the founder.** Use it to assemble the tokens block deterministically so that downstream consumers (including a future `/canvas-design` skill, Project 04, Project 07, and any other skill or tool that reads brand identity) can parse values without ambiguity.

---

## Why This Schema Exists

The brand kit is platform-agnostic and machine-consumable. Downstream skills will extract values programmatically — they should not have to infer, scrape, or guess. The Design Tokens block is the single source of truth. Every synthesis run must produce a block that:

1. Validates as well-formed JSON
2. Includes every required field
3. Uses consistent field names and types
4. Does not include tool-specific extensions (no Figma-only, Canva-only, or Tailwind-only fields)

If a downstream consumer reads `brand-identity.md`, parses the fenced JSON block under `## Design Tokens`, and gets a schema-valid object, everything downstream works. If you break the schema, downstream breaks silently.

---

## Schema Definition

The top-level object has these keys:

```
{
  "version":    string     (required, currently "1.0")
  "colors":     object     (required)
  "typography": object     (required)
  "spacing":    object     (required)
  "radii":      object     (required)
  "logo":       object     (required)
  "imagery":    object     (required)
}
```

### `version`

A string. Always `"1.0"` for the current schema. Downstream consumers should check this field and fail loudly if they encounter an unknown version.

### `colors`

```
{
  "primary":   { "hex": "#RRGGBB", "name": string, "usage": string }
  "secondary": { "hex": "#RRGGBB", "name": string, "usage": string }   // optional
  "accent":    [ { "hex": "#RRGGBB", "name": string, "usage": string } ]  // array, 0+ items
  "neutrals":  {
    "background":     { "hex": "#RRGGBB" },
    "surface":        { "hex": "#RRGGBB" },
    "text_primary":   { "hex": "#RRGGBB" },
    "text_secondary": { "hex": "#RRGGBB" },
    "border":         { "hex": "#RRGGBB" }
  }
  "semantic": {
    "success": { "hex": "#RRGGBB" },
    "warning": { "hex": "#RRGGBB" },
    "error":   { "hex": "#RRGGBB" },
    "info":    { "hex": "#RRGGBB" }
  }
  "contrast_pairs": [
    { "foreground": string, "background": string, "ratio": number, "wcag": "AA" | "AAA" }
  ]
}
```

**Rules:**
- Every `hex` must be a 7-character uppercase hex string (`#RRGGBB`). Never use 3-char shorthand, never use lowercase, never include alpha.
- `primary` is required. `secondary` is optional (many brands use a single brand color). `accent` is an array that can be empty but must be present.
- All five `neutrals` keys are required.
- All four `semantic` keys are required. Use sensible defaults if the founder has no strong preference (see `color-psychology-guide.md`).
- `contrast_pairs` is required. Include at least the `text_primary` on `background` pair. Reference other keys by their path-free name (e.g., `"text_primary"`, not `"neutrals.text_primary"`) for downstream simplicity.

### `typography`

```
{
  "display": {
    "family":  string,         // e.g., "Inter"
    "weights": [number],       // e.g., [600, 700]
    "source":  string,         // e.g., "Google Fonts"
    "license": string          // e.g., "SIL OFL 1.1"
  }
  "body": {
    "family":  string,
    "weights": [number],
    "source":  string,
    "license": string
  }
  "fallback_stack": [string]   // e.g., ["system-ui", "-apple-system", "sans-serif"]
  "scale": {
    "h1":      { "size_rem": number, "line_height": number, "weight": number },
    "h2":      { "size_rem": number, "line_height": number, "weight": number },
    "h3":      { "size_rem": number, "line_height": number, "weight": number },
    "body":    { "size_rem": number, "line_height": number, "weight": number },
    "small":   { "size_rem": number, "line_height": number, "weight": number },
    "caption": { "size_rem": number, "line_height": number, "weight": number }
  }
}
```

**Rules:**
- `display` and `body` may be the same family (one-face systems). If they are, both objects still must be present and populated.
- `weights` is an array of numeric weight values (e.g., `[400, 600, 700]`). Do not use names like `"regular"` or `"bold"` — always numeric.
- `fallback_stack` is an array of strings ordered from preferred to most-generic fallback. Always end with a generic family (`"sans-serif"`, `"serif"`, or `"monospace"`).
- All six scale roles are required: `h1`, `h2`, `h3`, `body`, `small`, `caption`.
- `size_rem` is in rem (e.g., `1.0` for 16px at default root). `line_height` is unitless (e.g., `1.5`). `weight` is numeric.

### `spacing`

```
{
  "base_rem": number,        // e.g., 0.25 — one spacing unit = 4px at default root
  "scale":    [number]       // e.g., [0, 1, 2, 3, 4, 6, 8, 12, 16] — multipliers
}
```

**Rules:**
- `base_rem` is the size of one spacing unit in rem. Default to `0.25` (4px) if the founder has no opinion.
- `scale` is an array of unitless multipliers. The actual spacing value is `base_rem * multiplier`.
- Default scale: `[0, 1, 2, 3, 4, 6, 8, 12, 16]` (0px, 4px, 8px, 12px, 16px, 24px, 32px, 48px, 64px at default root).

### `radii`

```
{
  "sm":   string,  // e.g., "4px"
  "md":   string,  // e.g., "8px"
  "lg":   string,  // e.g., "16px"
  "full": string   // e.g., "9999px"
}
```

**Rules:**
- All four keys required.
- Values are CSS-length strings (include units).
- `full` represents the "fully rounded / pill" radius. Default `"9999px"`.

### `logo`

```
{
  "mark_type":       "wordmark" | "lettermark" | "symbol_wordmark" | "abstract" | "emblem"
  "primary_concept": string
  "must_have":       [string]
  "must_avoid":      [string]
  "use_contexts":    [string]      // e.g., ["favicon", "header", "social_avatar", "print"]
  "color_variants":  [string]      // e.g., ["full_color", "white_on_dark", "black_on_light", "monochrome"]
  "min_size_px":     number         // minimum legible size in pixels
}
```

**Rules:**
- `mark_type` is one of the exact enum values above. Do not introduce new values.
- `must_have` and `must_avoid` must each have at least 1 entry (can be empty arrays if the founder has no constraints, but prefer to populate them from `logo-concepts.md`).
- `use_contexts` values are free-form strings but should be recognizable tags (`"favicon"`, `"header"`, `"social_avatar"`, `"print"`, `"app_icon"`, etc.).
- `color_variants` values should be drawn from the standard set: `"full_color"`, `"white_on_dark"`, `"black_on_light"`, `"monochrome"`.

### `imagery`

```
{
  "style":           "photo" | "illustration" | "abstract" | "mixed"
  "iconography":     "line" | "filled" | "duotone"
  "treatment_notes": string
}
```

**Rules:**
- `style` and `iconography` are enums — do not invent new values.
- `treatment_notes` is a free-form string describing any photo filters, illustration style, or brand-specific treatment rules.

---

## Example — Complete Valid Block

```json
{
  "version": "1.0",
  "colors": {
    "primary":   { "hex": "#2563EB", "name": "Signal Blue", "usage": "Primary CTAs, brand accents, links" },
    "secondary": { "hex": "#0F172A", "name": "Ink", "usage": "Headings, high-emphasis UI" },
    "accent": [
      { "hex": "#F59E0B", "name": "Flare", "usage": "Callouts, highlights, sparingly" }
    ],
    "neutrals": {
      "background":     { "hex": "#FFFFFF" },
      "surface":        { "hex": "#F8FAFC" },
      "text_primary":   { "hex": "#0F172A" },
      "text_secondary": { "hex": "#475569" },
      "border":         { "hex": "#E2E8F0" }
    },
    "semantic": {
      "success": { "hex": "#16A34A" },
      "warning": { "hex": "#F59E0B" },
      "error":   { "hex": "#DC2626" },
      "info":    { "hex": "#2563EB" }
    },
    "contrast_pairs": [
      { "foreground": "text_primary",   "background": "background", "ratio": 17.47, "wcag": "AAA" },
      { "foreground": "text_secondary", "background": "background", "ratio": 7.47,  "wcag": "AAA" },
      { "foreground": "background",     "background": "primary",    "ratio": 8.59,  "wcag": "AAA" }
    ]
  },
  "typography": {
    "display": { "family": "Inter",  "weights": [600, 700], "source": "Google Fonts", "license": "SIL OFL 1.1" },
    "body":    { "family": "Inter",  "weights": [400, 500], "source": "Google Fonts", "license": "SIL OFL 1.1" },
    "fallback_stack": ["system-ui", "-apple-system", "Segoe UI", "sans-serif"],
    "scale": {
      "h1":      { "size_rem": 3.0,   "line_height": 1.1,  "weight": 700 },
      "h2":      { "size_rem": 2.25,  "line_height": 1.2,  "weight": 700 },
      "h3":      { "size_rem": 1.75,  "line_height": 1.25, "weight": 600 },
      "body":    { "size_rem": 1.0,   "line_height": 1.5,  "weight": 400 },
      "small":   { "size_rem": 0.875, "line_height": 1.4,  "weight": 400 },
      "caption": { "size_rem": 0.75,  "line_height": 1.3,  "weight": 500 }
    }
  },
  "spacing": {
    "base_rem": 0.25,
    "scale": [0, 1, 2, 3, 4, 6, 8, 12, 16]
  },
  "radii": {
    "sm":   "4px",
    "md":   "8px",
    "lg":   "16px",
    "full": "9999px"
  },
  "logo": {
    "mark_type": "symbol_wordmark",
    "primary_concept": "A geometric wordmark paired with a single-glyph mark derived from the first letter, optimized for 16px favicon legibility",
    "must_have": [
      "Legible at 16px",
      "Single-color version for print",
      "Works on both light and dark backgrounds"
    ],
    "must_avoid": [
      "Globe or arrow clichés",
      "Gradient fills in the primary mark"
    ],
    "use_contexts": ["favicon", "header", "social_avatar", "app_icon", "print"],
    "color_variants": ["full_color", "white_on_dark", "black_on_light", "monochrome"],
    "min_size_px": 16
  },
  "imagery": {
    "style": "photo",
    "iconography": "line",
    "treatment_notes": "Photos should feel candid and human, not stock. Icons use 1.5px stroke on a 24px grid."
  }
}
```

---

## Filling Gaps with Defaults

If the three upstream outputs do not provide a value for a required field, fill it in with a sensible default from this guide and **tell the founder explicitly in the conversation** that you are doing so. Common gaps:

- `spacing` and `radii` — rarely specified in `color-palette.md`. Default to the example values above.
- `imagery.treatment_notes` — often missing. Ask the founder one focused question and default to a neutral placeholder if they have no opinion.
- `contrast_pairs` — compute these from the palette rather than expecting them to be pre-stated.
- `logo.min_size_px` — if `logo-concepts.md` does not state it, default to `16` (favicon-legible).

Never silently invent brand colors, typeface names, or logo decisions. Those must come from the upstream outputs.

---

## Validation Checklist

Before emitting the tokens block, walk through this checklist:

- [ ] `version` is `"1.0"`
- [ ] Every hex value is a 7-char uppercase string starting with `#`
- [ ] All six `colors` sub-objects are present (`primary`, `neutrals`, `semantic`, `contrast_pairs`, and either `secondary` or an empty `accent` array — ideally both)
- [ ] `typography.display` and `typography.body` each have `family`, `weights`, `source`, `license`
- [ ] `typography.scale` has all six roles
- [ ] `spacing.base_rem` is numeric, `spacing.scale` is a numeric array
- [ ] All four `radii` keys present with unit strings
- [ ] `logo.mark_type` is one of the five enum values
- [ ] `imagery.style` and `imagery.iconography` are one of their enum values
- [ ] No tool-specific fields (no `figma_*`, `canva_*`, `tailwind_*` keys)
- [ ] The whole block parses as valid JSON

If any item fails, fix before writing.
