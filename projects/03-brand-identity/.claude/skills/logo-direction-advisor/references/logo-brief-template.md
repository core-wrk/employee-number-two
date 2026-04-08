# Logo Brief Template & Question Bank

This is an internal reference for the `logo-direction-advisor` skill. It contains a question bank organized by topic and a structural template for the final brief. **Do not show this document to the founder.** Use it to guide the conversation naturally.

---

## How To Use This Guide

1. Let the founder lead with whatever they bring to the conversation.
2. Use the **Question Bank** to probe, reframe, and push toward specifics.
3. Use the **Mark Type Decision Tree** when the founder is uncertain about direction.
4. Use the **Verbal Description Vocabulary** when you need to describe visuals precisely.
5. When synthesizing, follow the **Brief Template Structure** exactly — downstream consumers (including a future `/canvas-design` skill and the `brand-identity-synthesizer`) expect these sections.

---

## Question Bank

### Logo purpose and use contexts

**Primary:** "Before we talk about what the logo looks like, let's talk about where it lives. What are the three most important places this logo will show up?"

**Follow-ups:**
- If they name a website: "Is the logo sitting in a header on a light background, a hero with imagery behind it, or both?"
- If they name social: "Which platforms? A circular profile crop has very different constraints than an open canvas."
- If they name a product: "Is there a favicon or app icon? That's often the most constrained version and worth designing for first."
- If they struggle: "Let me offer a default set — header on a website, favicon at 16px, profile avatar on LinkedIn or X, title slide of a deck. Does that cover your needs?"

### Mark type

**Primary:** "There are roughly five kinds of logos — a wordmark (just the name, styled), a lettermark (initials or a single letter), a combination mark (symbol + name), an abstract mark (symbol alone), or an emblem (symbol and name locked together in a shape). Do you have instincts about which kind feels right?"

**Follow-ups:**
- If they want a symbol alone: "Symbols are powerful but require recognition. For an early-stage brand, they can feel anonymous. Would a combination mark — symbol with the name alongside — give you more flexibility early and let you lean on the symbol later?"
- If they want a wordmark: "Wordmarks rely entirely on typography and letterform details. How do you feel about the length of the name? Short names become punchier wordmarks; longer names need more rhythm."
- If they are unsure: use the **Mark Type Decision Tree** below.

### Competitive scan

**Primary:** "If I looked at the five closest competitors, what would their logos have in common?"

**Follow-ups:**
- If they describe a pattern (e.g., "everyone uses a lowercase sans-serif wordmark"): "That's the convention. Do you want to be legible as one of them, or distinctive from them?"
- If they claim no pattern exists: "Even loose patterns count. Do they lean serif or sans? Wordmark or symbol? Geometric or organic? Colorful or monochrome?"
- Use the `competitor-visual-scan.md` reference for a more structured version of this conversation.

### Symbolic vocabulary

**Primary:** "When you think about what the brand stands for, what objects, shapes, or metaphors come to mind? Even if they feel too literal to actually use — I want to know what's in your head."

**Follow-ups:**
- If they offer a concrete object: "Interesting. What about that object represents the brand — its function, its shape, a cultural association?"
- If they offer an abstraction: "Help me picture it. If I had to describe it to someone without using the word, how would I?"
- If nothing comes to mind: "Let me try the opposite — what symbols feel *wrong* for this brand? Sometimes it's easier to start there."

### Tone attributes → form

**Primary:** "One of the brand voice attributes is [X]. In visual form, that could mean a lot of things — geometric or organic shapes, heavy or light weights, hard or soft edges. Do any of those feel like a natural fit?"

**Follow-ups:** Use the **Verbal Description Vocabulary** section to offer specific translations.

### Must-haves and must-avoids

**Primary:** "Are there any visual ideas you *definitely* want included — a specific shape, a reference to the name, a nod to your industry? And equally important: anything you want to rule out entirely?"

