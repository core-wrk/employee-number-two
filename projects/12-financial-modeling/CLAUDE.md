# Project 12 — Financial Modeling

## Purpose

Build a dynamic, markdown-based financial model the founder can translate into a spreadsheet (or hand to a finance contractor). Model revenue scenarios, cost structure, unit economics, a hiring plan, and runway — plus an investor-facing metrics summary.

The goal is not a polished CFO-grade Excel workbook. The goal is a decision tool the founder can defend: every number either traces to a source document, to a founder-supplied assumption, or is flagged as illustrative. A model that is directionally honest and assumption-transparent beats a precise-looking model built on invented inputs.

This is the terminal project in the workspace. It consumes upstream context and produces project-scoped outputs; it does not write back to global context.

## Prerequisites

**Project 09** (pricing and packaging — produces `pricing-model.md`) is required. Revenue modeling without a pricing structure is guesswork.

**Project 06** (product management — produces `product-overview.md`) is required. The hiring roadmap maps to product milestones; cost of delivery references product scope.

**Project 10** (legal and company formation — produces `company-profile.md`) is required. Entity structure affects tax, founder comp assumptions, and investor-facing cap-table framing.

**Project 11** (fundraising prep — produces `investor-prospect-list.md`) is recommended. When modeling dilution and ask size, ticket ranges from the prospect list make the model concrete.

**Project 01** (ICP) is recommended. Revenue scenarios improve when new-logo volume is grounded in a defined ICP rather than a blended average.

## Global Context Files

**Loads:** `pricing-model.md`, `product-overview.md`, `company-profile.md`

**May reference (project-scoped):** `projects/11-fundraising-prep/outputs/investor-prospect-list.md`

**Writes to global:** none. Project 12 is terminal — all outputs stay project-scoped.

## How This Project Works

Skills fall into four sequential arcs:

1. **Revenue** — `revenue-modeler` builds bear / base / bull ARR trajectories from the pricing tiers, conversion assumptions, and churn. Every assumption is flagged with source: pricing doc, founder input, or illustrative default.

2. **Hiring** — `hiring-roadmap-builder` maps hires to product and revenue milestones, computes fully-loaded cost, and lays out quarterly hiring cadence. This feeds cost structure.

3. **Unit economics** — `unit-economics-builder` computes CAC, LTV, payback, and gross margin. At pre-seed / seed stage these are sketches, not measurements. The skill frames them honestly and flags which inputs are real and which are modeled.

4. **Scenarios** — `scenario-planner` synthesizes revenue + costs + hiring into full P&L-style runway scenarios (conservative / base / aggressive) and produces the investor-facing metrics summary.

All skills refuse to fabricate financials silently. If an input is missing and cannot be derived, the skill either asks the founder or flags the output as illustrative with an explicit `assumption_source` marker.

## Skills

| Skill | Description |
|---|---|
| `revenue-modeler` | Build SaaS revenue model with bear / base / bull scenarios grounded in pricing tiers; ARR build = new logos × ACV + expansion − churn |
| `hiring-roadmap-builder` | Map hires to product/revenue milestones; fully-loaded cost; quarterly hiring cadence and cumulative run-rate |
| `unit-economics-builder` | Compute CAC, LTV, LTV/CAC, gross margin, payback; frame honestly for stage; flag modeled vs measured inputs |
| `scenario-planner` | Combine revenue, costs, hiring into runway scenarios; produce investor metrics summary; sensitivity table on top 3 levers |

## Recommended Flow

**In order:**

1. **`revenue-modeler`** — first. 45–90 minutes. Requires `pricing-model.md`. Produces `outputs/revenue-model.md` with three scenarios, explicit assumptions, and a `revenue_model_confidence` frontmatter field.

2. **`hiring-roadmap-builder`** — second. Can run in parallel with unit economics if time-constrained, but hiring-first is cleaner because it feeds costs into unit economics (salaries flow through gross margin) and into scenarios. Produces `outputs/hiring-roadmap.md` and, as a byproduct, `outputs/cost-structure.md` (salaries + non-headcount opex + tools + COGS).

