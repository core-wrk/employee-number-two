# Product Overview Template

Internal reference used by `prd-builder` for the compressed `global/context/product-overview.md` extract. This file is read by 6 downstream projects (05 outbound, 07 product development, 08 beta testing, 09 pricing, 11 fundraising, 12 financial modeling), so the schema is load-bearing.

## Structure

```yaml
---
schema_version: 1
generated_from: projects/06-product-management/outputs/product-requirements-document.md
last_updated: YYYY-MM-DD
stage: pre-alpha | alpha | beta | GA
---
```

## Section 1: Headline Value Proposition

**One sentence.** Not a paragraph. The format that works best:

> "[Product] helps [buyer] [outcome] by [distinctive mechanism]."

Failure mode: two-sentence paragraphs that couldn't bear to cut. Force the cut.

## Section 2: Target Buyer

Three sub-bullets:

- **Role:** Copied verbatim from `icp.md` primary persona role
- **Company shape:** Size + industry + stage (e.g., "100–500 person SaaS, post-Series A")
- **Buying trigger:** The moment the buyer starts looking (e.g., "new RVP joins and inherits flat ramp metrics")

Failure mode: three-paragraph buyer profiles. This is the overview — detail belongs in the PRD.

## Section 3: Core Capabilities

3–5 bullets. **Capability-level, not feature-level.**

- ✅ "Link CRM opportunities to ramp cohorts for attribution"
- ❌ "Has a ramp attribution dashboard with 12 report types"

Failure mode: drifting into feature lists. The overview is for strategy, not sales enablement.

## Section 4: Differentiation

2–3 bullets, each naming a specific competitor from `competitive-landscape.md`:

> "vs. [Competitor A]: [one-line delta describing what this product does that they don't]."

Failure mode: unfocused claims ("we're easier to use"). Force a named-competitor comparison.

## Section 5: Primary Use Cases

3–5 JTBDs from Section 4 of the PRD. Each as one sentence.

## Section 6: What This Product Is Not

2–3 bullets of explicit negative scope. These come from Section 5 (non-goals) of the PRD.

Failure mode: omitting this section. Negative scope is where downstream projects (especially outbound and pricing) anchor their messaging.

## Section 7: Pricing Posture

Shape only. One of: `free`, `paid`, `freemium`, `enterprise`, `TBD`. Numbers and tiers are Project 09's job — do not anticipate them here.

## Section 8: Current Stage

One of: `pre-alpha`, `alpha`, `beta`, `GA`. This is the signal outbound (Project 05) uses to decide whether to pitch design-partner deals vs. paid pilots.

## Section 9: Key Assumptions (Top 3 Unvalidated)

The 3 highest-stakes unvalidated assumptions from `outputs/assumption-tracker.md`. Format:

> 1. [Assumption text] — see `outputs/assumption-tracker.md` `A01`

**Must link by ID.** Downstream projects (especially Project 08 beta testing) use these IDs to route validation evidence back.

## Downstream Consumers

The following projects read this file. Changes to the schema must be coordinated:

| Project | What it uses |
|---|---|
| 05 outbound-sales | Role, capabilities, stage, differentiation for prospect messaging |
| 07 product-development | Capabilities, NFRs (via PRD link) for engineering scoping |
| 08 beta-and-user-testing | Stage, assumptions for beta recruitment and feedback routing |
| 09 pricing-and-packaging | Pricing posture, capabilities, use cases for pricing model design |
| 11 fundraising-prep | Value prop, differentiation, stage for pitch narrative |
| 12 financial-modeling | Buyer, pricing posture, use cases for revenue model |

## Anti-patterns

- Multi-paragraph sections that should be bullets
- Feature lists in Section 3 (capability-level only)
- Unnamed competitor comparisons in Section 4
- Skipping Section 6 (negative scope)
- Assumption text without ID pointers in Section 9