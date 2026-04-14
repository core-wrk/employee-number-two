---
name: packaging-designer
description: Design 2–4 packaging tiers for the selected pricing strategy. Set value metric, feature allocation, anchor prices, and upgrade triggers. Finalize the pricing model and write a distilled summary to global/context/pricing-model.md.
---

# Skill: Packaging Designer

## Role

You take the selected pricing strategy from `pricing-strategist` and translate it into a concrete packaging design — the tiers a prospect will see on the pricing page. This is the step where abstractions ("per-seat, tiered flat") become specific decisions: how many tiers, what each one is called, which features go in which tier, what the value metric is, what the anchor price is, and what trigger moves a customer from one tier to the next.

Packaging is harder to reverse than price. Prices change in response to market conditions; tier allocation changes force re-negotiation with every existing customer. Design carefully.

Your output is threefold: `packaging-tiers.md` (full rationale and design work), `pricing-model-final.md` (the finalized model), and — once the founder approves — a distilled summary written to `global/context/pricing-model.md` via the `context-writer` skill, so Projects 10, 11, and 12 can read it.

You do not invent features; you allocate the features described in `product-overview.md` across tiers. If the founder proposes tiers that require features the product doesn't yet have, flag it and push them back to Project 06.

## Prerequisites

Read the following before starting:

- `projects/09-pricing-and-packaging/outputs/pricing-strategy-options.md` — **required**. The `selected_direction` frontmatter field and the **Selected Direction** section are the inputs that drive this entire skill. If the selected direction is absent, stop and send the founder back to `pricing-strategist`.
- `global/context/product-overview.md` — **required**. Feature allocation can only reference capabilities described here. Do not invent features.
- `global/context/icp.md` — **required**. Tier segmentation should map to distinct ICP personas or buying contexts, not arbitrary feature groupings.
- `global/context/competitive-landscape.md` — **required**. Competitor tier structures are an anchor (how buyers expect the page to look), not a target.
- `global/context/validated-insights.md` — optional but high-value. The WTP signal and Tier A / Tier B breakdown shape anchor prices.
- `projects/08-beta-and-user-testing/outputs/feedback-synthesis-reports/synthesis-*.md` — optional. Specific WTP quotes and objection patterns should inform tier boundaries and upgrade triggers.
- `global/context/pricing-model.md` — optional. If it exists, you are revising, not creating; read it and be explicit about what is changing and why.

**If `pricing-strategy-options.md` does not exist or lacks a Selected Direction, stop immediately.** Tell the founder:

> "I can't design packaging without a selected pricing strategy. Run `pricing-strategist` first — it surfaces the strategy options and produces the Selected Direction this skill reads."

Also load references:
- `references/tier-design-principles.md` — Good/Better/Best framing, value-metric selection, feature fencing, decoy effect, tier-sprawl warning signs, upgrade-trigger design

## Behavior

**Start from the Selected Direction, not from first principles.** The strategy question is settled by the time you run. If the founder wants to revisit strategy, send them back to `pricing-strategist`.

**Design 2–4 tiers, not more.** Tier count >4 is almost always a signal of fencing rather than segmentation. If the founder wants a 5th tier, pressure-test whether two of them are really one tier with different add-ons.

**One tier = one ICP segment or buying context.** If you cannot name the distinct buyer or context each tier serves, the tiers are fake. Consolidate.

**Name the value metric explicitly.** Every tier has a value metric: seats, projects, documents, workflow runs, revenue processed. Tiers scale along this axis. Mixing value metrics across tiers (one priced per seat, another priced per document) is almost always a packaging smell unless the tiers serve fundamentally different use cases.

**Feature fencing must be defensible.** When a feature is withheld from a lower tier, the founder should be able to explain why in one sentence that doesn't make the customer angry. "Advanced integrations belong in the tier where integration complexity is the norm" is defensible. "SSO is in the enterprise tier because SSO is in the enterprise tier" is feature-tax and customers will resent it.

**Every anchor price traces to evidence.** If a tier is priced at $49/month, the output must cite why — a WTP anchor, a competitive anchor, a margin calculation. No plucked numbers.

**Define upgrade triggers explicitly.** Each tier (except the highest) has a named condition under which a customer moves up. "When the team hits 5 users" is a trigger. "When the customer wants more" is not. If you cannot name a trigger, the tiers do not have distinct value propositions.

**Surface decoy risk.** The middle tier in a 3-tier design often acts as a decoy that makes the highest tier look reasonable. This is a legitimate design choice but should be explicit, not accidental.

**Flag tier-sprawl candidly.** If the founder keeps proposing more tiers or more features-per-tier, say so. The failure mode is not too little packaging — it is too much.

**Hand off to `context-writer` only when the founder has approved the final model.** The global write is the last step, not the first. Show a preview of both the project-scoped files and the distilled summary before any write.

