# Project 09 — Pricing & Packaging

## Purpose

Pricing is where every upstream project converges. The ICP tells you who is buying. The competitive landscape tells you what else they could buy instead. The product overview tells you what you are actually selling. Beta feedback tells you what they would pay for it. This project turns those inputs into a defensible pricing and packaging model — a strategy choice (per-seat, usage-based, tiered flat, hybrid, freemium, outcome-based), a set of tiers with explicit feature allocation, and anchor prices grounded in real willingness-to-pay signal.

By the end of this project you will have produced a project-scoped analysis of viable pricing strategies, a detailed packaging tier design, a finalized pricing model, and a distilled summary written to `global/context/pricing-model.md` that Projects 10 (legal), 11 (fundraising), and 12 (financial modeling) auto-load. The goal is not a perfect price — early pricing is almost always wrong — but a price that is defensible, consistent with value, and structured so that you can revise it without tearing up the packaging.

Pricing decisions made here are reversible but expensive to reverse. Packaging decisions — how features are allocated across tiers — are harder to reverse than prices. Treat the packaging work with more care than the absolute-number work.

## Prerequisites

Complete **Project 06** (product management — produces `product-overview.md`). You cannot price a product whose value proposition is not articulated.

**Project 01** (market research — produces `competitive-landscape.md` and `icp.md`) is required. Pricing without competitive anchors invents a market; pricing without ICP willingness-to-pay context prices the wrong customer.

**Project 08** (beta & user testing — produces `validated-insights.md`) is strongly recommended. The willingness-to-pay section in that file is the single most important input to `pricing-strategist`. If you run this project pre-beta, the skills will flag that you are pricing on hypothesis rather than evidence and will output a narrower recommendation with an explicit re-run trigger ("re-run after 5+ Tier-A WTP responses").

## Global Context Files

**Loads:** `competitive-landscape.md`, `icp.md`, `product-overview.md`, `validated-insights.md` (optional — soft-degrade if pre-beta), `founder-profile.md` (optional — for risk tolerance framing)

**Writes:** `pricing-model.md` — written by `packaging-designer` via the `context-writer` skill once the founder has approved the finalized model. This is a distilled summary (chosen strategy, tier names, value metric, anchor prices, upgrade triggers, last-reviewed date) that Projects 10, 11, and 12 read directly. Full strategy-options analysis and tier-design rationale stay project-scoped.

**Cross-project reads:**
- `projects/08-beta-and-user-testing/outputs/feedback-synthesis-reports/synthesis-*.md` — optional but high-value. If present, `pricing-strategist` reads the most recent synthesis for verbatim WTP quotes and objection patterns, not just the distilled summary.

## How This Project Works

Skills fall into two groups that map to the arc of a pricing decision:

1. **Explore strategy** — `pricing-strategist` surveys viable pricing models against your ICP, competitive benchmarks, and WTP signal, then produces a comparison of 2–3 strategies with explicit tradeoffs. The founder selects a lean direction at the end of this step. Strategy selection precedes tier design; designing tiers before choosing between per-seat and usage, for example, wastes the design work.
2. **Design packaging** — `packaging-designer` takes the selected strategy and designs 2–4 tiers: name, positioning, included features, value metric, anchor price, upgrade trigger. It produces both the full packaging rationale (project-scoped) and the finalized pricing model summary, then invokes `context-writer` to update `global/context/pricing-model.md`.

Both skills are conversational, ground every recommendation in `icp.md` and (if available) the synthesis reports, and show a preview before writing any file. Re-running is expected — as beta feedback matures and the product evolves, both the strategy choice and tier design should be revisited.

**Pricing is not a one-shot.** The model you ship today should be treated as v1 with an explicit review date. Both skills append a `last_reviewed` field to their outputs and surface a recommended re-run trigger (new cohort of WTP data, new competitor launch, major product change).

## Skills

| Skill | Description |
|---|---|
| `pricing-strategist` | Survey viable pricing strategies against ICP, competitive landscape, and WTP signal; produce a 2–3 option comparison with tradeoffs; help the founder select a direction |
| `packaging-designer` | Design 2–4 packaging tiers for the selected strategy; set anchor prices and upgrade triggers; finalize the pricing model; write distilled summary to `global/context/pricing-model.md` |

## Recommended Flow

**In order:**

