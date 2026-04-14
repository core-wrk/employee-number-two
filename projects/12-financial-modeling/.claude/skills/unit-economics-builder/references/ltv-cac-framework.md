# LTV / CAC Framework

Working reference for `unit-economics-builder`. Formulas, benchmark ranges, and the common failure modes that distinguish real unit economics analysis from theater.

---

## 1. Formulas

### CAC (Customer Acquisition Cost)

```
CAC (blended) = total S&M spend in period / new customers acquired in period
CAC (paid)    = paid acquisition spend in period / customers attributed to paid
```

**Total S&M spend** includes:
- Sales headcount (AEs, SDRs, sales engineers, sales ops) — fully loaded
- Marketing headcount — fully loaded
- Paid acquisition (ads, sponsorships)
- Sales & marketing tools (CRM, outbound tools, attribution)
- Events, content production
- Allocated founder time (discounted — see below)

**Do not include:** product development, G&A, customer success (that's retention cost, belongs to LTV side).

**Founder-time allocation:** if the founder is actively selling, 30–60% of founder compensation is an S&M cost. This is often the largest hidden CAC component at pre-seed. Don't exclude it; don't also extrapolate it into future scale (founder-led selling is not scalable).

### Gross margin

```
Gross margin % = (Revenue − COGS) / Revenue
```

**COGS for SaaS includes:**
- Cloud infrastructure (AWS, GCP, Azure)
- Databases, monitoring, logging
- Third-party APIs that scale per customer (LLM calls, SMS, payments rails, email)
- Hosting / CDN
- Customer support personnel (allocated portion; full-time support engineers = 100%)

**Excluded from COGS:** R&D, G&A, S&M.

**Gotcha — LLM-heavy products:** if the product is built on LLM calls, COGS per customer can be 30–60% of revenue, producing gross margins in the 40–70% range — lower than traditional SaaS. This is not a crisis per se, but it must be modeled, not hidden.

### LTV (Lifetime Value)

**Contribution LTV (use this):**

```
LTV = ACV × gross margin % × (1 / monthly churn)
```

For monthly churn, this collapses a geometric series. Cap at a reasonable horizon to avoid infinite-retention assumptions:

```
LTV_capped = ACV × gross margin × Σ(t=1 to T) (1 − churn)^t
```

where T = 60 months (5 years) or 84 months (7 years) is a common cap.

**Do not use:**
- Revenue LTV (ignores COGS — overstates by gross margin factor)
- LTV with no horizon cap (implies infinite retention, which does not exist)
- LTV without churn grounding (if you don't know churn, you don't know LTV — say so)

### LTV / CAC ratio

```
LTV / CAC = LTV / fully-loaded CAC
```

### Payback period

```
Payback (months) = CAC / (monthly ACV × gross margin %)
```

Where monthly ACV is ACV / 12.

---

## 2. Benchmarks (directional only — never as proof)

| Metric | SMB SaaS | Mid-market | Enterprise |
|---|---|---|---|
| Gross margin | 65–80% | 70–85% | 75–85% |
| Monthly logo churn | 4–7% | 1–2% | 0.3–0.8% |
| LTV/CAC at healthy | 3–5 | 3–4 | 3–5 |
| Payback | 6–18 months | 12–24 months | 18–36 months |
| Blended CAC (illustrative) | $500–$3K | $5K–$25K | $30K–$150K+ |

These are **benchmarks for orientation**, not targets. A company running well below the benchmark may have a structural cost problem; a company running well above may have a measurement problem (optimistic assumptions compounding).

---

## 3. The "LTV/CAC 4.2 with 12 customers" problem

Common pattern: early-stage deck claims LTV/CAC of 4.2.

Inspect:
- 12 paying customers, 6 months of history
- Churn assumed at 5% monthly (no actual cohort data)
- ACV = $15K
- Gross margin assumed 80% (no COGS allocation yet)
- CAC computed as paid acquisition only, excluding founder time

Every input is modeled. The ratio is a function of the founder's optimism, not the company's economics. The correct framing:

> "Based on current assumptions, modeled LTV/CAC is 4.2. This number is not measured — we have 12 customers and 6 months of history. For this ratio to materialize at scale, we need: churn below 5%, CAC of $X fully loaded, gross margin ≥80% once infra scales. Here's what we're doing to validate each."

That version is credible. The one-liner "LTV/CAC is 4.2" is not.

---

## 4. Pre-revenue framing

If no paying customers:
- Report no ratios
- Instead, report the "target" economics with "what would need to be true":
  - Target payback: X months → requires CAC of $Y at ACV of $Z
  - Target LTV/CAC: 3+ → requires churn below X% at gross margin above Y%
- Ground every target in a mechanism the founder believes is achievable (PLG funnel conversion rate, outbound response rate, average deal size from design-partner conversations)

Pre-revenue unit economics are a **hypothesis**, not a metric. Framing them that way is the single most important credibility move at pre-seed.

---

## 5. Sensitivity — the 20% rule

For any modeled LTV/CAC, test what happens if each key input moves 20% in the wrong direction:

| Input | 20% worse means |
|---|---|
| Churn rate | 5% → 6% |
| CAC | $1000 → $1200 |
| Gross margin | 80% → 64% (note: 20% relative, so −16pp) |
| ACV | $12K → $9.6K |

If the ratio falls below 2 in any single-variable shock, the economics are fragile. If it falls below 2 when two variables shock together, the model is brittle — flag and have the founder revisit assumptions.

---

## 6. Common failure modes

- **Using benchmark churn as measured.** "SaaS churn is 5%" is not a measurement of your product's churn. Label as illustrative.
- **Excluding founder time from CAC.** The most common omission at pre-seed. Founder-led selling has a real cost; include 30–60% of founder comp.
- **Revenue LTV instead of contribution LTV.** Inflates LTV by 1/gross-margin (25–50% overstatement).
- **Infinite-horizon LTV.** Assumes customers never leave. Cap at 5–7 years.
- **CAC excluding tools and paid spend.** Fully loaded means fully loaded.
- **Blending cohorts of wildly different economics.** SMB self-serve and enterprise sales-led should be reported separately, not blended into a single CAC / LTV.
- **Payback period missing.** Investors look at payback first — a short payback with a modest LTV/CAC often beats a long payback with a big ratio.
- **Not separating organic from paid.** Organic is real but not scalable. Paid CAC is the lever that must work for growth.
- **Treating LLM-call costs as R&D instead of COGS.** They scale per customer — they are COGS.
- **Reporting a single number without a scenario label.** Unit economics differ bear / base / bull.
- **Not updating after real data arrives.** A model built at 0 customers is obsolete at 50 customers. Re-run.
