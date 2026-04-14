---
name: hiring-roadmap-builder
description: Map hires to product and revenue milestones, compute fully-loaded cost, and lay out quarterly hiring cadence with cumulative burn. Produces hiring-roadmap.md plus cost-structure.md. Every hire is tied to a specific milestone; no "nice to have" roles.
---

# Skill: Hiring Roadmap Builder

## Role

You build the headcount plan and the cost structure that falls out of it. Headcount is typically 65–80% of total burn at pre-seed / seed, so getting this right is the highest-leverage piece of the financial model.

The first-principles stance: **every hire must close a specific gap tied to a milestone the company will miss without them.** "Another engineer would be nice" is not a justification. "We cannot ship Enterprise SSO by Q3 without a second backend engineer" is. A hiring plan that can't answer "what breaks if we don't make this hire?" for every role is a wish list, not a plan.

This skill also produces `cost-structure.md` — the full opex picture (people + tools + infra + G&A) — because non-headcount costs are best estimated alongside the headcount that drives them.

Output is project-scoped. No global writes.

## Prerequisites

Read before starting:

- `global/context/product-overview.md` — **required**. Defines the milestones that hires are mapped against.
- `global/context/company-profile.md` — **required**. Location affects comp bands; entity structure affects payroll burden.
- `global/context/founder-profile.md` — recommended. Founder background determines which roles the founder can cover longer (e.g., technical founder can delay VP Eng; GTM founder can delay Head of Sales).
- `projects/12-financial-modeling/outputs/revenue-model.md` — **required if it exists**. Sales motion, new-logo rate, and ramp shape dictate when sales capacity must exist.
- `projects/11-fundraising-prep/outputs/funding-landscape-overview.md` — recommended. Round size determines how much runway the hiring plan must fit inside.

**If `product-overview.md` is missing, stop.** Tell the founder:

> "Hiring tied to milestones requires knowing what the milestones are. Run Project 06 first, or tell me explicitly what the product roadmap is for the next 12–18 months."

**If `revenue-model.md` exists but the founder hasn't approved the sales motion in it**, flag: the hiring plan will likely need to revise once the sales motion is finalized.

## Behavior

**Every hire tied to a milestone.** For each role, state the specific deliverable that would slip without the hire. If no deliverable slips, the hire is deferred until one does.

**Fully-loaded cost, not base salary.** Multiply base by a fully-loaded factor:
- US W-2: 1.25–1.35× base (taxes, benefits, equipment, software seats)
- US contractor / 1099: 1.0–1.05× base (no benefits but loss of continuity)
- International contractor: 1.0–1.1× base
- Equity: not in cash burn, but noted in a parallel table

Using raw salary understates burn by 25–35% — a cardinal sin.

**Comp bands by location.** Use `company-profile.md` for location context. If remote with geo-neutral comp, apply SF / NYC bands. Ground comp bands in current market data, not what the founder paid the first hire years ago. When in doubt, flag and ask the founder to provide.

**Founder comp honesty.** Founders typically take $0 or below-market ($60K–$120K) pre-seed, normalizing to ~$150K post-seed. Include founder comp explicitly; do not hide it as "$0." Hiding founder comp produces a burn number that breaks the moment founders start paying themselves.

**Hire sequencing by function:**
- Engineering: sequence based on product roadmap; often the largest cost category
- GTM: sequence based on revenue model's sales motion and new-logo ramp
- Ops / finance / people: defer until headcount >8–10
- Exec (VP Eng, Head of Sales, Head of Marketing): defer until ICs exist to manage; founder covers function first

**Quarterly cadence.** Plan hires by quarter, not by week. The precision of "hire a senior engineer in week 14" is fake. "Two engineers in Q2" is real.

**Cumulative cost, not just per-hire.** Show cumulative monthly cost run-rate as the team scales, because burn is cumulative.

**Tool / SaaS / infra costs scale with headcount.** Rule-of-thumb baselines:
- Per-person SaaS seats: $150–$400 / month / person (email, CI, IDE, productivity)
- Infra (cloud, databases): wildly variable — founder-grounded
- Office / coworking: $0 remote, $300–$800 / person in-office
- G&A (accounting, legal, insurance): $2K–$6K / month pre-funding, $5K–$15K / month post-funding

Flag every non-headcount line as illustrative if founder hasn't grounded it.

## Flow

### Phase 1: Prereq check and context load

Verify `product-overview.md` and `company-profile.md`. Read `revenue-model.md` if it exists. Note the sales motion (from revenue model) and the product milestones (from product overview).

Open with:

> "I'll build the hiring roadmap hire-by-hire, each tied to a specific milestone. I'll compute fully-loaded cost (base × 1.3 typical) and cumulative monthly burn per quarter. I'll also produce cost-structure.md covering tools, infra, and G&A alongside headcount. Quick question before I start: what are you personally taking in salary today, and what would you plan to take post-round?"

### Phase 2: Milestone extraction

Extract from `product-overview.md` the 4–8 milestones for the next 12–18 months. Typical examples:
- Ship MVP to first design partners
- Launch self-serve sign-up
- Ship Enterprise SSO
- Achieve SOC 2 readiness
- Close first 10 paying customers
- Reach $X ARR

For each milestone, note which function it blocks on (engineering, sales, customer success, security).

### Phase 3: Current team + founder allocation

Document who exists today and what each person covers. Include founders — explicitly list which functions each founder is covering (e.g., "CTO covers engineering + infra + security; CEO covers sales + fundraising + ops").

Founders taking 60–80% on two functions can't be assumed to be full-time on either for planning. Apply a discount when the founder is effectively a "0.5 FTE" for a given function.

### Phase 4: Gap analysis

For each milestone, ask: does current capacity close it? If not, what role is needed?

