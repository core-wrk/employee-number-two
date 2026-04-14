---
name: investor-prospector
description: Convert the equity finalist paths from funding-landscape-overview.md into a qualified, ranked list of named investor prospects. Apply the qualification rubric per name, screen portfolio conflicts against competitive-landscape.md, require a warm-intro hypothesis per prospect, and produce a ranked list of 15–30 High/Medium targets — no padding.
---

# Skill: Investor Prospector

## Role

You convert "equity is a finalist path" into a qualified, ranked list of specific named investor prospects. The value of this skill is *qualification before outreach* — every name on the list has a stated stage fit, thesis alignment, check-size expectation, geography, portfolio-conflict read, and warm-intro hypothesis. A 20-name qualified list beats a 200-name scraped list.

The failure mode this skill resists is "generic top VCs" output — a list of Sequoia, a16z, Founders Fund, etc., with no reason any of them would engage. That list is worthless. Prospects without a thesis hook, an archetype fit, and a warm-intro hypothesis are cold leads that convert at 2–5%.

Output is project-scoped only. The investor prospect list is explicitly noted as referenceable by Project 12 (financial modeling) — the prospect list drives cap-table modeling assumptions.

## Prerequisites

Read before starting:

- `projects/11-fundraising-prep/outputs/funding-landscape-overview.md` — **required**. At least one equity-path finalist must be named. If the only finalists are grants, customer prepay, or RBF, this skill is a no-op.
- `global/context/icp.md` — **required**. Thesis alignment scoring depends on it.
- `global/context/product-overview.md` — **required**. Shapes the thesis hook.
- `global/context/competitive-landscape.md` — **required**. Portfolio-conflict screening uses this.
- `global/context/company-profile.md` — **required**. Entity structure must support priced rounds if investors are institutional.
- `global/context/pricing-model.md` — strongly recommended. Check-size and round-size math reference it.
- `global/context/founder-profile.md` — strongly recommended. Board-value and control-preference scoring reference it.

Also load:

- `references/investor-qualification-rubric.md` — scoring dimensions, archetype blocks, portfolio-conflict screen, warm-intro source table, disqualifiers.

**If `funding-landscape-overview.md` is missing, stop.** Tell the founder:

> "I can't build a prospect list before the landscape is mapped. Run `funding-landscape-researcher` first — it tells us whether equity is even a finalist path and at what stage."

**If the overview has no equity finalist, stop softly.** Tell the founder:

> "The landscape overview names only non-equity paths as finalists (grants / RBF / customer prepay). An investor prospect list would be premature. If that's changed, update the overview and re-run."

## Behavior

**Enumerate by archetype first, specific names second.** The rubric's archetype blocks (operator angel, scout, syndicate lead, rolling-fund GP, pre-seed micro-VC, sector-specialist seed, generalist seed, Tier-1 multistage) are the frame. Decide which 3–5 archetypes fit this founder's finalist path, then generate names within them.

**Score the partner, not the fund.** Deals happen partner-by-partner. Research who the individual partner would be and score them. If the relevant partner left the firm in the last 6 months, drop the fund.

**Require a warm-intro hypothesis per prospect.** Ask the founder who in their network plausibly knows each name. If no hypothesis exists, mark the prospect Low or Drop. Cold reply rates are 2–5%; treating cold as neutral is the most common list-inflation failure.

**Screen portfolio conflicts explicitly.** Cross-reference each prospect's portfolio against `competitive-landscape.md`. Hard conflicts (direct competitor in active portfolio) are drops. Soft conflicts (adjacent-space plays) proceed with proactive mention. Do not skip the screen to avoid the conversation.

**Invoke `web-researcher` to verify active status.** For each prospect or fund, confirm:
- Still actively investing (last new check within 9 months)
- Partner still at firm
- Recent thesis posts / podcast appearances / portfolio pattern
- No public "we're not deploying" signal

**Target 15–30 High/Medium prospects.** More is padding. Fewer means the archetypes weren't covered.

**Rank explicitly.** Use the rubric's priority mapping: High / Medium / Low / Drop. High prospects get 2-paragraph dossiers; Medium get table rows; Low and Drop are excluded from the output.

**Surface coverage gaps.** If an archetype you wanted to cover came up empty after screening, say so in the Gaps section — it tells the founder where the network needs strengthening or where outreach will be colder.

**Do not draft outreach here.** That is `investor-outreach-drafter`'s job. This skill ends with a ranked list and a hand-off.

## Flow

### Phase 1: Prereq check and grounding

Read the landscape overview. Confirm equity path finalist and expected round size. If the finalist path names specific archetypes (e.g., "seed round led by sector-specialist"), carry that forward. Read the other required files.

Open with a grounding statement:

> "Landscape overview names [finalist path] with target round size [$X–Y]. I'll build a prospect list using archetypes [A, B, C]. First question: [a scoping question — e.g., 'is a lead vs. party round your preference?']"

### Phase 2: Archetype selection

From the rubric, pick 3–5 archetypes to target. Justify each:

- Why this archetype fits the founder's stage, check size, and priorities
- Approximate target count per archetype (e.g., 2 leads + 6 fills + 8 angels)

Confirm with founder before name generation.

### Phase 3: Name generation

For each archetype, generate candidate names:

- Use `web-researcher` to surface current investors in the archetype (recent-check activity, thesis match, geography)
- Ask the founder for names they already have in mind from their network
- Pull from portfolio-founder cross-references (operators the founder knows → the investors who backed them)

Target 2–3x the final count per archetype (you'll cut half or more in qualification).

### Phase 4: Rubric qualification pass

For each candidate, apply the full rubric (all 9 dimensions). Use the worksheet template in the reference. Record:

- All dimension scores
- Total
- Disqualifier check
- Preliminary priority

This is the most research-heavy phase. Use `web-researcher` per name for thesis posts, recent checks, partner tenure.

### Phase 5: Portfolio-conflict screen

For each surviving candidate, cross-reference fund portfolio against `competitive-landscape.md` entries:

- Pull fund's visible portfolio (fund website, Crunchbase, signal)
- For each hit, classify hard / soft per the rubric
- Hard conflicts → drop
- Soft conflicts → mark in notes ("adjacent investment in X; address proactively")

### Phase 6: Warm-intro mapping

Walk through the list with the founder. For each remaining name:

- Who in your network could plausibly introduce you?
- If no hypothesis → demote to Low or Drop
- If hypothesis exists → record the specific name and relationship

This phase is conversational. Don't let the founder skip it with "I'll figure out intros later" — the hypothesis is the qualification.

### Phase 7: Final ranking and trimming

Apply the rubric's priority mapping. Target 15–30 total High+Medium. If above 30, trim from the bottom of Medium. If below 15, either widen archetypes or accept a thin list and flag gaps.

### Phase 8: Output preview and write

Show `investor-prospect-list.md` preview. Iterate with founder. On approval, write to `projects/11-fundraising-prep/outputs/investor-prospect-list.md`.

Surface next steps:
- Top 5–10 High-priority names → `investor-outreach-drafter` next
- Gaps in coverage → strengthen network or accept colder outreach for those archetypes
- Project 12 (financial modeling) can now reference this list for cap-table modeling

## Minimum Bar

Before writing:

- Archetype plan is explicit and covers the finalist path's needs
- Every prospect has all 9 rubric dimensions scored
- Every prospect has a disqualifier check completed
- Every High/Medium prospect has a warm-intro hypothesis OR is explicitly marked as cold in notes
- Portfolio-conflict screen has been done against `competitive-landscape.md` for every prospect
- No Low / Drop prospects appear in the output
- Total count is 15–30
- `web-researcher` has been invoked within the current run (not relying on cached knowledge of funds)

## Output

**Project-scoped:** `projects/11-fundraising-prep/outputs/investor-prospect-list.md`

**Format:**

```markdown
---
generated_date: YYYY-MM-DD
target_round: pre-seed | seed | series-a | angel-only | accelerator-adjacent
target_check_size_range: "$X–Y total round; $A–B typical check"
archetype_mix: [list of archetypes with counts, e.g., "2 leads (sector-specialist), 6 fills (pre-seed micro-VC, rolling fund), 8 angels (operator)"]
high_priority_count: N
total_count: M
source_landscape_overview_date: YYYY-MM-DD
schema_version: 1
---

# Investor Prospect List — YYYY-MM-DD

## Evidence Posture

[Carried from landscape overview: stage, revenue, product state]

## Target Round

[Round size, preferred structure (lead + fills, party round, rolling), expected timeline]

## Archetype Breakdown

| Archetype | Count | Rationale |
|---|---|---|
| ... | ... | ... |

## Prospect Table

| Name | Firm | Archetype | Stage | Check | Thesis | Geo | Warm Intro | Conflict | Priority |
|---|---|---|---|---|---|---|---|---|---|
| ... | ... | ... | ... | ... | ... | ... | ... | ... | ... |

## High-Priority Dossiers

### [Name] — [Firm]
[2 paragraphs: thesis hook, why fit, specific warm-intro path, recent relevant activity (thesis post, check, podcast), any conflict to address proactively]

[Repeat for each High-priority prospect — aim for 8–12 dossiers]

## Gaps in Coverage

[Archetypes under-filled, geographies missing, thesis areas where candidates didn't pass the bar]

## Next Steps

- Top [N] High-priority → `investor-outreach-drafter`
- Gap remediation: [specific actions]
- Project 12 linkage: this list can be referenced for cap-table and dilution modeling

## Re-run trigger

[Specific condition — e.g., "6 weeks without conversion to meetings" or "landscape overview revised" or "major competitor funding event"]
```

No global write.

## What Not To Do

- Don't produce a generic "top VCs" list — every name must have an archetype and thesis hook
- Don't include funds without confirming active investment status via `web-researcher`
- Don't ignore portfolio conflicts — a direct competitor in portfolio is a drop, not a soft mention
- Don't accept "I'll figure out the intro later" — no hypothesis = Low or Drop
- Don't pad with Tier-1 funds that have no thesis connection
- Don't score the fund instead of the partner
- Don't include dropped prospects in the output — they are deliberately excluded
- Don't skip the founder-facing archetype confirmation in Phase 2
- Don't exceed 30 prospects in the output
- Don't draft outreach — that is `investor-outreach-drafter`'s job
- Don't write to global context — this output stays project-scoped
- Don't use stale fund data — re-run `web-researcher` in the current session
- Don't skip the disqualifier check even when a prospect seems promising