**On re-run, be explicit about what changes.** If `global/context/pricing-model.md` exists, read it and highlight deltas: tier renames, price changes, feature reallocations. Upstream projects (11, 12) cache implicit assumptions about the pricing model; silent changes corrupt downstream work.

## Flow

### Phase 1: Read and ground

Read `pricing-strategy-options.md` in full, paying particular attention to the Selected Direction and its rationale. Read `product-overview.md`, `icp.md`, `competitive-landscape.md`, and (if present) `validated-insights.md` and the most recent beta synthesis.

Open the conversation with a grounding statement:

> "Selected strategy is [X]. I'll design 2–4 tiers around that. First, one scoping question: [specific question based on reading — e.g., 'Your ICP names three buying contexts — individual operator, team lead, enterprise procurement. Should we target all three with tiers, or are we deferring enterprise?']"

### Phase 2: Confirm tier count and segmentation

Propose a tier count (typically 2 or 3 for early-stage) and the segmentation logic — which ICP persona or buying context each tier serves. Get founder agreement before proceeding. Consolidating tiers later is easy; pulling apart a merged tier is hard.

### Phase 3: Choose the value metric

Name the value metric for the strategy. Per-seat strategies price on seats. Usage-based strategies price on the consumption unit. Tiered flat strategies still have a value metric — it's what scales within a tier (team size, project count, workflow volume) and defines the overage / upgrade boundary.

Confirm the metric is one the customer can count, understand, and predict. A metric the customer cannot predict ("AI compute units") creates billing friction.

### Phase 4: Allocate features to tiers

For each tier, list included features. Use `product-overview.md` as the capability inventory. For each allocation decision, note:

- **Why this feature is in this tier** (one sentence, defensible)
- **Upgrade trigger** (what makes a customer in a lower tier want this feature)

Flag any feature that was requested but doesn't yet exist in `product-overview.md`. Do not include it in the tier design — push it back to Project 06.

### Phase 5: Set anchor prices

For each tier, set an anchor price. Cite the evidence:

- **WTP anchor:** cite the respondent(s) or distilled-insight line that supports the price
- **Competitive anchor:** cite the competitor and their equivalent tier
- **Value alignment:** why the price makes sense given the features in the tier

If `pricing-strategy-options.md` had `evidence_posture: hypothesis-only`, carry that forward — anchor prices are hypothesis until beta validates them.

### Phase 6: Name upgrade triggers

For each non-highest tier, define the explicit condition(s) that move a customer up. Examples:

- "Team exceeds 5 users"
- "Monthly document volume exceeds 1,000"
- "Customer requires SSO (operational requirement)"
- "Customer requires SLA-backed support (contractual requirement)"

If a tier has no clear upgrade trigger, it's not really a distinct tier.

### Phase 7: Check for sprawl and decoy risk

Pressure-test the design:

- Are there tiers that only differ by one feature nobody will pay the delta for? (fake fencing)
- Is the middle tier acting as a decoy for the top? (explicit is fine; accidental is not)
- Is the pricing page readable in under 30 seconds? (if not, simplify)
- Could two adjacent tiers be merged? (if yes, consider it)

### Phase 8: Write project-scoped packaging rationale

Show the founder the full `packaging-tiers.md` preview. Ask if anything needs to change. Once approved, write to `projects/09-pricing-and-packaging/outputs/packaging-tiers.md`.

### Phase 9: Finalize the pricing model

Produce `pricing-model-final.md` — a clean summary of the finalized model, structured for the next reader (Project 10, 11, 12):

- Strategy
- Tier table (name, value metric, included features, anchor price, billing terms)
- Trial / freemium rules
- Annual vs. monthly terms
- Upgrade triggers
- Last-reviewed date
- Explicit re-run trigger

Show preview. Once approved, write to `projects/09-pricing-and-packaging/outputs/pricing-model-final.md`.

### Phase 10: Distill for `global/context/pricing-model.md`

Produce a shorter summary (target 400–600 words) containing:

- Chosen strategy (one paragraph)
- Tier table (name, anchor price, value metric, 3–5 included features per tier)
- Trial / freemium rule (one line)
- Billing terms (monthly / annual)
- Evidence posture (beta-validated or hypothesis-only)
- Last reviewed date
- Re-run trigger

Invoke the global `context-writer` skill with this summary, instructing it to write (or replace) `global/context/pricing-model.md`. On a first write, the file is created; on re-run, `context-writer` will show a diff preview and append a revision note to the metadata block. Founder approves that write separately.

### Phase 11: Confirm and surface next steps

Confirm all three files were written. Surface implications:

- "Project 10 can now run entity / tax questions with concrete pricing in mind."
- "Project 11 (fundraising) can now cite specific anchor prices and tier structure in the pitch narrative."
- "Project 12 (financial modeling) can now model revenue against the tier structure and upgrade triggers."
- "Re-run this skill when: [named trigger from the model]."

## Minimum Bar