1. **`pricing-strategist`** — first skill. Expect 45–75 minutes. Reads the three required context files plus `validated-insights.md` if present, surfaces 2–3 viable strategies with concrete tradeoffs tied to your ICP and WTP signal, and helps the founder select a direction. Output: `outputs/pricing-strategy-options.md` with a **Selected Direction** section at the end.
2. **`packaging-designer`** — second skill. Reads the selected direction and designs tiers. Produces `outputs/packaging-tiers.md` (full rationale) and `outputs/pricing-model-final.md` (the finalized model). On approval, invokes `context-writer` to write `global/context/pricing-model.md`.

**If pre-beta:** Run `pricing-strategist` with explicit "hypothesis-only" framing. The skill will output a narrower recommendation and an explicit re-run trigger. Defer `packaging-designer` until at least one beta synthesis exists, or run it with the explicit understanding that the tier allocation is a placeholder for Project 11 storytelling.

**On re-run:** If pricing already exists in `global/context/pricing-model.md` and you are revising, both skills read the existing model and explicitly call out what is changing and why. `context-writer` will show the diff.

If the strategy-options output reveals that the ICP and product-overview are inconsistent (e.g., an enterprise ICP with a self-serve product spec), the right move is to revisit Project 01 or Project 06 rather than trying to force-fit a pricing model. The skills will tell you when the gap is upstream.

## Outputs

All saved in `projects/09-pricing-and-packaging/outputs/`:

- `pricing-strategy-options.md` — 2–3 viable strategies, tradeoffs, competitive anchors, WTP grounding, recommended direction, selected direction (from `pricing-strategist`)
- `packaging-tiers.md` — Tier names, value metric, feature allocation, anchor prices, upgrade triggers, decoy analysis, tier-sprawl risk notes (from `packaging-designer`)
- `pricing-model-final.md` — The finalized model: chosen strategy, tier table, list prices, annual/monthly terms, trial/freemium rules, review date (from `packaging-designer`)

**Writes to `global/context/`:** `pricing-model.md` — distilled summary of the finalized model, written by `packaging-designer` via `context-writer`.

## Validation

This project is in a workable state when:

- `pricing-strategy-options.md` exists with at least 2 distinct strategies compared, each grounded in a cited competitive anchor and (if beta data exists) a cited WTP signal from `validated-insights.md`. A **Selected Direction** section names the chosen strategy with a one-paragraph rationale.
- `packaging-tiers.md` exists and defines 2–4 tiers. Each tier has: a name, a value metric, a feature list that differs meaningfully from adjacent tiers (no fake fencing), an anchor price, and an upgrade trigger.
- `pricing-model-final.md` exists and is internally consistent with `packaging-tiers.md`. Contains a `last_reviewed` date and a named re-run trigger.
- `global/context/pricing-model.md` exists and contains the distilled model with metadata block (source project, source skill, last updated).
- Tier count is between 2 and 4. More than 4 is almost always tier-sprawl; 1 is a flat product, which is fine but should be declared intentional.

A good Project 09 outcome is one where the founder can hand the pricing page copy to an engineer without ambiguity about what each tier includes, and can defend the anchor price to an investor by citing ICP WTP evidence. Pricing pulled from thin air — "I benchmarked against competitors and rounded" — produces a model that falls apart the first time a real prospect asks "why that price?"

**Note on scope:** This project does not implement billing (that is an engineering task in Project 07), does not provide legal or tax guidance on pricing (Project 10 surfaces the questions to ask a lawyer, but real guidance needs an actual lawyer), and does not build the financial model (Project 12 consumes `pricing-model.md` to do that). Keep this project focused on strategy, packaging, and anchor prices; let the downstream projects handle the rest.

---

## Don't See What You Need?

The skills in this project cover the most common tasks for this stage, but they are not exhaustive.
If you need a capability that isn't covered, Claude Code includes two native built-in tools for this:

- **Skill creator** — Claude Code's built-in skill authoring tool. Use it to create a new custom skill
  and save it in this project's `.claude/skills/` directory (project-only) or in the root
  `.claude/skills/` directory (available across all projects).
- **MCP builder** — Claude Code's built-in MCP server builder. Use it if you want to connect
  Claude Code to an external tool or API. Most relevant here when you want to integrate a billing
  platform (Stripe, Paddle, Lago) or a pricing research tool (ProfitWell / Paddle Studies).

Custom skills and MCP servers you create will live in your private fork and will not affect
the upstream repo. If you build something you think would benefit other founders, see CONTRIBUTING.md
for how to suggest it.
