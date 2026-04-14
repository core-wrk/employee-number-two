# Scenario Planning Variables

Working reference for `scenario-planner`. The levers that actually move runway, typical magnitudes, and which combinations produce which outcomes.

---

## 1. The five levers that matter

At pre-seed / seed, runway is a function of a small number of variables. Most founders overestimate which variables matter in year 1.

| Lever | Typical runway impact (12-month window) | Notes |
|---|---|---|
| Hiring pace | **Very high** | Headcount is 65–80% of burn. Delaying two hires by 3 months often extends runway more than doubling revenue does. |
| New-logo rate | Medium | In year 1, revenue is usually too small to materially change burn. Matters more in year 2+. |
| Average ACV | Medium | Same dynamic as new-logo rate. Per-customer economics matter at scale, not immediately. |
| Gross margin | Medium–high if usage-based | If COGS scales with usage (LLMs, APIs), gross margin degradation is a silent runway killer. |
| Churn | Low in year 1, high in year 2 | Churn compounds. Low customer counts + 12 months = not much impact. 100+ customers + 2 years = meaningful. |

**Implication:** in year 1, cost discipline is the dominant lever. In year 2+, revenue execution becomes dominant. The model should reflect this shift.

---

## 2. Scenario composition patterns

Scenarios are built by combining revenue and hiring scenarios. Not all 9 combinations are useful. The four worth reporting:

| Name | Revenue | Hiring | What it shows |
|---|---|---|---|
| **Conservative** | Bear | Base | What happens if revenue underperforms and we don't adjust. Reveals the cuts founders may face. |
| **Base** | Base | Base | The plan. |
| **Aggressive** | Bull | Bull | Good year + accelerated hiring. Often surprising — hiring can compress runway faster than revenue expands it. |
| **Survival** (optional) | Bear | Bear | Explicit cut plan: which hires delayed / cut if revenue lags. Useful as a pre-planned response to a miss. |

Do not report all 9 combinations. Pick 3 (Conservative, Base, Aggressive); consider adding Survival if the founder wants a pre-agreed cut plan.

---

## 3. Sensitivity magnitudes

Typical runway extension per lever when the lever moves 20%:

| Lever | 20% worse → runway impact | 20% better → runway impact |
|---|---|---|
| Hiring pace (slower) | +1.5 to +3 months | N/A (faster hiring shortens) |
| Hiring pace (faster) | N/A | −2 to −4 months |
| New-logo rate | −0.5 to −1.5 months | +0.5 to +1.5 months |
| ACV | −0.5 to −1.5 months | +0.5 to +1.5 months |
| Gross margin | −1 to −2 months | +1 to +2 months |
| Churn | −0.2 to −1 month (year 1) | +0.2 to +1 month (year 1) |

These are starting points for the sensitivity table, not answers. Compute from the actual model.

**What this tells you:** in year 1, hiring pace is the single biggest lever. A 20% slowdown in hiring often buys more runway than a 20% revenue beat. Founders tend to intuit the reverse; the model corrects this.

---

## 4. Round-timing modeling

Rounds do not close on announced dates. Common slippage:

- Stated "closing in 2 months" → actual median is 4 months
- Lead-investor change mid-process adds 6–10 weeks
- Legal and diligence at seed+ adds 4–8 weeks beyond handshake

Always model the round with three date variants:
- **On time**: founder-stated close date
- **3 months late**: the more realistic scenario
- **Does not close**: bridge or cut plan

The "does not close" variant is not pessimism — it's prudence. Investors read models that include this variant as more credible, not less.

---

## 5. Runway floor triggers

Standardized triggers for operating decisions:

| Runway remaining | Trigger action |
|---|---|
| 12 months | **Plan the raise.** Start refining deck, updating investor list, thinking about lead investors. |
| 9 months | **Start the raise.** Begin outreach, take meetings. |
| 6 months | **Escalate.** Bridge, cut burn, or accelerate. Bad raise terms get worse below 6 months. |
| 3 months | **Emergency.** Bridge round, significant cuts, or wind-down conversation. |

Flag each trigger in the scenario output with the absolute month/year.

---

## 6. Cash-out date discipline

Report cash-out as:
- Absolute date: "March 2027"
- Not: "in 14 months"

Reasons:
- "14 months" becomes 8 months in 6 weeks without the founder noticing
- Absolute dates force the calendar conversation ("what's happening in March? Any board commitments, product launches, conferences?")
- Investors read months-from-now as soft; dates as hard

---

## 7. Common scenario-modeling failure modes

- **Averaging scenarios.** "Bear plus bull divided by two" is not base. Each scenario is a coherent narrative, not an arithmetic midpoint.
- **Baking the round into base.** The base case should show cash-out without the raise. Then show how the raise extends it.
- **Ignoring round-close delay.** Everyone plans for on-time close. Few rounds close on time.
- **Conservative = Bear.** Conservative uses bear revenue *with base hiring* on purpose — it shows the mismatch between optimistic cost plans and pessimistic revenue.
- **Aggressive = more hires.** Aggressive often has worse runway than base because hiring compresses cash faster than revenue expands it in year 1. Founders routinely miss this; the model should surface it.
- **No floor triggers.** A cash-out date 14 months out feels comfortable. Flagging the 12/9/6 month trigger dates reframes urgency.
- **Missing the hiring sensitivity.** The highest-leverage lever is the most commonly under-examined. Always include it in sensitivity.
- **Investor summary longer than one page.** If it's longer than a page, it's not a summary.
- **Static model after round close.** Post-round, the assumptions change materially (more cash, different hiring plan, different milestone pressure). Re-run.

---

## 8. What a good runway scenario output looks like

The founder reads the output and can, within 60 seconds, answer:

- When does cash run out in each scenario?
- What's the one lever that most extends runway?
- What's the cost of a 3-month-late round close?
- Which 3 hires can I delay if revenue lags?
- What would I tell an investor about our financial discipline?

If the output does not enable those answers immediately, it is not done.
