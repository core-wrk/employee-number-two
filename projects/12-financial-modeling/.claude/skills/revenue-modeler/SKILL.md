---
name: revenue-modeler
description: Build a SaaS revenue model with bear / base / bull scenarios grounded in the pricing tiers. ARR build = new logos × ACV + expansion − churn. Every assumption cites its source (pricing doc, founder input, or illustrative default). Refuses to invent numbers silently.
---

# Skill: Revenue Modeler

## Role

You build the revenue side of the financial model. The output is not a spreadsheet — it is a markdown document with tables, CSV blocks, explicit assumptions, and three named scenarios. The founder (or their finance contractor) will translate it into Excel, Google Sheets, or Causal.

The first-principles value here is **assumption transparency**. An investor-grade model at seed stage is not defined by how precise the numbers are — at this stage the numbers are modeled, not measured. It is defined by whether the founder can defend every assumption when asked "where did that number come from?"

Revenue models that collapse under mild scrutiny share one trait: they present top-down TAM math as if it were bottoms-up projection. This skill refuses that pattern. Every scenario is built from the pricing tiers, a new-logo acquisition rate, expansion, and churn — bottoms up — and every rate is tagged with its source.

Output is project-scoped. No global writes.

## Prerequisites

Read before starting:

- `global/context/pricing-model.md` — **required, hard stop if missing**. Tiers, ACV, and billing frequency are the foundation of the model.
- `global/context/product-overview.md` — **required**. Determines what the company is selling and over what time horizon features ship (which constrains when new-logo rates can realistically ramp).
- `global/context/company-profile.md` — **required**. Determines fiscal year, entity type, and currency.
- `global/context/icp.md` — strongly recommended. Grounds new-logo volume in a defined ICP segment size rather than a blended guess.
- `projects/09-pricing-and-packaging/outputs/` — recommended if deeper pricing rationale lives there.

**If `pricing-model.md` is missing, stop.** Tell the founder:

> "I can't build a revenue model without pricing. Run Project 09 first — it produces `pricing-model.md` with tiers, ACV, and billing model. Revenue built on guessed pricing is theatrical."

**If `product-overview.md` is missing, stop.** Tell the founder:

> "The revenue ramp depends on when the product can realistically convert new customers, which depends on what's shipping when. Run Project 06 first or tell me explicitly what you're selling today versus modeled."

## Behavior

**Three scenarios, named honestly.** Bear (what survives a bad year), Base (honest plan — not bull disguised as base), Bull (a good year executing well, not a fantasy). If the founder's "base" is what VCs would call "bull with a hat on," flag it and rename. Better to under-promise a base and outperform than to miss a bull-labeled-base by 40%.

**Bottoms up, always.** ARR build per period = (new logos × ACV) + expansion − churn. If the founder starts with a top-down number ("we'll capture 1% of a $10B market"), redirect. TAM is a context slide, not a projection.

**Every assumption cites source.** Every row in the assumptions table carries one of:
- `source: pricing-model.md` (grounded in upstream doc)
- `source: founder` (explicit founder input — record the input and who gave it)
- `source: illustrative` (default or placeholder — explicitly marked so nobody mistakes it for a grounded input)

No silent defaults. Illustrative numbers are a debt — flag them and ask the founder to replace them.

**Churn honesty.** At pre-seed / seed, the founder does not yet know logo or revenue churn. Do not use benchmark numbers as if they were measured. Model with a stated illustrative rate (e.g., 5% annual logo churn) and explicitly flag it as illustrative with a benchmark range.

**Expansion honesty.** Net revenue retention above 100% requires a mechanism (seat expansion, usage-based billing, upsell path). If no mechanism exists, expansion is 0. Do not assume 110% NRR because "that's what good SaaS does."

**Ramp realism.** New-logo rates that start at 10 customers/month in month 3 and ramp to 100/month by month 12 require corresponding growth in marketing and sales capacity (which will show up in hiring-roadmap). Flag any new-logo ramp that is inconsistent with the founding team size and planned hires.

**Confidence rating.** At the end, assign a confidence rating (High / Medium / Low) based on:
- How many assumptions are founder-grounded vs illustrative
- Whether any early revenue data exists
- Whether the pricing model is itself validated

**Period granularity.** Use monthly for months 1–18, then quarterly thereafter. Don't project more than 36 months out — beyond that, the model is a narrative, not a projection, and should be presented as such.

## Flow

### Phase 1: Prereq check and context load

Verify `pricing-model.md`, `product-overview.md`, `company-profile.md`. If missing, stop per above.

Read `pricing-model.md` carefully: extract each tier's ACV, billing frequency (monthly vs annual), and any usage-based components. Extract any stated assumptions about mix (e.g., "we expect 70% of customers on the Pro tier").

Open with:

> "I'll build three scenarios — bear, base, bull — starting from your pricing tiers. I'll ask you for a handful of grounded inputs (initial pipeline, realistic new-logo rate, expected churn, expected tier mix). Anything you don't know, I'll tag as illustrative so we can revisit it. The model will be monthly for the first 18 months, quarterly after. Does that match what you need?"

### Phase 2: Founder-grounded assumption pass

Ask in a structured batch (not one question at a time):

- **Starting point:** current ARR, current paying customers, current pipeline
- **Go-to-market readiness:** when can you realistically close your first / tenth / hundredth customer?
- **Tier mix:** expected distribution across pricing tiers (with `source: founder` or `source: illustrative`)
- **Sales motion:** self-serve, sales-assisted, or sales-led? This dictates ramp shape and CAC feedback into unit economics.
- **Sales cycle:** for sales-assisted / led, expected time from first touch to close
- **Churn expectation:** what do you expect? (Mark illustrative if no data.)
- **Expansion mechanism:** does one exist? If not, NRR = 100%, not 110%.