3. **`unit-economics-builder`** — third. Requires revenue model and cost structure. Produces `outputs/unit-economics.md` with CAC, LTV, payback, gross margin. Honest staging: pre-revenue sees modeled unit economics explicitly flagged.

4. **`scenario-planner`** — last. Synthesizes the three upstream outputs. Produces `outputs/runway-scenarios.md` and `outputs/investor-metrics-summary.md`.

**Re-run triggers per skill:** close of a new customer (revenue), material hire or role change (hiring), pricing change (all four), round close or new cash event (scenarios).

## Outputs

All saved in `projects/12-financial-modeling/outputs/`:

- `revenue-model.md` — three scenarios (bear / base / bull), ARR build by month or quarter, explicit assumptions table, confidence rating (from `revenue-modeler`)
- `cost-structure.md` — headcount cost, tools/SaaS, infrastructure/COGS, G&A, per-category monthly run rate (from `hiring-roadmap-builder`)
- `hiring-roadmap.md` — role-by-role hiring plan tied to milestones, fully-loaded cost, cumulative headcount and burn (from `hiring-roadmap-builder`)
- `unit-economics.md` — CAC, LTV, LTV/CAC, gross margin, payback period, staging honesty (from `unit-economics-builder`)
- `runway-scenarios.md` — conservative / base / aggressive P&L, cash-out dates, sensitivity on top 3 levers (from `scenario-planner`)
- `investor-metrics-summary.md` — the 6–10 numbers investors actually ask for, with one-line context each (from `scenario-planner`)

**Writes to `global/context/`:** none.

## Validation

This project is in a workable state when:

- `revenue-model.md` has three named scenarios with ARR build per period, an assumptions table where every row cites source (pricing doc, founder input, or illustrative), and a stated confidence rating.
- `hiring-roadmap.md` has every planned hire tied to a specific milestone, a fully-loaded cost multiplier applied (not raw salary), and cumulative quarterly cost.
- `cost-structure.md` breaks out people / tools / infra / G&A with monthly run rate and includes a "what happens to this number if we hire one fewer engineer" sensitivity note.
- `unit-economics.md` explicitly distinguishes modeled vs measured inputs. If the company is pre-revenue, every unit-economics number is flagged illustrative with an explicit stage-disclaimer.
- `runway-scenarios.md` shows cash-out dates for each scenario, and a sensitivity table on the top 3 levers (typically new-logo rate, average ACV, hiring pace).
- `investor-metrics-summary.md` is short (one page, 6–10 numbers) and every number traces back to one of the upstream output files.

A good Project 12 outcome: the founder can walk an investor through each number, cite the assumption behind it, and answer "what if you miss plan by half?" without inventing a new model on the spot.

**Note on scope:** This project does not replace a CFO or finance contractor once the company has revenue — once there is a real P&L, migrate to a proper financial workbook maintained by someone who can own it. This project does not file taxes, produce GAAP statements, or structure compensation plans. It does not claim accuracy beyond the assumptions stated, and it names that honestly at the top of every output.

---

## Don't See What You Need?

The skills in this project cover the most common financial-modeling tasks for pre-seed / seed founders, but they are not exhaustive.
If you need a capability that isn't covered, Claude Code includes two native built-in tools for this:

- **Skill creator** — Claude Code's built-in skill authoring tool. Use it to create a new custom skill
  and save it in this project's `.claude/skills/` directory (project-only) or in the root
  `.claude/skills/` directory (available across all projects). Financial-modeling-adjacent skills to
  consider: cap-table-modeler, 409a-prep-helper, board-deck-builder, variance-tracker.
- **MCP builder** — Claude Code's built-in MCP server builder. Use it if you want to connect
  Claude Code to an external tool or API. Most relevant here when you want to pull live data from
  accounting (QuickBooks, Xero), billing (Stripe, Chargebee), or cap-table (Carta, Pulley) systems.

Custom skills and MCP servers you create will live in your private fork and will not affect
the upstream repo. If you build something you think would benefit other founders, see CONTRIBUTING.md
for how to suggest it.
