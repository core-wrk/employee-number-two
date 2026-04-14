# Tier Design Principles

Reference for the `packaging-designer` skill. Covers the Good/Better/Best framing, value metrics, feature fencing, decoy effect, tier-sprawl warning signs, and upgrade-trigger design.

---

## Good / Better / Best

The three-tier pattern is the default for a reason: it gives the buyer three choices, which is enough to signal that you've thought about pricing without forcing a decision across five or six options.

- **Good (lowest paid tier):** The entry point. Serves the least-committed buyer. Priced to remove friction at first purchase. Includes enough to be useful alone; excludes enough to create a clear upgrade path.
- **Better (middle tier):** The target tier — where you want most customers to land. Priced to look reasonable against both the Good and Best anchors. Includes the features that define "real" use of the product.
- **Best (highest tier):** Anchors the high end. Most pricing pages expect a Best tier that is visibly more expensive — it makes Better look like the smart choice (decoy effect). Best includes features that genuinely matter to a smaller buyer segment (enterprise, high-volume, compliance-regulated).

**Two-tier variant:** Good / Best, no middle. Works when the ICP is bimodal (individual users vs. teams; small businesses vs. enterprise) and a middle tier would be artificial.

**Four-tier variant:** Add an Enterprise tier ("contact us") on top of Good/Better/Best. Works when enterprise deals require custom contracting, SLAs, or legal terms. Do not use four tiers to split Better into Better-lite and Better-pro; that's sprawl.

**Never more than four.** If you think you need five, you are either splitting one tier or stacking add-ons that should be sold separately.

---

## Value metrics

Every tier has a **value metric** — the unit the customer buys more of as they grow. Within a tier, the value metric scales up to an allowance; above the allowance, the customer upgrades (or pays overage).

Common value metrics:

- **Seats / users:** Collaborative products.
- **Projects / workspaces:** Products organized around a unit of work (design tools, CI systems).
- **Documents / records / objects processed:** Content tools, CRMs, data pipelines.
- **Workflow runs / API calls / jobs:** Automation, AI, integration platforms.
- **Revenue / volume processed:** Billing, payments, commerce tools.
- **Data stored / compute used:** Infrastructure.

Criteria for a good value metric:

1. **Customer can count it.** They should be able to predict their bill without a spreadsheet.
2. **It correlates with value.** Customers using more of the metric are getting more value (not just more cost).
3. **It scales naturally as the customer grows.** You don't want to cap it prematurely.
4. **It's meterable without disputes.** Both sides can see the same number.

**Do not mix value metrics across tiers** unless the tiers serve genuinely different use cases. A product priced per-seat in the Team tier and per-document in the Business tier will confuse every prospect who tries to map one to the other.

---

## Feature fencing

Feature fencing is withholding a feature from lower tiers to motivate upgrades. Done well, it's invisible to the customer who doesn't need the feature. Done poorly, it feels punitive and generates churn risk.

**Defensible fencing:**
- Features that fundamentally serve a different buyer context ("Advanced audit logs" — only compliance-regulated customers need this)
- Features that incur real marginal cost on your side ("Dedicated support channel" — costs you money per customer, fair to gate)
- Features that scale with customer size ("Team-wide admin controls" — only meaningful at team size)

**Indefensible fencing:**
- SSO in the enterprise tier when your ICP includes mid-market teams (SSO has become table stakes for anyone buying software; gating it is perceived as extortion)
- Trivial features gated purely to force upgrades ("CSV export in Pro tier")
- Features gated by number when the number is arbitrarily low ("up to 3 integrations in Starter")

**The sso-as-enterprise-tax problem.** The "SSO tax" — gating SSO to enterprise tier — is widely criticized and increasingly rejected by sophisticated buyers. If your ICP includes any security-conscious buyers, think carefully before gating SSO.

---

## The decoy effect

A three-tier design almost always uses the middle tier as a "decoy" — the tier that makes the Best tier look reasonable by being visibly cheaper. Or alternatively, uses the Best tier as a decoy to make Better look like the smart choice.

**Example:**
- Starter: $9/mo
- Pro: $49/mo ← you want most customers here
- Business: $199/mo ← decoy that makes Pro look like a bargain

The decoy effect is real and widely documented in pricing research. Acknowledging it and designing for it is legitimate. Accidentally creating a decoy through tier math (where Best ends up being obviously overpriced) is not — it will cost the Best tier deals from customers who would have paid it if it had been priced more carefully.

**Make the decoy explicit in the rationale.** If the middle tier is the target and the top tier is the anchor, say so. The founder should understand the pricing psychology, not stumble into it.

---

## Tier-sprawl warning signs

Tier sprawl is the failure mode of adding tiers, features, add-ons, and options over time until the pricing page is unreadable. Signs:

- **Five or more tiers.** Rarely justified.
- **Tiers differentiated by one or two minor features.** Likely fake tiers.
- **Heavy use of "contact us."** If multiple tiers require a conversation to price, you have a sales process, not a pricing page.
- **Overlapping value metrics.** One tier priced per seat, another per document.
- **Add-ons proliferating at the bottom of the page.** Each add-on is a negotiation seed; prospects can't decide.
- **Long feature comparison tables.** If the table has more than 20 rows, the customer stopped reading at row 8.

Simplicity is a feature. Most customers prefer a clear three-tier page with concise features over a comprehensive one with thirty feature rows.

---

## Upgrade triggers

An upgrade trigger is the explicit condition under which a customer in a lower tier hits the boundary and moves up. Good triggers are:

1. **Observable.** The customer and the system both know when it's triggered (e.g., seat count, usage volume).
2. **Tied to growth.** The trigger fires when the customer is succeeding with the product — this is expansion, not squeeze.
3. **Unambiguous.** No judgment calls ("when the customer wants more features" is not a trigger).

**Typical triggers:**
- Team size crosses a threshold (5, 10, 50 users)
- Usage allowance hit (documents, workflow runs, storage)
- Operational requirement surfaces (SSO required by IT, SLA required by procurement)
- Advanced feature becomes load-bearing (custom integrations, audit logs, dedicated support)

**Every non-highest tier has a trigger.** If you cannot name the trigger that moves a customer from Tier 2 to Tier 3, then Tier 2 and Tier 3 do not have distinct value propositions and should be merged.

---

## Two special cases

**Enterprise tier ("contact us").** Legitimate when deals require custom contracting, SLAs, legal terms, or genuinely different pricing structures (e.g., annual commit, volume discounts). Not legitimate as a way to avoid publishing a price — if every customer asking for "Enterprise" gets the same quote, just publish it.

**Freemium tier.** Not a paid tier; it's a marketing mechanism. Rules for a free tier:
- Set limits that let the free user get real value (otherwise they bounce before converting)
- Set limits that naturally cap at individual use (team features are paid)
- Protect unit economics — if every free user costs you real money (LLM inference, storage), bound the exposure
- Define an upgrade trigger: team invites, hitting a usage cap, wanting a specific feature

---

## Revisiting tier design

Pricing changes after launch happen in two forms:

1. **Price tuning.** Changing numbers within the existing tier structure. Low-risk, expected. Grandfather existing customers or give them a grace period.
2. **Repackaging.** Changing the tier structure — renaming tiers, reallocating features, adding or removing tiers. High-risk. Every existing customer must be mapped to the new structure; some will see feature removal and churn. Do this deliberately, not reactively.

Early-stage startups should expect to tune prices and to repackage at least once within the first 12–18 months. The design produced here is v1; build it so v2 doesn't require tearing everything up.