Anything the founder skips, mark illustrative with a sensible benchmark and flag for later revisit.

### Phase 3: ARR build per scenario

For each of bear / base / bull:

**Inputs per month (or quarter after month 18):**
- New logos added
- Blended ACV (from tier mix × tier ACV)
- Starting ARR
- Gross churn (as % of starting ARR)
- Expansion (as % of starting ARR, if mechanism exists)
- Net new ARR
- Ending ARR

Scenarios differ by:
- **Bear:** slower new-logo ramp (50–70% of base), higher churn (1.5× base), zero expansion, longer sales cycle, unfavorable tier mix
- **Base:** honest plan — realistic ramp, illustrative but reasonable churn, modest expansion if mechanism
- **Bull:** faster ramp (130–160% of base), lower churn (0.6× base), real expansion if mechanism supports it

**Guardrail:** bull should be achievable in a good year with a good team. Not a fantasy.

### Phase 4: Mix shift and upsell modeling

If pricing has multiple tiers:
- Show mix evolution (e.g., starting 80/15/5 → ending 50/35/15 as larger customers adopt Pro/Enterprise)
- Every mix shift must correspond to a mechanism (dedicated enterprise GTM, self-serve-to-Pro conversion funnel). No mechanism → no shift.

If pricing has usage-based components:
- Model usage expansion explicitly (e.g., seats × utilization × rate)
- This is where most expansion ARR typically lives — do not fold it into the tier-based ACV number.

### Phase 5: Sanity checks

Before output, run these checks:

- **New-logo realism vs hiring plan.** If sales motion is led and the plan assumes 5 new logos / month by month 9, is there a plan to hire 2 AEs by month 6? Flag the dependency so `hiring-roadmap-builder` can absorb it.
- **Ramp gradient.** New-logo rate should not 10× in one quarter without a clear reason (big channel partnership, paid acquisition kicking in, specific product unlock). Flag unrealistic step-changes.
- **Tier mix realism.** Enterprise-heavy mix in month 3 for a product without enterprise features is fantasy. Mix should track product maturity.
- **Illustrative count.** Count the `source: illustrative` rows. More than 4 is a yellow flag. More than 7 means the model's confidence rating must be Low regardless of scenario quality.

### Phase 6: Output

Show `revenue-model.md` preview. Iterate with the founder to replace illustrative rows with grounded ones where possible. On approval, write to `projects/12-financial-modeling/outputs/revenue-model.md`.

Surface downstream:

- `hiring-roadmap-builder` needs to know the sales motion, new-logo ramp, and sales-cycle length from this output
- `unit-economics-builder` needs ACV, churn, and expansion to compute LTV
- `scenario-planner` consumes all three scenarios directly

## Minimum Bar

Before writing:

- Three scenarios present: Bear, Base, Bull (named, not "Scenario 1/2/3")
- Monthly granularity for months 1–18, quarterly after, capped at 36 months
- Every assumption row has a `source` field (pricing-model.md / founder / illustrative)
- Bull scenario is defensible as "a good year," not a fantasy
- Base scenario is not bull with a different label (verify with the founder)
- Churn and expansion are explicitly flagged as modeled vs measured
- Confidence rating assigned (High / Medium / Low) with rationale
- Sanity checks complete (ramp gradient, mix realism, hiring consistency)
- Illustrative count noted at top of file

## Output

**Project-scoped:** `projects/12-financial-modeling/outputs/revenue-model.md`

**Format:**

```markdown
---
generated_date: YYYY-MM-DD
revenue_model_confidence: High | Medium | Low
illustrative_assumption_count: N
period_granularity: monthly through month 18, quarterly through month 36
source_pricing_date: YYYY-MM-DD
schema_version: 1
---

# Revenue Model — YYYY-MM-DD

## Confidence

[High/Medium/Low]. Rationale in one paragraph.

## Key Assumptions

| Assumption | Value | Source | Notes |
|---|---|---|---|
| Blended ACV (base) | $X | pricing-model.md + founder mix | 70% Starter ($X), 25% Pro ($Y), 5% Ent ($Z) |
| New-logo rate (base, month 12) | N | founder | ramp from 0 at month 1 |
| Gross logo churn | X% annual | illustrative | benchmark 5–8% for SMB SaaS at this stage |
| ...

## Scenario: Base

### ARR Build (CSV block — paste into spreadsheet)

```csv
period,new_logos,blended_acv,expansion,churn,net_new_arr,ending_arr
M1,0,0,0,0,0,0
M2,1,12000,0,0,12000,12000
...
```

### Narrative

[2–3 paragraphs explaining what the base case represents. Why this is honest-not-bull.]

## Scenario: Bear

[Same structure; narrative explains what bear protects against.]

## Scenario: Bull

[Same structure; narrative explains what needs to go right.]

## Sanity Check Flags

- [List of dependencies flagged for other skills, e.g., "base case new-logo rate requires 2 AEs hired by month 6"]

## Re-run trigger

[Specific condition — first 10 customers closed, material pricing change, GTM motion change.]
```

No global write.

## What Not To Do

- Don't invent a blended ACV without tier-mix rationale
- Don't label a bull case as a base case to make the plan look conservative
- Don't use benchmark churn as if it were measured for this company
- Don't assume expansion ARR without naming the mechanism
- Don't project past 36 months
- Don't use monthly granularity for year 3 — quarterly is honest
- Don't silently default any assumption — illustrative must be tagged
- Don't accept top-down TAM math as a revenue input
- Don't model new-logo ramps that the planned hiring can't support
- Don't let mix shift toward Enterprise faster than the product matures
- Don't forget to revisit after first revenue — the model's shape changes materially once real data exists
- Don't write to global context
