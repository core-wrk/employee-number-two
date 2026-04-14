---
name: scenario-planner
description: Synthesize revenue, costs, hiring, and unit economics into full runway scenarios (conservative / base / aggressive) plus the investor-facing metrics summary. Cash-out dates per scenario, sensitivity on the top 3 levers, and the 6–10 numbers investors actually ask about.
---

# Skill: Scenario Planner

## Role

You assemble the full picture. The three upstream skills produce the components; this skill turns them into a runway view and an investor-facing summary.

The first-principles stance: **a financial model exists to answer two questions — when does the money run out, and what are the levers to push that date out.** Everything else is decoration. The runway scenarios and sensitivity table *are* the model; the P&L is the plumbing.

The second output — `investor-metrics-summary.md` — is the one-page version for investor conversations. Six to ten numbers, each with one-line context. The founder should be able to recite it from memory. If the summary is longer than a page, it is not a summary.

Output is project-scoped. No global writes.

## Prerequisites

Read before starting:

- `projects/12-financial-modeling/outputs/revenue-model.md` — **required**. Source of revenue per scenario.
- `projects/12-financial-modeling/outputs/hiring-roadmap.md` — **required**. Source of headcount cost per quarter.
- `projects/12-financial-modeling/outputs/cost-structure.md` — **required**. Source of non-headcount costs.
- `projects/12-financial-modeling/outputs/unit-economics.md` — **required**. LTV/CAC, gross margin, payback feed the investor summary.
- `global/context/company-profile.md` — **required**. Currency, fiscal year, entity type.
- `projects/11-fundraising-prep/outputs/funding-landscape-overview.md` — recommended. Informs round size assumptions.
- `projects/11-fundraising-prep/outputs/investor-prospect-list.md` — recommended. Ticket ranges inform round-structure modeling.

**Cash position:** ask the founder for current cash balance directly. Do not guess. This is the anchor of every runway calculation.

**If any upstream output is missing, stop.** Tell the founder:

> "The scenario planner synthesizes the other four outputs. Missing: [list]. Run those skills first — re-running this one is cheap once they exist."

## Behavior

**Runway scenarios, named by outcome not optimism.** Use **Conservative / Base / Aggressive** for the scenario names in this skill's outputs, aligned with the revenue model's Bear / Base / Bull. The shift in naming is intentional — runway talks about founder choices, not market outcomes.

- **Conservative:** bear revenue × base hiring → shows what happens if revenue underperforms while hiring continues as planned. Reveals cut-decisions the founder may face.
- **Base:** base revenue × base hiring → the plan.
- **Aggressive:** bull revenue × bull hiring → shows how runway compresses even with good revenue if hiring accelerates. Often surprises founders.

**Cash-out date is the headline.** For each scenario, compute and display the specific month cash reaches zero. Not "12 months runway" — the month and year. "Cash zero: March 2027."

**Runway floor triggers.** Flag months where cash falls below 6 / 9 / 12 months of burn. These are the decision points — 12 months is "start planning next round," 9 is "actively raising," 6 is "bridge or cut." A founder seeing 6-month runway in Q4 should treat the model as a forcing function.

**Top-3 lever sensitivity.** For the base scenario, identify the three inputs that most affect cash-out date. Typically:
1. New-logo rate (revenue side)
2. Hiring pace (cost side)
3. One of: ACV, gross margin, or churn (varies by business)

Show runway extension (in months) for +/− 20% on each lever, individually. This is the operating dashboard: "if we slow hiring by 20%, runway extends by N months."

**Post-round modeling.** If the founder has a round in the plan, model both pre-round and post-round scenarios. Don't bake the raise into the base case as certain — show runway without it explicitly, then with it, so the founder can see which hires depend on the raise closing.

**Investor summary discipline — one page.** The six-to-ten numbers investors ask about:
1. Current ARR
2. Projected ARR (12 months)
3. Monthly burn (current)
4. Monthly burn (post-hire)
5. Runway (months from now)
6. LTV/CAC ratio (flag if modeled)
7. Gross margin
8. Payback period
9. Round size ask (if raising)
10. Use of funds (one sentence)

Each with one line of context. No extra prose. If a number is uncomfortable, include it and address it — leaving it out is worse.

**Honest framing at the top.** Every output opens with the same honesty statement: what stage of data, how many illustrative assumptions, confidence rating. Investors who read a lot of decks pattern-match optimism collapse — a model that leads with its limitations is more credible, not less.

## Flow

### Phase 1: Prereq check and cash anchor

Verify all four upstream outputs exist. Read them. Ask the founder:

> "I need your current cash balance (anchor for runway), your target round size if raising, and expected close date for that round. I'll model pre-round and post-round separately so the dependency is explicit."

### Phase 2: Monthly cash-flow build per scenario

For each of Conservative / Base / Aggressive:

```
For each month t:
  Revenue_t         = from revenue-model.md (for matched scenario)
  Gross profit_t    = Revenue_t × gross margin (from unit-economics.md)
  Opex_t            = People + tools + infra + G&A + paid acq (from cost-structure.md hiring-scenario-matched)
  Net burn_t        = Opex_t − Gross profit_t  (if positive, burning; if negative, profitable)
  Cash_t            = Cash_{t-1} − Net burn_t
```

Project to cash-out date or 36 months, whichever comes first.

### Phase 3: Cash-out date and runway floors

For each scenario:
- Cash-zero month: first month where Cash ≤ 0
- 12-month-runway month: first month where remaining runway < 12 months
- 9-month, 6-month triggers

Report as absolute dates ("March 2027"), not months-from-now.

### Phase 4: Sensitivity on top 3 levers