**Follow-ups:**
- "What about common clichés in your space — are there visual tropes you're sick of seeing?"
- If they name specific items: "Is there a reason you want to avoid that, so the designer understands — aesthetic, cultural, competitive?"

### Deliverables

**Primary:** "Last question area. What files will you need to actually use this logo — SVG, PNG, variants for dark and light backgrounds, monochrome, favicon?"

**Follow-ups:**
- If they don't know: "Default set is: SVG primary, SVG on dark, SVG monochrome, PNG at 1x/2x/3x, and a 32x32 favicon. Good starting point?"

---

## Mark Type Decision Tree

Use when the founder is genuinely uncertain.

```
Is the brand name 1-2 short words AND memorable without a symbol?
├── Yes → Lean wordmark or lettermark
│   └── Are the letterforms themselves distinctive/could be customized?
│       ├── Yes → Pure wordmark
│       └── No → Lettermark (initials or monogram)
└── No or unsure → Lean combination mark
    ├── Is there a strong symbolic idea the brand wants to own long-term?
    │   ├── Yes → Combination mark with intent to evolve into abstract mark
    │   └── No → Combination mark (safer, more flexible early)
    └── Is the brand industry-traditional or has strong heritage association?
        ├── Yes → Consider emblem (locked shape)
        └── No → Skip emblem — they feel dated for most new brands
```

Present this as a conversation, not a decision tree. "Here's how I think about it — is your name the kind of word that's memorable on its own?"

---

## Verbal Description Vocabulary

When translating tone attributes to visual form, use precise language. Examples:

### Geometric vs. organic
- **Geometric:** "built from circles and straight lines," "mathematical precision," "grid-aligned"
- **Organic:** "hand-drawn feel," "irregular curves," "breathable negative space"

### Weight and density
- **Heavy:** "confident stance," "solid presence," "bold strokes that fill the space"
- **Light:** "airy," "restrained," "elegant thin strokes that rely on negative space"

### Edges
- **Hard:** "sharp terminals," "angular corners," "uncompromising silhouette"
- **Soft:** "rounded terminals," "friendly corners," "inviting curves"

### Complexity
- **Minimal:** "reduced to essentials," "single shape or gesture," "memorable at any size"
- **Detailed:** "rewarding closer inspection," "layered meaning," "craft and patience"

### Character (for wordmarks specifically)
- **Classic:** "transitional serif proportions," "traditional letterform structure"
- **Modern:** "neo-grotesque clarity," "industrial honesty"
- **Playful:** "rounded counters," "optical bounce," "hand-adjusted spacing"
- **Technical:** "mono-inspired uniformity," "grid-locked proportions"

---

## Brief Template Structure

When writing `outputs/logo-concepts.md`, use exactly these sections in this order:

1. Summary
2. Mark Type (with rationale)
3. Concept (one paragraph of evocative specifics)
4. Visual References (described in words, 3+)
5. Competitive Differentiation
6. Must-Haves
7. Must-Avoids
8. Tone Attributes → Form (table)
9. Color Applications (tie to color-palette.md if present)
10. Typography Tie-In (tie to typography-guide.md if present)
11. Technical Requirements
12. Deliverables Requested
13. Prompts for AI Image Tools (optional)

The `brand-identity-synthesizer` will read this file and expects these sections. If you deviate, the synthesis step has to guess, which creates ambiguity.

---

## When To Push Back

Push back gently when the founder:

- **Says "I'll know it when I see it"** — "That's honest, but we can't hand a designer 'you'll know it.' Let me push on what you *don't* want first — sometimes it's faster."
- **Wants to combine too many symbols** — "Each symbol you add dilutes the others. If we had to pick one, which would you keep?"
- **Copies a competitor too closely** — "That logo works for them because of what they already are. What would make yours work because of what *you* already are?"
- **Resists specificity** — "Vague briefs produce vague logos. The more concrete you are now, the less negotiation we need later."
- **Wants "timeless"** — "Timeless is code for 'don't look dated in 5 years.' That usually means reducing trend signals. What specific trends do you want to avoid?"
