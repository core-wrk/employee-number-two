# Color Psychology Guide

This is an internal reference for the `color-system-builder` skill. It contains voice-to-color translation tables, industry conventions, question banks, and WCAG accessibility shortcuts. **Do not show this document to the founder.** Use it to guide the conversation naturally and to calibrate your recommendations.

---

## How To Use This Guide

1. Listen to the founder describe their brand voice and audience.
2. Use the **Voice-to-Color Translation Table** below to identify 2-3 plausible color families.
3. Use the **Industry Conventions** section to decide whether to conform or contrast with norms.
4. Use the **Question Bank** to probe when answers are vague.
5. Use the **WCAG AA Shortcuts** to verify any text-on-background pair before proposing it.

Never recite this guide verbatim. Weave its insights into the conversation naturally.

---

## Voice-to-Color Translation Table

| Brand voice attribute | Primary family suggestions | Avoid |
|---|---|---|
| Serious, trustworthy, established | Deep blue, navy, charcoal, forest green | Saturated oranges, hot pinks |
| Playful, energetic, approachable | Coral, sunshine yellow, teal, bright purple | Dull earth tones, grayscale-only |
| Warm, human, grounded | Terracotta, cream, olive, warm brown | Cool blues, neon greens |
| Cool, analytical, precise | Cobalt, slate, ice blue, graphite | Warm oranges, peach |
| Bold, disruptive, confident | Crimson, electric blue, jet black | Pastels, washed-out tones |
| Calm, considered, premium | Sage, muted lavender, warm white, taupe | High-saturation primaries |
| Optimistic, fresh, youthful | Mint, sky, citrus, soft coral | Black-dominant palettes |
| Technical, precise, modern | Electric blue, graphite, acid green accent | Earth tones, pastels |

**How to use this table:** If `brand-voice.md` describes the brand as "confident, direct, and not afraid to disagree," you are looking at the *bold, disruptive, confident* row. Propose 2-3 options from that family and ask the founder which resonates, without showing them the table.

---

## Industry Conventions

When to conform, when to contrast:

- **Fintech / banking** — Convention is deep blue + white + green for growth. Contrasting works if the brand voice is disruptive. Default to conforming if the brand is targeting enterprise buyers.
- **Healthcare** — Convention is teal + white + soft blue (calm, clean). Contrasting risks signaling unserious. Default to conforming.
- **Consumer / DTC** — No strong convention. Differentiation matters more than conformity.
- **Developer tools** — Convention is dark mode first, monochrome-friendly, accent colors used sparingly. Contrasting with a bright, friendly palette can work for developer experience brands.
- **B2B SaaS** — Convention is a single bold primary + neutral supporting palette. Expressive palettes risk looking consumer-grade.
- **Children / education** — Convention is bright, high-saturation, multi-color. Muted palettes risk feeling clinical.
- **Luxury / premium** — Convention is restrained palette: black, white, gold or deep jewel accent. Bright colors signal mass-market.
- **Sustainability / climate** — Convention is green dominant, earth tones. Contrasting with unexpected colors (coral, cobalt) can signal "not another greenwash brand."

---

## Question Bank

### Emotional register

**Primary:** "When someone sees your brand for the first time — on a website, in an email, on a business card — what are the first three words you want them to think?"

**Follow-ups:**
- If they say "professional": "Professional can mean a lot of things. Serious like a law firm? Polished like a consulting firm? Precise like a lab? Which is closest?"
- If they say "friendly": "Friendly in what way — warm and human, or bright and energetic?"
- If they say "modern": "Modern is a moving target. Do you mean clean and minimal, or bold and tech-forward?"
- If they struggle: "Let's try the opposite — what words do you definitely *not* want people to think?"

### Industry context

**Primary:** "If I looked at your five closest competitors side by side, what colors would I see?"

**Follow-ups:**
- If they describe a dominant convention: "Does fitting into that group feel right, or do you want to stand apart?"
- If they claim no conventions exist: "Even loose ones count — what do most fintechs/wellness brands/dev tools tend to reach for?"
- If they name a competitor they admire: "What specifically about that color works — is it the hue itself, or how they use it?"

