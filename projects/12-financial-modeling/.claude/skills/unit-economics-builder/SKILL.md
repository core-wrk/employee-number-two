---
name: unit-economics-builder
description: Compute CAC, LTV, LTV/CAC ratio, gross margin, and payback period. At pre-seed / seed these are sketches, not measurements — frame honestly and flag every modeled vs measured input. Refuses to present illustrative numbers as validated metrics.
---

# Skill: Unit Economics Builder

## Role

You produce the unit economics view — CAC, LTV, LTV/CAC, gross margin, payback. These are the numbers investors will ask about, and they are also the numbers most often fabricated in early-stage decks.

The first-principles stance here is uncomfortable but important: **at pre-seed and most of seed, the company does not have enough cohort history or enough customers to compute real unit economics.** LTV/CAC of 4.2 based on 12 customers and 6 months of history is a cosplay of a metric, not a metric. This skill refuses to dress up a sketch as a measurement.

The output is still valuable — it forces the founder to have a *theory* of unit economics even if they can't measure them yet. That theory is what will be tested once real data exists. The output is explicit about which numbers are measured, which are modeled, and what would need to be true for the modeled numbers to land.

Output is project-scoped. No global writes.

## Prerequisites

Read before starting:

- `projects/12-financial-modeling/outputs/revenue-model.md` — **required**. ACV, churn, and expansion drive LTV.
- `projects/12-financial-modeling/outputs/cost-structure.md` — **required**. GTM spend drives CAC; COGS drives gross margin.
- `projects/12-financial-modeling/outputs/hiring-roadmap.md` — **required**. GTM headcount is the dominant CAC input.
- `global/context/pricing-model.md` — **required**. Billing frequency and discounting affect the economics.
- `global/context/product-overview.md` — recommended. Infrastructure-per-customer cost context.

**If any of the three upstream outputs are missing, stop.** Tell the founder:

> "Unit economics synthesize revenue, cost structure, and hiring. At minimum I need revenue-model.md and cost-structure.md. Run `revenue-modeler` and `hiring-roadmap-builder` first."

## Behavior

**Separate modeled from measured — everywhere.** Every metric in the output is tagged `measured` (cohort data exists) or `modeled` (computed from assumptions). If the company has <20 paying customers and <12 months of history, *all* metrics are modeled. Say so plainly at the top.

**CAC formula discipline.** Fully-loaded CAC includes:
- Sales headcount cost (AEs, SDRs, sales engineers, sales ops — fully loaded)
- Marketing headcount cost
- Paid acquisition spend
- Sales/marketing tools
- Founder time allocated to sales (if relevant — discount honestly)

CAC = (total S&M spend over period) / (new customers acquired in period).

**Blended vs paid CAC.** Report both if acquisition is mixed:
- Blended CAC = total S&M / all new customers
- Paid CAC = paid acquisition spend / customers attributed to paid

Investors care about paid CAC because it's the lever that must scale. Organic customers are real but not a scalable channel.

**LTV formula discipline.** For subscription:

```
LTV = ACV × gross margin % × (1 / churn rate)
```

Use `ACV × gross margin` for *contribution* LTV (the version that matters for LTV/CAC comparisons). Never use revenue LTV ignoring COGS.

For the `1 / churn rate` term:
- Use **monthly gross revenue churn** if you have it
- If modeled, state the churn rate and cite revenue-model.md
- Cap LTV horizon at a reasonable bound (e.g., 5–7 years) — infinite geometric series assumes infinite retention, which nobody delivers.

**Gross margin discipline.** Gross margin = (Revenue − COGS) / Revenue.

COGS for SaaS typically includes:
- Infrastructure (cloud, databases, monitoring)
- Third-party APIs that scale per-customer (LLM calls, SMS, payments rails)
- Customer support personnel (fully loaded, allocated portion)
- Hosting/CDN

Excluded from COGS: product development (R&D), G&A, sales, marketing.

If the product relies heavily on LLM calls or other usage-based third-party costs, model COGS as a % of revenue at different utilization levels — this is where most early-stage SaaS gross margin surprises live.

**Payback period.** CAC / (monthly ACV × gross margin). Target: <18 months for SMB, <24 months for mid-market, <36 months for enterprise. Exceeding these ranges is a signal the economics don't work at scale.

**LTV/CAC ratio benchmarks (as benchmarks, not proofs):**
- <1: unit economics broken
- 1–2: break-even, not investable
- 3+: healthy if measured; aspirational if modeled
- 5+: suspicious unless cohort data confirms

**Pre-revenue stance.** If the company is pre-revenue, the unit economics section is a *target* with explicit "what would need to be true" framing. No ratios reported. Just: "for our model to work, CAC must be under $X, gross margin above Y%, churn under Z%. Here's why we think those are achievable."

## Flow

### Phase 1: Prereq check and context load

Read all three upstream outputs. Note customer count, months of history, and whether the company has paying customers.

Determine stage:
- **Pre-revenue:** no paying customers yet → target framing only
- **Early revenue (<20 customers, <12 months):** modeled numbers with heavy flagging
- **Emerging data (20–100 customers, 12+ months):** mix of modeled and measured — be explicit per metric
- **Real data (100+ customers, 18+ months):** mostly measured; still flag any that aren't

Open with (example for early-revenue company):

> "Your current data is [N customers, M months]. That's not enough to *measure* unit economics — the numbers will be modeled from your revenue plan and cost structure. I'll tag each metric as modeled or measured so nothing reads as proven when it isn't. Ready?"

