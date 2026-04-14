# TAM / SAM / SOM Guide

A working reference for `pitch-deck-builder`. How to size a market honestly without inventing numbers.

The job is to produce TAM / SAM / SOM that a skeptical investor can stress-test and either accept or push back on with specific questions. The failure mode is a copied analyst number that collapses on the first "how did you calculate that?" question.

---

## 1. Definitions

**TAM (Total Addressable Market)** — total annual revenue opportunity if every potential buyer in the universe bought your product.

**SAM (Serviceable Addressable Market)** — annual revenue opportunity from buyers you can actually reach given your product's design, geography, language, compliance scope.

**SOM (Serviceable Obtainable Market)** — annual revenue opportunity you can realistically win in a stated timeframe (usually 3–5 years) given competition and capacity.

**Plain-language example** (hypothetical B2B SaaS for US dental offices):
- TAM: every dental office globally = 150,000 practices × $6,000/yr ACP = **$900M/yr global**
- SAM: US dental offices using an EHR that integrates = 65,000 practices × $6,000 = **$390M/yr US**
- SOM: realistic 3-year capture at 3% penetration = 1,950 practices × $6,000 = **$11.7M/yr by year 3**

Investors look at all three. SOM is the number that must be defensible because it's what your model relies on.

---

## 2. Bottoms-up methodology (primary method)

The default approach for early-stage. Derive numbers from the ICP, not from analyst reports.

**Formula:**

```
Market size = (count of target accounts) × (annual contract price) × (attach rate)
```

**Step 1: Define the unit.** What is one customer? An individual? A team? A company? A transaction? Be specific.

**Step 2: Count the target accounts.** Use the ICP definition from `icp.md`. If the ICP is "US dental practices with 2+ providers," find the count (Bureau of Labor Statistics, IBISWorld, Census Bureau). Cite the source.

**Step 3: Multiply by annual contract price.** Use `pricing-model.md`. If tiered, use a weighted average or mid-tier anchor.

**Step 4: Apply attach rate for SAM.** Not every account in the TAM is reachable. Estimate the fraction that are: right technology stack, right size, right geography. Be honest.

**Step 5: Apply capture rate for SOM.** In 3–5 years, what % of the SAM can you reasonably win? Base this on:
- Competitive intensity
- GTM capacity (team, capital)
- Sales cycle / time to close
- Reference comparables (how fast did a similar-stage company grow their customer count?)

**Worked example tied to a generic B2B ICP:**

ICP: US mid-market legal firms (10–50 attorneys) using cloud-based practice management.

- Count: ~28,000 firms (per IBISWorld / NALP reports — cite)
- ACP: $18,000/yr (derived from `pricing-model.md`, 3 tiers weighted)
- **TAM (US only):** 28,000 × $18,000 = $504M/yr
- Attach rate (firms already on cloud practice-management + ready to add workflow tool): 60%
- **SAM:** 16,800 × $18,000 = $302M/yr
- Realistic 5-year capture: 4%
- **SOM:** 672 × $18,000 = **$12M/yr ARR by year 5**

Every number cited. Investor can push back on any assumption; you can defend or concede each one.

---

## 3. Top-down sanity check (secondary method)

Top-down uses analyst reports (Gartner, Forrester, IDC, IBISWorld) to size the total market. Use it only as a **cross-check** against your bottoms-up number, never as the primary.

**Why top-down fails alone:**

- Analyst categories rarely match your actual ICP
- Analyst TAMs are often aggregated across geographies, product types, segments you can't serve
- "Our SOM is 1% of TAM" is not methodology — it's handwaving

**How to use top-down defensibly:**

1. Find the analyst category closest to your space
2. Cite the source (with date)
3. Explicitly narrow: "This $X category includes [segments]; we address [narrower subset] which we estimate at [%]"
4. Compare to your bottoms-up — if they're wildly different, figure out why before presenting

---

## 4. Assumption-explicit template

Every number should carry:

```
[Number] = [source / derivation]
  Assumption 1: [stated]
  Assumption 2: [stated]
  Confidence: Low | Medium | High
```

Example:

```
SAM: $302M/yr
  Derivation: 16,800 US mid-market legal firms × $18,000 ACP
  Source for count: IBISWorld Legal Services 2025 report (cite link)
  Source for ACP: our pricing-model.md, 3-tier weighted average
  Assumption 1: 60% of firms are on cloud practice-management (Clio Report 2024)
  Assumption 2: Our product integrates with their existing stack
  Confidence: Medium (count source is strong, attach rate is estimated)
```

If an assumption is fragile, say so. Investors appreciate calibrated confidence more than false precision.

---

## 5. Common failure modes

**"$100B TAM from Gartner."** Every investor has seen this a thousand times. Without bottoms-up support, it signals you haven't done the work.

**Mismatched ICP-to-TAM.** ICP is US SMB but TAM cites global market including enterprise. Read again: TAM must match the ICP you are actually selling to.

**Double-counting.** Customers who appear in TAM for two of your product lines, or a B2B2C TAM that counts both the businesses AND their end users.

**Currency mismatches.** Citing global TAM in USD when ICP is in Europe where pricing differs.

**Vanity SOM.** "In 10 years we'll capture 30% of the market." Not a SOM — that's a fantasy.

**Static TAM in a growing market.** If the market is growing 15%/yr, say so; static numbers undersell defensible stories.

**Ignoring competitive SOM drag.** If 3 well-funded competitors exist, your realistic capture is lower than if you're alone.

**Confusing signed ARR with TAM.** "Our TAM is $50M because that's what our pipeline says." Pipeline is not TAM.

---

## 6. When TAM is small

Not every company needs a $10B TAM. A well-defined $500M SOM can be better than a speculative $50B TAM.

**How to present a small-but-defensible TAM:**

- Lead with SOM: "We can build a $50M ARR business in this segment."
- Show adjacencies: "From this beachhead, the adjacent segments extend SAM to $1.5B."
- Be honest about the wedge: "This is a focused, high-margin, capital-efficient business. Not every investor is a fit; we're looking for ones who are."

Small TAMs filter out wrong-fit investors early, which is net-positive. Don't inflate to match expectations you can't defend in diligence.

---

## 7. Range presentation

A single number implies certainty you don't have. Use ranges with named assumptions.

**Pattern:**

- **Low case:** pessimistic assumptions (lower attach, lower ACP, slower growth)
- **Base case:** expected assumptions (your central estimate)
- **High case:** optimistic but still defensible (higher attach, higher ACP)

Example:

```
SOM range (year 5):
  Low: $6M (2% capture, $15K ACP)
  Base: $12M (4% capture, $18K ACP)
  High: $22M (6% capture, $22K ACP)
```

Present base in the deck, show range in appendix or on demand.

---

## 8. Checklist before finalizing the market slide

- TAM, SAM, SOM are each defined (not just "market")
- Every number traces to a source or derivation
- Bottoms-up method is primary; top-down is check-only
- ICP in `icp.md` matches the population counted in TAM
- Assumptions are stated explicitly
- Confidence level is calibrated (not all "High")
- SOM timeframe is stated (3-year, 5-year)
- Range presentation (low/base/high) is available even if only base is in the deck
- No "1% of $100B market" handwaving
- Numbers pass the "defend it for 10 minutes with a skeptical investor" test
