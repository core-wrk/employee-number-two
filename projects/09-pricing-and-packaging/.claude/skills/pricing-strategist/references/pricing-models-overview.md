# Pricing Models Overview

Reference for the `pricing-strategist` skill. Covers the main pricing strategies a SaaS / software / AI-first startup might consider, when each fits, when it fails, and what revenue mechanics it implies.

This is not exhaustive — it is the working set that covers ~95% of early-stage pricing decisions. If the founder's business model falls outside these (marketplace take rate, transactional, hardware-attached, ad-supported), surface that and help the founder reason from first principles.

---

## Per-Seat (Per-User)

**How it works:** Customer pays a fixed fee per user per month (or year). Total bill scales with headcount using the product.

**When it fits:**
- Collaborative or workflow tools where more users = more value (Slack, Notion, Figma)
- ICP has a clear "team" or "department" purchase pattern
- Buyer can easily count and predict users
- Each user derives individual value (not just a shared resource)

**When it fails:**
- One-user-for-a-team products where a single account serves many humans (ticket dashboards read-only by execs)
- Products used intermittently by many people (annual-use compliance tools)
- Value is produced by the product's output, not by user activity (report generators, AI agents acting on behalf of a team)
- ICP buyers game the model by sharing credentials

**Revenue mechanics:** Expansion driven by seat count. Predictable. Makes land-and-expand natural. Churn of seats can be silent.

**Buying friction:** Low for small teams, rises with enterprise procurement (SSO, user provisioning, seat reconciliation).

**Failure mode to avoid:** Pricing per seat when the actual value metric is output volume. Customer resents paying for seats that don't use it; you resent leaving money on the table when a single seat processes 10x the volume.

---

## Usage-Based (Consumption)

**How it works:** Customer pays per unit of consumption — API calls, documents processed, tokens, minutes, GB stored.

**When it fits:**
- Infrastructure, AI, or workflow tools where value scales with use
- ICP has highly variable consumption (some customers will use 10x more than others)
- You can meter accurately without customer dispute
- Customer perceives unit of consumption as meaningful (per-document is meaningful; per-API-call may not be)

**When it fails:**
- ICP buyers cannot predict their bill (procurement hates this)
- Metering is lossy, disputed, or expensive to instrument
- Value is front-loaded: customer gets most of the value in the first 10 uses, then tapers
- Unit price is too small to feel meaningful (per-token pricing below $0.01 feels abstract; bundling into larger units helps)

**Revenue mechanics:** Expansion tracks product adoption directly. Highest value-alignment of any model. Hardest to forecast — both for you and for the customer. Churn can be silent (bill drops; you don't notice until it's zero).

**Buying friction:** High if budget-authority is a blocker. Often softened by adding committed minimums or credits.

**Failure mode to avoid:** Usage-based pricing at seed stage with no credit system. Customers can't predict spend, procurement rejects, you lose deals you could have won.

---

## Tiered Flat

**How it works:** 2–4 named tiers (e.g., Starter, Professional, Business), each a fixed monthly or annual fee, each including a bundle of features and a usage cap.

**When it fits:**
- Product has clearly segmented buyer personas with different needs
- Self-serve or low-touch sales motion
- Features can be meaningfully grouped (one tier can be the "team" tier, another the "org" tier)
- ICP prefers predictable billing

**When it fails:**
- All customers actually want the same thing — tier proliferation creates decision paralysis and fake fencing
- Customer value is highly variable within a tier (a "Business" tier customer doing 10x the volume of another Business customer)
- Tier count creeps past 4 — almost always a signal that the product is fencing arbitrarily

**Revenue mechanics:** Expansion via tier upgrade. Predictable. Pricing page is easy to read. Feature fencing risks resentment when features feel arbitrarily withheld.

**Buying friction:** Low. Pick a tier, pay, done.

**Failure mode to avoid:** Four-tier Good/Better/Best/Enterprise where Enterprise is "contact us" and Business vs. Professional is differentiated by a single feature nobody cares about.

---

## Hybrid (Seat + Usage, or Tier + Usage)

**How it works:** Fixed platform fee plus variable usage component. Or: tiered flat with included usage allowance, overages billed per unit.

**When it fits:**
- Product has both a "platform" value (availability, integrations, workflow) and a "consumption" value (throughput, AI calls, storage)
- ICP wants predictable baseline spend with expansion room
- Competitive landscape has normalized hybrid (AI infrastructure, observability, communications APIs)

**When it fails:**
- Complexity confuses buyers — if you cannot explain it on a pricing page in 3 lines, it will cost deals
- Meter implementation is non-trivial; most seed-stage companies can't instrument it reliably

**Revenue mechanics:** Best of both: predictable base + consumption upside. Most complex to run.

**Buying friction:** Medium. Procurement accepts the base; consumption requires monitoring and trust.

**Failure mode to avoid:** Layering hybrid on top of a product whose usage patterns aren't yet known. You end up tuning meters against a customer base that's too small to signal.

---

## Freemium

**How it works:** A free tier (permanent, not trial) with meaningful but constrained functionality. Paid tiers unlock features, scale, or collaboration.

**When it fits:**
- Product has a genuine individual-use case that creates value at zero cost
- The free tier drives viral or network effects (invites, shared output, public artifacts)
- Unit economics of the free tier are defensible (low marginal cost per free user)
- Conversion path from free → paid is clear and achievable

**When it fails:**
- Free tier cannibalizes paid (users never hit the upgrade trigger)
- Marginal cost of free tier is high (AI inference, LLM costs, support)
- ICP doesn't exist at individual level — the actual buyer is procurement, who doesn't care about free
- Founder uses freemium as an excuse not to decide pricing

**Revenue mechanics:** Driven by conversion rate from free → paid. Most companies have worse conversion than they expect (2–5% is common; >10% is a unicorn).

**Buying friction:** Zero for free. Conversion friction is the real metric.

**Failure mode to avoid:** Freemium as default choice for an enterprise product. Your buyer isn't the free user; they're a procurement team who ignores free.

---

## Outcome-Based (Value-Based)

**How it works:** Customer pays a percentage of the value the product delivers — revenue generated, cost saved, hours saved, workflow completed.

**When it fits:**
- Value is clearly measurable (closed-won revenue, verified cost savings)
- ICP is willing to share their outcome data
- Outcome attribution is defensible (you can prove your product drove the result)
- Deal sizes are large enough to justify the measurement overhead

**When it fails:**
- Attribution is disputed
- Outcomes are lumpy and hard to measure in short cycles
- ICP refuses to share the data needed to price
- Legal complexity around performance-based contracts

**Revenue mechanics:** Aligns incentives perfectly. Scales with customer success. Hard to forecast; long negotiation cycles.

**Buying friction:** High at contracting; low at signing (customer only pays on success).

**Failure mode to avoid:** Outcome-based as a seed-stage gimmick. Without the attribution infrastructure and legal support, it creates more dispute than revenue.

---

## How to choose between these

Do not start from the menu above and ask "which model do I like?" Start from:

1. **What is the natural value metric of the product?** Seats? Documents? Outcomes? Usage? This narrows the viable set.
2. **What does the ICP's buying process tolerate?** Procurement-heavy buyers reject unpredictable bills. Individual buyers reject complexity.
3. **What does the competitive landscape train the buyer to expect?** Deviation from category norms is a tax you pay unless deviation itself is a differentiator.
4. **What can you instrument reliably right now?** Usage pricing without a meter is a theoretical exercise.

The right strategy is usually obvious once you have answered those four. When it is not obvious, the answer is often "tiered flat" as a v1, revisited after 6–12 months of real revenue.
