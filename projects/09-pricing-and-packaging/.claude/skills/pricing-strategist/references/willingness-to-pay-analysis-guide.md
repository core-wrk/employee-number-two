# Willingness-to-Pay Analysis Guide

Reference for the `pricing-strategist` skill. Covers how to extract WTP signal from beta feedback, how to read Van Westendorp–style results, and how to weight competitive anchors without copying them.

---

## Where WTP signal actually comes from

Founders frequently ask "will you pay for this?" Answers to that question are almost entirely useless — buyers over-report willingness in surveys and under-report in purchase moments.

Real WTP signal comes from:

1. **Direct price anchors.** A respondent names a number: "I'd pay $50/month for this," or "our budget for tools like this is $10K/year." Capture verbatim.
2. **Alternative-cost anchors.** What the respondent currently spends solving this problem another way — competitor subscription, internal tool, contractor time. This is the buyer's existing reference point.
3. **Switching behavior.** Has the respondent left a prior tool? At what price point? Why? Switching is the truest revealed preference.
4. **Budget authority signal.** Does the respondent have discretionary spend, or does anything above $X require approval? The ceiling on discretionary spend is often the right anchor for self-serve pricing.
5. **Form preferences.** Monthly / annual / per-seat / usage / one-time — respondents often have strong preferences rooted in their accounting workflow (opex vs. capex, budget cycle timing).
6. **Pricing objections.** "That seems expensive" is weak signal. "That's more than we pay for [specific comparable tool]" is strong signal. Specificity is the discriminator.

If the synthesis reports from Project 08 do not include these structured fields, the WTP signal is likely thin even if it feels rich.

---

## Van Westendorp's Price Sensitivity Meter

A four-question framework that produces a defensible price range. Beta surveys may include it; if they did, the synthesis report should have the results.

The four questions:

1. **Too cheap:** "At what price would you consider this product to be so inexpensive that you'd question its quality?"
2. **Cheap / bargain:** "At what price would you consider this product to be a bargain — a great buy for the money?"
3. **Expensive:** "At what price would you consider this product starting to get expensive, but you would still consider buying it?"
4. **Too expensive:** "At what price would you consider this product to be so expensive that you would not consider buying it?"

Plotting the four responses as cumulative curves produces two intersection points:

- **Point of Marginal Cheapness (PMC):** Where "too cheap" crosses "expensive." Below this, quality perception suffers.
- **Point of Marginal Expensiveness (PME):** Where "cheap" crosses "too expensive." Above this, the deal base erodes quickly.
- **Indifference Price Point (IPP):** Where "cheap" crosses "expensive." The median acceptable price.
- **Optimal Price Point (OPP):** Where "too cheap" crosses "too expensive." The price with the fewest rejections.

In most practical analyses with small beta samples, you will not have statistically clean curves. Use the individual responses directly: identify the cluster, report it as a range, note how many respondents contributed, and split by Tier A / Tier B.

**Small-sample caveat:** With fewer than 15 respondents, the curves are noisy. Treat Van Westendorp results as ordinal (what's the cheap range, what's the expensive range) rather than cardinal (what is the exact optimal price).

---

## Weighting competitive anchors

Competitor pricing is a buyer-side anchor: it tells you what mental reference point the buyer walks in with. It is not a target.

Three reasons not to copy competitor pricing:

1. **Their unit economics are not yours.** Competitors' CAC, gross margin, and investor pressure shape their pricing. You don't know their inputs.
2. **They priced the product they built, not yours.** If your product is materially better (or worse) in the buyer's eyes, same price = wrong price.
3. **Competitive pricing encodes assumptions about positioning.** Premium competitors price to signal premium. If you want to be the challenger, pricing at parity defeats the positioning.

Use competitive pricing to:

- Identify the range the buyer expects (price floor, price ceiling, median)
- Identify structural norms (annual billing, per-seat, free tier) the category has normalized
- Identify whether deviation is itself a differentiator (simpler pricing as a value prop; pay-as-you-go vs. everyone-else's-annual-contract)

---

## Reading WTP across ICP tiers

Tier A WTP is the one that matters for sustainable pricing. Tier B and beyond either upgrade toward your core ICP or they don't — pricing them as primary inputs produces a model optimized for the wrong customer.

Always report WTP signal separately by tier. If Tier A WTP ranges at $100–150/month and Tier B at $30–50/month, a single tier priced at $75/month fails both. A tiered strategy that segments the tiers to the respective WTP ranges often succeeds.

If Tier A responses are too few to have signal (< 3 respondents with explicit WTP data), say so in the analysis. Do not synthesize a number from nothing.

---

## The "hypothesis posture"

Sometimes the founder needs to run `pricing-strategist` before beta data exists. This is legitimate — pricing is often needed for Project 11 (pitch deck), and waiting for perfect data is its own failure mode.

When running in hypothesis posture:

- Every price-range number must be explicitly flagged as hypothesis, not validated
- Ranges should be wider (±30% instead of ±15%)
- A re-run trigger must be defined ("re-run after 5+ Tier-A WTP responses")
- The `evidence_posture` frontmatter field must be set to `hypothesis-only`

Do not let a hypothesis-posture output drift into treatment-as-validated. The frontmatter and the explicit flags are there to prevent this.

---

## Red flags that WTP signal is unreliable

- All responses come from users who received the product free and cite numbers without anchoring (self-serving overestimation)
- Responses concentrate in one tier and the other is absent
- Price anchors are round numbers without explanation (respondents reaching for a plausible answer, not a considered one)
- Respondents all cite the same competitor anchor (groupthink or anchoring bias from survey wording)
- Respondents with budget authority are absent; responses come from champions, not buyers

When you see these, note them in the output and weight the strategy recommendation toward conservatism (lower anchor prices, more tiered flexibility).
