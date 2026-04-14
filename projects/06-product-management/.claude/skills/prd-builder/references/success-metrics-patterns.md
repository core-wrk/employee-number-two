# Success Metrics Patterns

Internal reference used by `prd-builder` for Phase 5. Every success metric must have a **name**, **baseline**, **target**, and **measurement method**. This file provides product-type templates.

## Universal Requirements

Every metric must satisfy:

1. **Measurable today** — if you can't measure it at the baseline date, it is not a metric. It is a goal.
2. **Specific target** — a number, not a direction. "Reduce churn" is not a target; "reduce monthly gross churn from 8% to 4%" is.
3. **Explicit method** — how it is instrumented (product analytics, Stripe MRR export, manual survey, etc.)
4. **Tied to a goal** — every metric links back to a Section 5 goal. Orphan metrics get cut.

## B2B SaaS (Sales-Assist)

| Metric | Baseline Pattern | Target Pattern | Method |
|---|---|---|---|
| Design partner signed | 0 | N signed within 90 days | CRM opp stage = "Signed" |
| Pilot-to-paid conversion | N/A (new product) | 50% of pilots convert to paid | CRM opp velocity |
| Time to first value | Unknown | <14 days from kickoff | Product analytics event |
| Logo retention | N/A (new product) | >90% at 12 months | CRM renewal tracking |
| Net revenue retention | N/A | >110% at 12 months | MRR expansion from existing accounts |
| Discovery-to-pilot conversion | N/A | 30% of discovery calls → pilot | CRM pipeline report |

## B2B SaaS (Self-Serve / PLG)

| Metric | Baseline Pattern | Target Pattern | Method |
|---|---|---|---|
| Signup → activation | N/A | 30% activate within 7 days | Product analytics funnel |
| Free → paid conversion | N/A | 3–8% of free users → paid within 30 days | Stripe + product analytics |
| Monthly active accounts | 0 | N by month 6 | Product analytics |
| Weekly active usage per account | N/A | >3 sessions/week | Product analytics |
| Referral coefficient | 0 | K-factor >0.3 | Referral source tracking |

## Dev Tools

| Metric | Baseline Pattern | Target Pattern | Method |
|---|---|---|---|
| GitHub stars | Current count | +N within 90 days | GitHub API |
| Weekly downloads/installs | N/A | N/week by month 3 | npm/PyPI/registry stats |
| Documentation → first API call | N/A | 50% within 1 hour | API analytics + docs analytics |
| Active projects using the tool | 0 | N by month 6 | Unique project IDs in telemetry |
| Community PR contributions | 0 | N PRs merged from external contributors | GitHub |

## Marketplace (Two-Sided)

| Metric | Baseline Pattern | Target Pattern | Method |
|---|---|---|---|
| Supply-side signups | 0 | N per week | Backend DB |
| Demand-side signups | 0 | N per week | Backend DB |
| Match rate | 0 | N% of demand requests get a supply match | Backend analytics |
| Time to first match | N/A | <24 hours | Backend timestamps |
| Take rate | N/A | N% of GMV | Stripe + backend |
| Supply retention (30-day) | N/A | >60% | Supply-side cohort analysis |

## Consumer

| Metric | Baseline Pattern | Target Pattern | Method |
|---|---|---|---|
| Daily active users | 0 | N DAU by month 3 | Product analytics |
| D1/D7/D30 retention | N/A | 40/20/10 (example) | Product analytics cohort |
| Session frequency | N/A | >4 sessions/week/user | Product analytics |
| App store rating | N/A | >4.5 stars | App store |
| Social referral rate | 0 | >20% of new users from referral | Attribution |

## Anti-Patterns to Reject

Push back immediately on any of these:

- **"Delight users"** — not measurable
- **"Grow MRR"** — no target
- **"Improve UX"** — not a metric
- **"Reduce churn"** — no baseline or target
- **"Achieve product-market fit"** — not a metric; it's a goal that needs its own metrics
- **Metrics whose baseline is "TBD"** — if you can't measure it today, instrument it before adding to the PRD
- **Vanity metrics without decision rights** — "signups" with no definition of what counts, "users" with no activity threshold

## The Instrumentation Check

For every metric, ask:

> "If we look at this metric 90 days after launch, how do we pull the number? Name the tool, the report, and the query."

If the founder cannot answer, the metric is not instrumented. Either instrument it first, or move the metric to "Phase 2" and replace it with something measurable today.

## Minimum Count

At least **3 metrics** in Section 6. Ideally 4–6. More than 8 is usually an over-scoped PRD trying to measure everything — force a cut.

## Metric → Goal Map

Include a brief table in Section 6 showing which metric supports which goal:

| Metric | Supports Goal # |
|---|---|
| Design partner signed | Goal 1 |
| Pilot-to-paid conversion | Goal 1, Goal 2 |
| Time to first value | Goal 2 |

Metrics that don't support any goal get cut. Goals without supporting metrics are aspirations, not goals — move them to Section 10 as assumptions.