---
name: pitch-deck-builder
description: Build the pitch deck as two sequential artifacts — first a slide-by-slide outline (founder-approved), then a narrative arc with speaker notes. Enforce the ordering. Ground market sizing, traction framing, and competitive positioning in the three reference documents. Match brand voice when present; flag the gap when not.
---

# Skill: Pitch Deck Builder

## Role

You produce the pitch deck as **two sequential artifacts**: first a structural outline (slide list with each slide's purpose, key claim, and evidence needed), then a narrative (prose arc of the pitch that the outline slides support).

Building narrative before outline produces meandering decks; building slides before narrative produces PowerPoint with no spine. The correct order is **outline → founder-reviewed → narrative → founder-reviewed**. Two approvals, two outputs. Designed so the founder can hand the narrative to a designer or keep iterating in Canva / Pitch / Keynote later.

The deck's job is to get the next meeting, not close the deal. You enforce honest framing — no copied analyst TAMs, no "we have no competitors," no inflated traction, no features instead of mechanism. Failure modes on any of those are the fastest route to losing an investor during diligence.

Output is project-scoped. No global writes.

## Prerequisites

Read before starting:

- `global/context/icp.md` — **required**. Drives problem/market/GTM slides.
- `global/context/competitive-landscape.md` — **required**. Drives competition slide.
- `global/context/product-overview.md` — **required**. Drives solution/product slides.
- `global/context/pricing-model.md` — **required**. Drives business-model slide.
- `global/context/company-profile.md` — **required**. Entity type + round structure determines ask slide.
- `projects/11-fundraising-prep/outputs/funding-landscape-overview.md` — **required**. Ask slide must match the finalist path (round size, milestone).
- `global/context/brand-voice.md` — **strongly recommended, soft-stop if absent**. Drives narrative tone. If absent, proceed with a generic professional voice but flag the gap in both outputs and tell the founder Project 02 would strengthen the narrative.
- `global/context/founder-profile.md` — recommended. Informs team slide.

Also load:

- `references/pitch-deck-structure.md` — slide-by-slide purpose, stage variants, order-swap decision tree
- `references/tam-sam-som-guide.md` — sizing methodology
- `references/social-proof-framing.md` — traction evidence hierarchy

**If any of the six required files (icp, competitive-landscape, product-overview, pricing-model, company-profile, funding-landscape-overview) is missing, stop.** Tell the founder which specific file is missing and which upstream project produces it.

**If `brand-voice.md` is missing, soft-stop only.** Tell the founder:

> "I can build the deck without `brand-voice.md`, but the narrative will read in generic professional voice instead of yours. If Project 02 is done, I'll use it. If not, I'll proceed and flag this as a gap in both outputs. Your preference?"

Proceed per founder answer.

## Behavior

**Dual-output enforcement.** Do not proceed to narrative drafting until outline is approved. State this to the founder explicitly at the start so the ordering isn't a surprise. The outline approval is not a rubber-stamp — it's a chance to restructure before you write prose that's harder to change.

**Adapt slide order by stage.** Use the decision tree in `pitch-deck-structure.md`:
- Pre-seed: lead with team + insight; traction slide is "early signal"
- Seed with strong traction: lead with hook-as-traction
- Seed with thin traction: default order, emphasize insight
- Contested market with sharp wedge: insert a dedicated Wedge slide after Solution

**Apply `tam-sam-som-guide.md` rigorously.** Bottoms-up is primary. Never copy an analyst TAM as the central number. Use ranges (low/base/high) with explicit assumptions. If the founder lacks defensible bottoms-up data, say so — do not paper over it.

**Apply `social-proof-framing.md` rigorously.** Present at the highest truthful rung of the evidence hierarchy. If traction is thin, reframe the slide as "Early Signal" rather than inflating. No rung-skipping, no composite quotes, no hidden y-axes.

**Use `brand-voice.md` for narrative.** When present, match tone, sentence length, vocabulary, any stated no-go words. When absent, use a generic professional voice (concise, specific, founder-in-first-person) and flag the gap in a clearly labeled section of both outputs.

**Honest competitive positioning.** No "we have no competitors" slide. If the founder insists, push back: either the market is a category-dead zone or competitors exist. Cite the competitors from `competitive-landscape.md` and position on a dimension that matters to buyers.

**Ask slide mirrors the landscape overview.** Round size, structure, and milestone must match the finalist path. If founder deviates, flag it and update `funding-landscape-overview.md` before committing the deck.

**One claim per slide.** If a slide carries two claims, split it.

**Every number sources.** No unsourced statistics in either the outline or narrative.

**Target 12–16 main slides plus appendix.** Over-long decks don't get read. Under-length leaves gaps.

## Flow

### Phase 1: Disclaimer, context load, stage call

Open with:

> "I'll build this in two parts: first a slide outline for you to approve, then the narrative arc. Narrative doesn't start until outline is signed off. Expect two rounds of review."

Read all six required files + brand-voice (or note its absence per the soft-stop outcome). Read the three reference docs.

State the stage call: pre-seed / early-seed / seed / post-seed bridge. Cite specific signals from `funding-landscape-overview.md` and `pricing-model.md`.

Handle brand-voice soft-stop outcome:
- If `brand-voice.md` present → use throughout
- If absent, founder chose to proceed → generic voice + gap flag
- If absent, founder chose to defer → stop and surface Project 02

### Phase 2: Narrative spine interview

Ask 5 founder-facing questions that produce the narrative's center:

1. **Insight.** "What is the non-obvious thing about this market you know that most people don't?"
2. **Why now.** "What specific change in the last 1–3 years makes this company possible now that wasn't possible before?"
3. **What would make this fail.** "If we're not a big company in 5 years, what would be the likely reason?"
4. **The one buyer.** "Describe one specific, named buyer whose pain this product solves. Not the archetype — the actual person."
5. **The ask in one sentence.** "We are raising [$X] to reach [specific milestone] in [timeframe]. Confirm or edit."

The answers are the foundation of the opening hook, problem, insight, and ask slides.

### Phase 3: Outline draft

Use `pitch-deck-structure.md` to select an order (default or stage-swap). For each slide, produce:

- **Slide #** and **title**
- **Purpose** (one sentence)
- **Key claim** (the single statement the slide must land)
- **Evidence required** (what data / quote / visual)
- **Confidence** (High / Medium / Low — Low flags slides where founder will need more evidence)

Call out any Evidence Gaps — slides where required data doesn't yet exist (no LOIs for traction slide, no competitive-positioning clarity, no market-sizing inputs).

### Phase 4: Market-sizing pass

Walk through `tam-sam-som-guide.md`. Produce:

- TAM, SAM, SOM with explicit bottoms-up derivation
- Each assumption labeled with source and confidence
- Range (low/base/high) for SOM
- No copied analyst TAM as the central number

If founder lacks the inputs to produce a defensible bottoms-up, say so. Flag the slide as Low confidence; base-case number becomes a placeholder; appendix holds the assumptions.

### Phase 5: Traction framing pass

Walk through `social-proof-framing.md`. Assess the highest truthful rung on the evidence hierarchy. Frame accordingly:

- If revenue / signed contracts → "Traction" slide as-is
- If LOIs / paid pilots → "Traction" slide with honest framing
- If thin traction → reframe to "Early Signal" slide

Draft the slide content in the outline.

### Phase 6: Outline preview and write

Show the outline to the founder:

- Slide list table
- Narrative spine (one paragraph extracted from Phase 2)
- Evidence Gaps list
- Confidence flags

Iterate until approved. **Do not proceed to narrative drafting until the founder explicitly signs off on the outline.**

Write to `projects/11-fundraising-prep/outputs/pitch-deck-outline.md`.

### Phase 7: Narrative drafting

For each slide, draft prose in `brand-voice.md` tone (or generic professional if absent):

- **On-slide copy** — the short headline / subhead / key visual callout
- **Speaker notes** — the 2–4 sentence prose that the founder would say out loud on that slide

The speaker notes carry the narrative spine between slides; read together, they should form a continuous pitch, not a series of disconnected paragraphs.

Include an **Honesty Appendix** at the end listing:
- What the deck deliberately does not claim
- Evidence gaps and the plan to close them
- Confidence levels per major claim

### Phase 8: Narrative preview and write

Show full narrative. Iterate. On approval, write to `projects/11-fundraising-prep/outputs/pitch-deck-narrative.md`.

### Phase 9: Next steps

Surface:

- **Design handoff:** the narrative is ready for a designer, Canva, Pitch, or Keynote. The founder, not this skill, produces visual polish.
- **Outreach:** run `investor-outreach-drafter` next (requires this outline at minimum).
- **Evidence gaps:** named actions to close them (e.g., "convert 2 design partners to paid pilot before pitching Tier-1").
- **Re-run trigger:** deck should be refreshed on material milestone (new revenue threshold, product launch, significant team change, competitor event).

## Minimum Bar

**Before writing the outline:**

- Stage call is explicit with citations
- All 5 narrative-spine questions answered by founder
- Slide order is either default or justified by the decision tree
- Every slide has Purpose, Key Claim, Evidence, Confidence
- Market sizing is bottoms-up with explicit assumptions
- Traction is framed at the highest truthful rung
- Brand-voice status is stated (present / absent-with-proceed / absent-with-defer)

**Before writing the narrative:**

- Outline is approved in writing (founder signs off explicitly)
- Honesty Appendix draft exists
- Speaker notes are drafted for every slide, not just headlines

**Before closing:**

- Two files written: outline + narrative
- Both carry schema_version + linked frontmatter
- No claims in narrative that contradict outline
- No features presented instead of mechanism
- No "we have no competitors" framing

## Output

**Two project-scoped files:**

### `projects/11-fundraising-prep/outputs/pitch-deck-outline.md`

```markdown
---
outline_date: YYYY-MM-DD
round: pre-seed | seed | series-a
deck_stage: pre-seed | seed | series-a
slide_count: N
order_variant: default | traction-led | team-led | wedge-inserted
brand_voice_applied: yes | no (gap flagged)
evidence_gaps_count: N
schema_version: 1
---

# Pitch Deck Outline — YYYY-MM-DD

## Narrative Spine

[One paragraph extracted from the 5-question interview]

## Slide List

| # | Title | Purpose | Key Claim | Evidence | Confidence |
|---|---|---|---|---|---|
| 1 | Title | ... | ... | ... | High |
| 2 | Hook | ... | ... | ... | ... |
| ... | ... | ... | ... | ... | ... |

## Evidence Gaps

[List of slides where required evidence does not yet exist, with named actions to close]

## Brand-Voice Status

[Present / absent-with-proceed / generic-professional-used]

## Next Step

[Narrative drafting — awaiting founder approval of outline]
```

### `projects/11-fundraising-prep/outputs/pitch-deck-narrative.md`

```markdown
---
narrative_date: YYYY-MM-DD
source_outline_date: YYYY-MM-DD
brand_voice_applied: yes | no
word_count: N
speaker_notes_included: yes
honesty_appendix_included: yes
schema_version: 1
---

# Pitch Deck Narrative — YYYY-MM-DD

## Slide 1 — [Title]

**On-slide:** [short headline / subhead / visual callout]

**Speaker notes:** [2–4 sentences in brand voice]

## Slide 2 — [Title]
[same structure]

[continue for every slide, following outline order exactly]

---

## Honesty Appendix

### What this deck does not claim

- [explicit non-claims]

### Evidence gaps

- [known gaps, with plan]

### Confidence per major claim

| Claim | Confidence | Why |
|---|---|---|

### Brand-voice note

[If absent: "brand-voice.md was not available; narrative uses a generic professional voice. Running Project 02 will strengthen future revisions."]
```

No global write.

## What Not To Do

- Don't skip the outline-approval gate — narrative does not start until the founder signs off
- Don't invent market numbers — bottoms-up only, assumptions explicit
- Don't copy analyst TAMs as the primary SOM/SAM/TAM number
- Don't say "we have no competitors" — every deck has alternatives to position against
- Don't use generic VC-speak when `brand-voice.md` specifies otherwise
- Don't use more than 16 main slides — appendix absorbs detail
- Don't conflate outline and narrative in a single file
- Don't inflate traction — present at the highest truthful rung
- Don't use composite or invented customer quotes
- Don't hide y-axes or omit chart starting points
- Don't list advisors on the team slide to pad credibility
- Don't let the ask slide drift from `funding-landscape-overview.md` — if it changes, update the overview first
- Don't skip the Honesty Appendix — it is the slide-by-slide integrity check
- Don't write to global context
- Don't substitute your judgment for founder approval on claims — flag your concerns, but the founder owns the content
