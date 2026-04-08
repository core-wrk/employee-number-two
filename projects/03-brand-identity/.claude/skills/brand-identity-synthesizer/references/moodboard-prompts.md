# Moodboard Prompt Templates

This is an internal reference for the `brand-identity-synthesizer` skill, and a shared resource that the `color-system-builder` and `logo-direction-advisor` skills can link to. It provides tool-agnostic prompt templates for building moodboards in any image tool (Midjourney, DALL-E, Firefly, Stable Diffusion, Pinterest search, or verbal descriptions for human designers). **Do not show this document to the founder verbatim** — use it to generate tailored prompts based on their specific brand voice and visual direction.

---

## Why Moodboards Matter

A moodboard is a shared visual vocabulary. Without one, conversations about brand identity drift into vague adjectives ("clean," "modern," "premium") that everyone interprets differently. A moodboard grounds the conversation in specific, concrete references — even if those references are descriptive rather than visual.

Claude Code cannot render or generate images. Instead, you help the founder:

1. Build a **verbal moodboard** — precise written descriptions that a designer or AI image tool can execute on.
2. Generate **prompt templates** for any image tool the founder wants to use.
3. Create **search queries** for finding references on Pinterest, Dribbble, Behance, or general web search.

The templates below are starting points. Always tailor them to the specific brand voice, palette, and direction that emerged from the conversation.

---

## Core Prompt Structure

A good visual prompt (for any tool) has four components:

1. **Subject** — what you want to see
2. **Style** — how it should be rendered
3. **Mood** — the emotional register
4. **Constraints** — what to avoid, aspect ratio, composition

Example assembled:
> "A minimal product photography scene of a ceramic coffee mug on a warm wood surface [subject], shot with soft window light and shallow depth of field [style], warm and inviting with a quiet, grounded feeling [mood], no text, no branding, neutral composition, 16:9 aspect ratio [constraints]"

Every prompt template below follows this four-part structure.

---

## Templates by Brand Voice

### Serious, trustworthy, established

**Verbal moodboard:**
> "A disciplined visual world with deep blues, warm off-whites, and restrained typography. Imagine the editorial design of a legacy business publication crossed with a modern software brand — confident, unhurried, considered."

**Image prompt template:**
> "[SUBJECT] in a refined editorial style, [muted deep blue / navy / warm neutral] palette, confident composition with generous negative space, feeling established and considered, no noise, no busy textures, [aspect ratio]"

**Search queries:**
- "editorial brand system deep blue"
- "legacy brand modernization"
- "restrained editorial layout"

### Playful, energetic, approachable

**Verbal moodboard:**
> "A bright, confident visual world with rounded shapes, warm accent colors, and type that feels friendly without being childish. Think of a consumer brand that makes daily use feel like a small pleasure."

**Image prompt template:**
> "[SUBJECT] in a bright, friendly style, [warm coral / sunshine yellow / soft teal] palette, rounded shapes, optical bounce and energy, inviting and approachable, no corporate stiffness, [aspect ratio]"

**Search queries:**
- "friendly consumer brand identity"
- "playful rounded wordmark"
- "warm accent color system"

### Technical, precise, modern

**Verbal moodboard:**
> "A disciplined, slightly clinical visual world with graphite neutrals, a single bright accent, and monospace-inflected details. Think developer tool sophistication — quiet, precise, trustworthy in an engineering-first way."

**Image prompt template:**
> "[SUBJECT] in a precise technical style, [graphite / electric accent] palette, monospace details and grid-aligned composition, calm and confident, no decorative flourishes, [aspect ratio]"

**Search queries:**
- "developer tool brand identity"
- "monospace brand system"
- "technical product moodboard"

### Warm, human, grounded

**Verbal moodboard:**
> "An earthy, breathable visual world with terracotta and cream neutrals, hand-adjusted details, and photography that feels candid rather than staged. Think of a brand that sells something made by people, not by a factory."

**Image prompt template:**
> "[SUBJECT] in a warm, human style, [terracotta / cream / olive] palette, natural lighting, candid composition, feeling handmade and grounded, no corporate polish, [aspect ratio]"

**Search queries:**
- "handmade brand identity"
- "warm editorial photography"
- "human-scale brand system"

### Bold, disruptive, confident