Identify the 3 levers that most shift cash-out date for the base scenario. For each:

| Lever | Base value | −20% | +20% | Cash-out shift (−20%) | Cash-out shift (+20%) |

Frame each shift in months of runway gained / lost.

### Phase 5: Round scenarios

If raising:
- Model base pre-round (no raise)
- Model base post-round with stated round size
- Show how round extends runway and which hires unlock
- Show what happens if the round closes 3 months later than planned (common)

### Phase 6: Investor metrics summary

Distill to one page. The 6–10 numbers above, each with one line. No prose. Frontmatter includes data-vintage and confidence.

### Phase 7: Decision memo (optional but recommended)

A 3–5 bullet "what this model is telling us" section. Examples:
- "Base case cash-out is March 2027. We need to be actively raising by September 2026."
- "The +/−20% hiring lever is twice as impactful as the +/−20% revenue lever in year 1 — cost discipline outweighs revenue upside short-term."
- "Unit economics are modeled, not measured. The first priority after this round closes is to generate real cohort data to validate."

### Phase 8: Output

Show `runway-scenarios.md` and `investor-metrics-summary.md` previews. Iterate.

On approval, write both. This is the terminal output of the entire project — no downstream skills to route to.

## Minimum Bar

Before writing:

- All four upstream outputs loaded
- Current cash anchored by founder
- Three scenarios present: Conservative / Base / Aggressive
- Cash-out date reported as absolute month/year for each
- Runway floors (6 / 9 / 12 months) flagged
- Top-3 lever sensitivity completed
- Pre-round and post-round modeled if raising
- Investor metrics summary is one page
- Honesty framing present in both outputs

## Output

**Project-scoped:**
- `projects/12-financial-modeling/outputs/runway-scenarios.md`
- `projects/12-financial-modeling/outputs/investor-metrics-summary.md`

**runway-scenarios.md format:**

```markdown
---
generated_date: YYYY-MM-DD
current_cash: $X
current_monthly_burn: $Y
round_in_plan: yes | no
round_size_assumed: $Z | null
round_close_assumed: YYYY-MM | null
base_case_cash_out: YYYY-MM
schema_version: 1
---

# Runway Scenarios — YYYY-MM-DD

## Honesty Framing

[One paragraph: data stage, illustrative count across upstream outputs, confidence rating.]

## Cash Anchor

- Current cash: $X (source: founder input, as of YYYY-MM-DD)
- Current monthly burn: $Y
- Baseline runway: N months (= current_cash / current_monthly_burn)

## Scenario: Base

### Monthly cash-flow build (CSV)

```csv
month,revenue,gross_profit,opex,net_burn,ending_cash
...
```

### Summary
- Cash-out date: YYYY-MM
- 12-month-runway trigger: YYYY-MM
- 9-month trigger: YYYY-MM
- 6-month trigger: YYYY-MM

### Narrative
[What the base case means. Which hires land. Which milestones hit.]

## Scenario: Conservative

[Same structure. Emphasize what cuts become necessary and when.]

## Scenario: Aggressive

[Same structure. Emphasize how hiring pace compresses runway even with good revenue.]

## Top-3 Lever Sensitivity (Base)

| Lever | Base | −20% impact on cash-out | +20% impact on cash-out |
|---|---|---|---|
| New-logo rate | | | |
| Hiring pace | | | |
| [3rd lever, e.g., gross margin] | | | |

## Round Scenarios

### Pre-round
- Cash-out: YYYY-MM (base scenario, no raise)

### Post-round
- Cash-out: YYYY-MM (base scenario, round of $X closing YYYY-MM)
- Hires unlocked by round: [list]
- If round closes 3 months late: cash-out = YYYY-MM

## Decision Memo

- [3–5 bullets]

## Re-run trigger

[New cash event, material revenue delta, hiring plan change, pricing change]
```

**investor-metrics-summary.md format:**

```markdown
---
generated_date: YYYY-MM-DD
data_vintage: YYYY-MM-DD
confidence: High | Medium | Low
illustrative_metric_count: N
schema_version: 1
---

# Investor Metrics Summary — YYYY-MM-DD

*Every number below traces to an upstream artifact in `projects/12-financial-modeling/outputs/`. Metrics flagged (modeled) are not measured.*

| Metric | Value | Context |
|---|---|---|
| Current ARR | $X | M paying customers |
| Projected ARR (12mo, base) | $Y | Bear $Y1 / Bull $Y2 |
| Monthly burn (current) | $Z | Post-hire: $Z' |
| Runway | N months | Cash-out YYYY-MM |
| Gross margin | X% (modeled) | COGS = [key drivers] |
| LTV / CAC | X (modeled) | Payback Y months |
| Round ask | $A | Use: [one sentence] |
| Round milestones | [one line] | Reach $X ARR by YYYY-MM |

## Honesty Notes

- [2–3 bullets on what is measured vs modeled and what would upgrade that]

## Re-run trigger

[Aligned with runway-scenarios.md]
```

No global write.

## What Not To Do

- Don't report runway as months only — use absolute cash-out dates
- Don't bake the round into the base case as certain — show pre- and post-round
- Don't assume the round closes on time — model a 3-month-late variant
- Don't average scenarios (a midpoint of bear and bull is not a plan)
- Don't omit the sensitivity table — it is the most useful section for operating decisions
- Don't let the investor summary exceed one page
- Don't hide uncomfortable numbers (low gross margin, long payback) — address them
- Don't present modeled metrics as measured
- Don't skip the honesty framing — it's the credibility gate
- Don't forget to re-run after round close or material revenue event
- Don't write to global context
- Don't attempt to replace a finance contractor / CFO once real P&L data exists — migrate to a proper workbook at that point
