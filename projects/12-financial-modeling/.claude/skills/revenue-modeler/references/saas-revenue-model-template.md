# SaaS Revenue Model Template

Working reference for `revenue-modeler`. Describes the ARR build mechanics, scenario-differentiation patterns, and common-failure modes.

---

## 1. ARR Build Identity

For any period (month or quarter):

```
Ending ARR = Starting ARR + New ARR + Expansion ARR − Churn ARR

where:
  New ARR       = new logos × blended ACV
  Expansion ARR = (mechanism-specific; often = starting ARR × NRR_lift_rate)
  Churn ARR     = starting ARR × gross churn rate (logo or revenue)
```

Net New ARR = New ARR + Expansion ARR − Churn ARR.

Net Revenue Retention (NRR) = (Starting ARR + Expansion − Churn) / Starting ARR. Report this in the output only once there is a real cohort to measure against — pre-revenue NRR is nonsense.

## 2. Blended ACV calculation

```
Blended ACV = Σ (tier_mix_share × tier_ACV)
```

If pricing is:
- Starter: $6K/yr, expected mix 70%
- Pro: $18K/yr, expected mix 25%
- Enterprise: $60K/yr, expected mix 5%

Blended ACV = (0.70 × 6000) + (0.25 × 18000) + (0.05 × 60000) = $4,200 + $4,500 + $3,000 = $11,700.

The mix shifts over time as larger customers are acquired — model the shift explicitly, not via a single blended number for all 36 months.

## 3. New-logo ramp shapes

Realistic ramp shapes depend on GTM motion:

**Self-serve (PLG):**
- Months 1–3: 0 (product readiness)
- Months 4–6: slow ramp (1–5 / month)
- Months 7–12: acceleration if funnel works (double every 1–2 months until a ceiling)
- Year 2: flatter growth unless new acquisition channel opens

**Sales-assisted:**
- Months 1–3: 0–1 (founder-led only)
- Months 4–9: slow ramp tied to first AE hire
- Months 10–18: hire-led growth — each new AE adds capacity at a lag of 3–4 months

**Sales-led / enterprise:**
- Months 1–6: 0–2 (founder-led design partner deals)
- Months 7–12: 1–3 / quarter
- Year 2: if sales team is built, 2–4 / month by end of year 2

Map the scenario's new-logo rate to the motion. A PLG model should not show a flat sales-led ramp; an enterprise sales-led model should not assume self-serve volume.

## 4. Scenario differentiation

Differentiate scenarios by inputs, not by fudge-factors. Keep the structure identical; change the numbers.

| Lever | Bear | Base | Bull |
|---|---|---|---|
| New-logo rate | 50–70% of base | honest plan | 130–160% of base |
| Sales-cycle length | 1.3× base | base | 0.8× base |
| Gross churn | 1.5× base | base | 0.6× base |
| Expansion / NRR | 0 (no mechanism assumed) | modest (if mechanism) | real (if mechanism supports it) |
| Tier mix shift to Pro/Ent | slower / none | planned pace | faster if upmarket motion exists |
| ACV (for usage-based tiers) | lower usage per customer | expected | higher usage per customer |

Each scenario must be narratively coherent: "Bull" is not just "all levers 130%"; it is "we land 3 lighthouse customers in Q2, expansion accelerates in Q3, and we close one enterprise deal by Q4."

## 5. Churn modeling

**Logo churn vs revenue churn:**
- Logo churn: % of customers who cancel
- Revenue churn: % of revenue lost (before expansion)

Revenue churn is almost always lower than logo churn in SaaS because large customers churn less. For pre-seed / seed with no data, model them equal and note the simplification.

**Benchmark ranges (illustrative only, never as "measured"):**
- SMB SaaS: 4–8% monthly logo churn (high!)
- Mid-market: 0.7–1.5% monthly
- Enterprise: 0.2–0.5% monthly

Convert monthly to annual via: `(1 − monthly_churn)^12` → annual retention; annual churn = 1 − that.

## 6. Expansion modeling

Only model expansion if a mechanism exists:

**Seat expansion:** customers add seats over time. Drivers: team growth at customer, department rollout. Model: average seats at M1 → average seats at M12 per customer tier.

**Usage expansion:** customers consume more of the metered product. Model: usage per customer at M1 → M12.

**Upsell / tier migration:** customers move from Starter → Pro → Enterprise. Model: % of cohort migrating per quarter.

**Cross-sell:** new product line sold to existing customers. Only model if the second product exists or ships during the modeled window.

If none of the four apply, expansion is 0 and NRR = 100 − churn. Do not claim 110% NRR without a mechanism.

## 7. Sales motion — ramp ceilings

Each AE has a capacity ceiling:

- Inbound-heavy AE: 8–12 closed deals / quarter typical at seed stage
- Outbound SDR-fed AE: 4–8 closed deals / quarter
- Enterprise AE: 2–4 closed deals / quarter

Founder-led selling: 2–5 closed deals / month maximum, declining as other responsibilities grow.

If the model assumes 20 new logos / month in month 9 with only the founder selling, the model is broken. Flag and route the gap to `hiring-roadmap-builder`.

## 8. Common failure modes

- **Bull disguised as base.** If the base case is "we 10× revenue in year 1," it is probably bull. Ask the founder for the 50th-percentile outcome, not the aspirational one.
- **Flat churn across scenarios.** Churn should differ by scenario — bear assumes worse product-market fit signal, bull assumes better.
- **Expansion without mechanism.** Claiming 115% NRR without naming the lever is the most common fabrication in early-stage models.
- **Linear ramp.** Real ramps are S-shaped. Linear ramps understate early difficulty and overstate mid-stage acceleration.
- **TAM-driven projection.** "1% of $10B market" is not a projection. It is a context slide. Remove from the model itself.
- **Ignoring fiscal-year boundaries.** ARR reported at Dec 31 is not the same as revenue recognized in the calendar year. For investor-facing summaries, report both.
- **36+ month projections treated as plans.** Beyond 36 months, label as "illustrative trajectory," not "projection."
- **Using monthly granularity in years 2–3.** Spurious precision. Quarterly is honest.