### Primary color direction

**Primary:** "If you had to pick a single color that represents the brand, what would you reach for?"

**Follow-ups:**
- If they give a broad family ("blue"): "What kind of blue — navy, cobalt, sky, teal? Each one says something different."
- If they give a specific hex: "What draws you to that exact shade? Have you seen it used somewhere that resonated?"
- If they are stuck: "Let me offer three directions based on what you've told me so far — [propose 3 from the translation table]. Does any of them feel closest?"

### Secondary and accent

**Primary:** "Your primary is the anchor. What do you want to sit alongside it — something that complements, something that contrasts, or something that lives quietly in the background?"

**Follow-ups:**
- If they want contrast: "High-contrast accents pull the eye. Where do you want that attention — CTAs, highlights, alerts?"
- If they want harmony: "A harmonious accent means the palette feels unified but can get visually flat. How will we create hierarchy?"

### Neutrals

**Primary:** "How does the brand feel about color density? Should it live on a bright white surface, a soft off-white, or something darker?"

**Follow-ups:**
- If they choose white: "Pure white or a warm/cool off-white? Warm off-whites feel more human; cool off-whites feel more technical."
- If they choose dark: "Is that for a dark-mode-only product, or the primary brand surface?"

### Accessibility

Always verify. You do not ask the founder about this — you check it yourself using the shortcuts below and tell them the result. If a pair fails, adjust and re-propose.

---

## WCAG AA Shortcuts

**Requirements:**
- Normal text (< 18pt or < 14pt bold): contrast ratio ≥ **4.5:1**
- Large text (≥ 18pt or ≥ 14pt bold): contrast ratio ≥ **3:1**
- UI components and graphics: contrast ratio ≥ **3:1**

**Common safe pairs (AA or better):**
- `#111111` on `#FFFFFF` → 18.88:1 (AAA)
- `#333333` on `#FFFFFF` → 12.63:1 (AAA)
- `#555555` on `#FFFFFF` → 7.46:1 (AAA)
- `#757575` on `#FFFFFF` → 4.54:1 (AA, borderline)
- `#FFFFFF` on `#1A1A1A` → 17.40:1 (AAA)
- `#FFFFFF` on `#0F172A` (slate-900) → 17.47:1 (AAA)

**Common failing pairs to avoid:**
- `#888888` on `#FFFFFF` → 3.54:1 (fails AA for normal text)
- Pure yellow `#FFFF00` on `#FFFFFF` → 1.07:1 (fails everything)
- Mid-gray on mid-gray — any combination where both values are in the 400-600 range

**Calculation shortcut:** If you need to verify a pair you are uncertain about, state the hexes explicitly in your reasoning, estimate conservatively, and tell the founder the ratio you believe it has. If you are below 4.5:1, adjust. If you are unsure, err on the side of darker foreground or lighter background.

---

## Semantic Color Defaults

If the founder has no strong opinion on semantic colors, these are sensible starting points that work in most palettes:

- **Success:** green in the 500-600 range (`#22C55E`, `#16A34A`)
- **Warning:** amber/orange in the 500-600 range (`#F59E0B`, `#F97316`)
- **Error:** red in the 500-600 range (`#EF4444`, `#DC2626`)
- **Info:** blue in the 500-600 range (`#3B82F6`, `#2563EB`)

Adjust the saturation to match the overall palette character. A muted palette gets muted semantic colors; a bold palette gets saturated ones.

---

## When To Push Back

Push back gently when the founder:

- **Picks a color because they personally like it** without connecting it to the brand — "That's a great color. Help me understand how it connects to [voice attribute they named earlier]."
- **Wants to use their favorite competitor's exact colors** — "That palette is doing a job for them. What job do we want yours to do differently?"
- **Gives vague answers like "something modern and clean"** — "Modern and clean covers a huge range. Would you say more Apple or more Stripe? More Linear or more Notion?"
- **Dismisses accessibility** — Do not let this slide. Explain once, briefly, that any palette that fails AA will block customers from reading the content, and then proceed with accessible alternatives.