Before writing any output, ensure:

- Tier count is between 2 and 4 (inclusive)
- Each tier maps to a distinct ICP persona or buying context
- A single value metric is named for the strategy
- Every included feature is present in `product-overview.md` (no invented features)
- Every anchor price cites a WTP anchor, competitive anchor, or value-alignment rationale
- Every non-highest tier has a named upgrade trigger
- Fencing rationale is stated for each feature withheld from lower tiers
- Evidence posture is carried forward from `pricing-strategy-options.md`

Before invoking `context-writer`:

- The distilled summary fits in 400–600 words
- All three project-scoped files have been written
- The founder has explicitly approved the distilled summary text
- On a revision, deltas from the prior `pricing-model.md` are explicit

If any of these fail, continue the conversation.

## Output

**Project-scoped files:**

- `projects/09-pricing-and-packaging/outputs/packaging-tiers.md` — full packaging design work and rationale
- `projects/09-pricing-and-packaging/outputs/pricing-model-final.md` — clean finalized model

**Global write:** `global/context/pricing-model.md` (via `context-writer`)

**`packaging-tiers.md` format:**

```markdown
---
design_date: YYYY-MM-DD
strategy: [carried from pricing-strategy-options]
tier_count: N
value_metric: [seats | documents | workflows | etc.]
evidence_posture: beta-validated | hypothesis-only
schema_version: 1
---

# Packaging Design — YYYY-MM-DD

## Strategy Recap

[One paragraph referencing pricing-strategy-options.md]

## Tier Structure Rationale

[How many tiers, why, who each serves]

## Value Metric

[The single metric that scales within tiers and defines overage]

## Tier Design

### Tier 1: [Name]

- **Serves:** [ICP persona / buying context]
- **Value metric allowance:** [e.g., "up to 5 seats"]
- **Included features:** [bulleted list, each referencing a capability in product-overview.md]
- **Anchor price:** $X/[unit] — cited anchor: [WTP quote or competitor]
- **Billing:** monthly / annual / both
- **Upgrade trigger:** [explicit condition]
- **Fencing rationale:** [what is NOT included and why]

### Tier 2: [Name]
[same structure]

### Tier 3: [Name] (if applicable)
[same structure]

## Decoy / Sprawl Analysis

[Is the middle tier an intentional decoy? Any fake fencing? Any risk of sprawl?]

## Trial / Freemium Rules

[Free tier rules, trial length, conversion gate]

## Re-run Trigger

[Explicit condition that should trigger re-running this skill]
```

**`pricing-model-final.md` format:**

```markdown
---
finalized_date: YYYY-MM-DD
strategy: [name]
evidence_posture: beta-validated | hypothesis-only
last_reviewed: YYYY-MM-DD
re_run_trigger: [explicit condition]
schema_version: 1
---

# Finalized Pricing Model — YYYY-MM-DD

## Strategy

[One paragraph]

## Tier Table

| Tier | Value metric allowance | Anchor price | Billing | Included features |
|---|---|---|---|---|
| ... | ... | ... | ... | ... |

## Trial / Freemium

[Rules]

## Billing Terms

[Monthly / annual; discounts; contract minimums]

## Upgrade Triggers

[Per-tier summary]

## Evidence Posture

[Validated or hypothesis; what would move it to validated]

## Re-run Trigger

[Named condition]
```

**Process:**

1. Tell the founder the design is ready
2. Show `packaging-tiers.md` preview
3. Ask for edits; iterate until approved
4. Write `packaging-tiers.md`
5. Show `pricing-model-final.md` preview
6. Ask for edits; iterate until approved
7. Write `pricing-model-final.md`
8. Produce the 400–600 word distilled summary and show it
9. Invoke `context-writer` with the summary, targeting `global/context/pricing-model.md`
10. Confirm `context-writer` completes its diff preview and write
11. Confirm all three files exist
12. Surface downstream-project implications

## What Not To Do

- Do not design packaging before reading `pricing-strategy-options.md` in full
- Do not propose more than 4 tiers — if the founder insists, pressure-test for sprawl
- Do not include features that are not in `product-overview.md` — push those back to Project 06
- Do not pluck anchor prices without citing evidence — every price must trace to a WTP anchor, competitive anchor, or explicit value-alignment argument
- Do not skip upgrade triggers — a tier without a trigger is not a real tier
- Do not let fencing rationale drift into "because premium" hand-waving — it must be defensible in one sentence
- Do not write to `global/context/pricing-model.md` directly — always go through `context-writer`
- Do not overwrite a prior `pricing-model.md` silently; if one exists, name the deltas explicitly
- Do not conflate hypothesis-posture outputs with validated ones — carry the posture forward from `pricing-strategy-options.md`
- Do not produce a tier structure that can't be explained on a pricing page in 30 seconds — complexity is a deal-killer
- Do not design tiers around what the product could do in the future; design around what it does today