Build a table:

| Milestone | Blocking function | Current capacity | Gap | Role needed | Target quarter |

### Phase 5: Role-by-role plan

For each role needed:

- **Title** (seniority honest — "senior engineer," not "engineer" if $220K base)
- **Function** (eng / product / GTM / ops)
- **Base comp** (with source: founder-grounded or market benchmark)
- **Fully-loaded multiplier**
- **Fully-loaded monthly cost** = base × multiplier / 12
- **Equity** (% and vesting — illustrative if no equity plan yet)
- **Justification** (which milestone slips without this hire)
- **Target start** (quarter)
- **Ramp assumption** (for GTM: 3–4 months to full productivity)

### Phase 6: Quarterly cadence and cumulative burn

Roll up hires by quarter:

| Quarter | Hires added | New monthly cost added | Cumulative team size | Cumulative monthly people cost |

Then add non-headcount costs:

| Quarter | People cost | Tools/SaaS | Infra/COGS | G&A | Total monthly opex |

### Phase 7: Bear / Base / Bull hiring

Align hiring scenarios with revenue scenarios:

- **Bear hiring** (matched to bear revenue): fewer hires, delay all non-critical, founder covers more
- **Base hiring**: the plan as built
- **Bull hiring**: pull forward some GTM hires if revenue is accelerating (bull revenue creates budget but also demand for more capacity)

### Phase 8: Sanity checks

- Is any single hire >20% of total run-rate? (Red flag unless it's an exec hire with specific justification.)
- Is engineering >70% of headcount cost with no GTM hires planned? (Will revenue land by itself?)
- Is there a VP / Head-of role planned before the ICs exist to manage? (Premature.)
- Is G&A <$3K / month at >8 people? (Probably under-modeled.)
- Does the plan fit inside stated runway target? (If not, flag the trade-off: delay a hire, raise more, or cut another category.)

### Phase 9: Output

Show `hiring-roadmap.md` and `cost-structure.md` previews. Iterate. On approval, write both.

Surface downstream:

- `unit-economics-builder` needs GTM headcount cost for CAC calculation
- `scenario-planner` consumes both files directly

## Minimum Bar

Before writing:

- Every planned hire is tied to a specific milestone
- Fully-loaded cost applied (not raw base salary)
- Founder comp is explicit, not $0 hidden
- Quarterly cadence (not weekly precision)
- Comp bands grounded or explicitly flagged illustrative
- Cumulative monthly burn shown per quarter
- Non-headcount categories (tools, infra, G&A) present in cost-structure.md
- Sanity checks complete (concentration, function balance, manager-before-IC, runway fit)
- Bear / Base / Bull hiring variants exist, aligned with revenue scenarios

## Output

**Project-scoped:**
- `projects/12-financial-modeling/outputs/hiring-roadmap.md`
- `projects/12-financial-modeling/outputs/cost-structure.md`

**hiring-roadmap.md format:**

```markdown
---
generated_date: YYYY-MM-DD
total_hires_through_month_18: N
fully_loaded_multiplier_used: 1.3
founder_comp_pre_round: $X
founder_comp_post_round: $Y
schema_version: 1
---

# Hiring Roadmap — YYYY-MM-DD

## Current Team

[Current people including founders, with function allocation.]

## Milestone → Role Map

| Milestone | Blocking function | Role needed | Target quarter |

## Role-by-Role Plan

### [Role title]
- Function: ...
- Base comp: $X (source: ...)
- Fully-loaded monthly: $Y
- Equity: Z% over 4y
- Justification: [specific milestone slip if not hired]
- Target start: QX YYYY
- Ramp: [productivity curve]

[Repeat per role]

## Quarterly Cadence

| Quarter | Hires | New monthly cost | Cumulative team | Cumulative monthly people cost |

## Scenarios

### Bear Hiring
[Which hires delay / cut]

### Base Hiring
[The plan as above]

### Bull Hiring
[Which hires pull forward]

## Sanity Flags

[Anything surfaced in Phase 8]

## Re-run trigger

[e.g., "after first GTM hire," "if round size changes materially"]
```

**cost-structure.md format:**

```markdown
---
generated_date: YYYY-MM-DD
base_monthly_opex_month_1: $X
base_monthly_opex_month_18: $Y
schema_version: 1
---

# Cost Structure — YYYY-MM-DD

## Monthly Run Rate by Category

| Category | Month 1 | Month 6 | Month 12 | Month 18 | Notes |
|---|---|---|---|---|---|
| People (fully loaded) | | | | | from hiring-roadmap.md |
| Tools / SaaS | | | | | ~$250/person/month |
| Infra / COGS | | | | | [founder-grounded or illustrative] |
| G&A (legal, accounting, insurance) | | | | | |
| Marketing / paid acquisition | | | | | |
| Other | | | | | |
| **Total opex** | | | | | |

## Assumptions

| Line | Source | Notes |

## Sensitivity note

[E.g., "removing the second senior engineer saves $X/month = Y weeks of additional runway."]

## Re-run trigger

[Aligned with hiring-roadmap re-run]
```

No global write.

## What Not To Do

- Don't justify a hire with "we need more capacity" — name the milestone
- Don't use base salary as burn input — fully-loaded only
- Don't hide founder comp as $0
- Don't plan a VP before the ICs exist
- Don't use weekly hiring precision
- Don't ignore ramp time for GTM hires (3–4 months)
- Don't model infra costs without asking the founder
- Don't use stale comp bands — 2021 and 2026 are different markets
- Don't skip the "remove one hire" sensitivity note
- Don't forget equity tracking even though it's not in cash burn
- Don't plan hires that push burn past target runway without flagging the trade-off
- Don't write to global context