### Phase 2: Gross margin

- Ask the founder for COGS line items if not obvious from cost-structure.md
- Flag any usage-based third-party cost that scales per customer (LLMs, payments, SMS)
- Compute gross margin at current revenue and at modeled future revenue (where scale may reduce unit COGS)
- Report as: "Gross margin at M6 (modeled): X%. At M18 (modeled): Y%."

### Phase 3: CAC

- Compute blended CAC from cost-structure.md + new-logo rate from revenue-model.md
- If any paid acquisition exists, compute paid CAC separately
- Discount founder-sold deals — founder time isn't free but it's also not sustainable, so don't extrapolate it
- Report per scenario (bear / base / bull) — CAC differs materially because of denominator

### Phase 4: LTV

- Use `ACV × gross margin × (1 / monthly churn)`, capped at 5 years
- Use base-case assumptions; report sensitivity to churn (Phase 6)
- Report contribution LTV, not revenue LTV

### Phase 5: LTV/CAC and payback

- Ratio and payback per scenario
- Flag any ratio above 5 for scrutiny (modeled 5+ is usually optimistic assumptions compounding)

### Phase 6: Sensitivity

A one-direction sensitivity table — "what happens to LTV/CAC if each of the key inputs moves 20% the wrong way":

| Input | Base | 20% worse | LTV/CAC at worse | Note |
|---|---|---|---|---|
| Churn | X% | 1.2X% | ... | |
| CAC | $Y | $Y × 1.2 | ... | |
| Gross margin | Z% | Z% − 6pp | ... | |
| ACV | $A | $A × 0.8 | ... | |

If LTV/CAC falls below 2 in any 20%-worse scenario, flag it explicitly.

### Phase 7: Honesty framing

Write an "honesty appendix":
- How many of these metrics are measured vs modeled
- Which assumptions are load-bearing (moving them breaks the picture)
- What would need to be true for the modeled picture to materialize
- What data collection would upgrade modeled → measured (cohort tracking, attribution, COGS allocation)

### Phase 8: Output

Show `unit-economics.md` preview. Iterate. On approval, write.

Surface downstream:

- `scenario-planner` uses CAC and gross margin directly in P&L
- Investor metrics summary will pull LTV/CAC, gross margin, payback

## Minimum Bar

Before writing:

- Every metric tagged `measured` or `modeled`
- Stage call made (pre-revenue / early / emerging / real data)
- CAC is fully loaded (headcount + tools + paid + allocated founder time)
- LTV uses contribution, not revenue, and caps at reasonable horizon
- Gross margin accounts for usage-based third-party costs
- Payback reported in months
- Sensitivity table for 20%-worse on each of (churn, CAC, gross margin, ACV)
- Honesty appendix present
- No ratio above 5 left unchallenged

## Output

**Project-scoped:** `projects/12-financial-modeling/outputs/unit-economics.md`

**Format:**

```markdown
---
generated_date: YYYY-MM-DD
stage: pre-revenue | early-revenue | emerging-data | real-data
customer_count: N
months_of_history: M
all_metrics_are: modeled | mixed | measured
schema_version: 1
---

# Unit Economics — YYYY-MM-DD

## Stage Disclaimer

[One paragraph. What stage of data the company has, and what that means for the numbers below.]

## Gross Margin

- Month 6 (modeled): X%
- Month 18 (modeled): Y%
- Source: cost-structure.md + revenue-model.md
- COGS components: [list]
- Sensitivity to usage-based costs: [note]

## CAC

### Base scenario
- Blended CAC: $X (modeled from $S&M / new logos)
- Paid CAC: $Y (if applicable)
- Fully-loaded inputs: [list]
- Founder time allocation: [note]

### Bear / Bull
- Bear CAC: $X1 (numerator same, denominator fewer new logos)
- Bull CAC: $X2 (numerator scales with hires, denominator more new logos)

## LTV

- ACV × gross margin × (1 / monthly churn), capped at 5 years
- Base: $Z
- Assumptions: ACV = $A, GM = B%, monthly churn = C%, horizon cap = 5y
- All modeled | measured — per input

## LTV / CAC

| Scenario | LTV | CAC | Ratio | Payback (months) |
|---|---|---|---|---|
| Base | | | | |
| Bear | | | | |
| Bull | | | | |

## Sensitivity

| Input | Base | 20% worse | LTV/CAC impact | Note |

## Honesty Appendix

- Metrics measured: [list or "none at this stage"]
- Metrics modeled: [list]
- Load-bearing assumptions: [list]
- What would need to be true: [list]
- Data collection to upgrade modeled → measured: [specific recommendations]

## Re-run trigger

[e.g., "after 20 paying customers with 6 months history," "if churn data starts contradicting the model"]
```

No global write.

## What Not To Do

- Don't present modeled LTV/CAC as measured
- Don't use revenue LTV (ignores COGS) — contribution LTV only
- Don't cap LTV at infinity — use a horizon
- Don't exclude founder time from CAC (if they're selling, it's a cost)
- Don't report a single CAC — scenarios differ
- Don't ignore usage-based third-party COGS
- Don't report LTV/CAC above 5 without a measured cohort to back it
- Don't skip the stage disclaimer — pre-revenue unit economics without a stage note is the #1 credibility killer
- Don't omit the honesty appendix
- Don't hand-wave payback — it's the clearest signal of whether the economics work
- Don't treat benchmarks as proofs ("SaaS churn is 5% so ours is 5%")
- Don't write to global context