**Verbal moodboard:**
> "A high-contrast visual world where type and color do the heavy lifting. Deep black, a single confident brand color, and layouts that are not afraid of empty space. Think of a brand that does not ask permission."

**Image prompt template:**
> "[SUBJECT] in a bold, confident style, [black / single saturated brand color] palette, high contrast, oversized type, unapologetic composition, no decoration, [aspect ratio]"

**Search queries:**
- "bold brand identity high contrast"
- "editorial bold wordmark"
- "confident minimal brand"

### Calm, considered, premium

**Verbal moodboard:**
> "A quiet, deliberate visual world with warm whites, a muted accent (sage, taupe, dusty lavender), and composition that feels like it breathes. Think of a brand that assumes its audience does not need to be shouted at."

**Image prompt template:**
> "[SUBJECT] in a quiet, premium style, [warm white / muted sage / taupe] palette, generous negative space, subtle typographic hierarchy, contemplative mood, no brightness, no noise, [aspect ratio]"

**Search queries:**
- "premium brand identity minimal"
- "considered brand system"
- "quiet luxury moodboard"

---

## Templates by Surface

### Landing page hero

> "A landing page hero for [brand description], using [primary color] and [display face] from the type system, with [single strong visual element — illustration / photo / typographic composition], generous whitespace, confident CTA placement, mood matches [voice attribute], 16:9 aspect ratio, no lorem ipsum, realistic copy placeholders"

### Slide deck title slide

> "A title slide for [brand description], using [primary color] as the dominant color field, [display face] for the title, [body face] for the subtitle, clean horizontal composition, logo in [corner / center], mood matches [voice attribute], 16:9 aspect ratio"

### Social post (square)

> "A 1:1 social post for [brand description], single strong visual idea, brand color present but not dominant, readable at thumbnail size, [voice attribute] mood, optional short text overlay using [display face], no hashtag clutter"

### App icon

> "An app icon for [brand name], [mark type from logo-concepts.md], [primary color] on [neutral surface], legible at 16px, rounded square canvas, no gradient, no drop shadow, works on both light and dark system backgrounds"

---

## Using These Templates

1. **Pull values from the brand's actual outputs.** Replace bracketed tokens with real values from `color-palette.md`, `typography-guide.md`, and `logo-concepts.md`. Never ship a template with `[primary color]` still un-substituted.

2. **Produce 2-3 variants per prompt.** Visual tools are probabilistic — one prompt run produces one outcome. Offer the founder multiple variants of the same prompt (e.g., "warm coffee mug scene" and "cool coffee mug scene") so they can compare.

3. **Strip tool-specific syntax.** Do not include `--ar 16:9`, `weight:1.5`, or any other Midjourney/DALL-E/SD-specific token. Use plain English. If the founder is using a tool that supports that syntax, they can translate.

4. **Name what not to include.** Image tools are better at including than excluding. Always name the things to avoid: "no text," "no watermarks," "no busy backgrounds," "no generic stock photography feel."

5. **For human designers, rewrite as a paragraph.** A designer does not want a prompt — they want a description. Rewrite the prompt into a short paragraph that reads naturally.

---

## When The Founder Is Stuck

If the founder cannot describe the visual direction they want:

1. **Start with exclusions.** "What kind of visual feels completely wrong for this brand?" Easier to generate than "what feels right."
2. **Reference brands, not aesthetics.** "Are there brands whose visual worlds you admire?" Concrete references beat abstract adjectives.
3. **Compare in pairs.** "Stripe or Linear? Notion or Figma? Nike or Allbirds?" Paired comparisons surface preferences faster than open questions.
4. **Describe a scene, not a logo.** "Imagine your customer using your product on a Tuesday morning. What's the room like? What are they wearing? What kind of light?" Scene-based prompts unlock visual intuition that logo-based prompts don't.

---

## Output to the Synthesizer

The moodboard work produced here feeds into:

- `brand-kit-instructions.md` — the "How To Apply This Kit" section can include 1-2 generalized prompt templates for downstream use
- `global/context/brand-identity.md` — the narrative "Style Rules" section can include verbal mood language derived from here
- A future `/canvas-design` skill — will use the `imagery.treatment_notes` field in the Design Tokens block to generate consistent imagery downstream

Do not over-document the moodboard work in the output files. Keep it focused: the tokens and the narrative are the deliverable, not the raw prompts.
