# Project 06 — Product Management

## Purpose

This is where the market evidence from Projects 01–05 becomes a structured product. The goal is threefold: translate validated buyer needs into a canonical Product Requirements Document, break that PRD into a prioritized, machine-parseable backlog of epics, and maintain an honest view of what's next — sequenced by dependency and capacity, not by wishful dates.

By the end of this project you will have a PRD that names goals AND non-goals, a `global/context/product-overview.md` that six downstream projects read as ground truth, an epic list that Project 07 parses into engineering specs, a roadmap organized as Now / Next / Later (not quarters), and an assumption tracker that catches invalidations early and back-pressures on shipped work when beliefs turn out to be wrong.

This is the center of the repo. Projects 01–05 produce the inputs; Projects 07–12 consume the outputs. A weak PRD here propagates into weak engineering scoping, weak pricing decisions, weak fundraising narratives, and weak beta recruitment downstream. The skills are designed to force the conversations that prevent that.

## Prerequisites

Complete Project 01 (market research) first — `icp.md` and `competitive-landscape.md` are hard-required by `prd-builder`. The other skills will refuse to run without their direct upstream artifact (`prd-builder` → `epic-definer` → `assumption-tracker` → `roadmap-builder`).

Projects 02, 04, and 05 are soft prerequisites. If they exist, their outputs (`messaging-framework.md`, `waitlist-tracker.md`, `pipeline-tracker.md`) are pulled in as evidence; if they don't, the skills warn but proceed. The quality of the PRD increases materially with discovery-call data from Project 05, so most founders should complete at least some Project 05 work before running `prd-builder` in full.

If you need a `product-overview.md` to unblock Project 05 (outbound), Project 09 (pricing), or Project 11 (fundraising) *before* you're ready for a full PRD, `prd-builder` offers a **minimal bootstrap path** — a 30-minute conversation that produces only the product-overview. You return for the full flow when you have more evidence.

## Global Context Files

**Loads:** `icp.md`, `competitive-landscape.md`, `startup-hypothesis.md`, `founder-profile.md`, `product-overview.md` (if exists), `brand-voice.md` (if exists for tone), `messaging-framework.md` (via Project 02, if exists)

**Writes:** `product-overview.md`. This file is the canonical product summary read by Projects 05, 07, 08, 09, 11, and 12. Its schema is load-bearing — the `prd-builder` skill enforces it.

## How This Project Works

Skills fall into two groups:

1. **Strategy (strict linear)** — `prd-builder` runs first and produces the PRD plus `product-overview.md`. `epic-definer` runs second and breaks the PRD into an epic backlog. `roadmap-builder` runs last and sequences the epics. Each skill refuses to run without its upstream artifact, so you cannot accidentally sequence ahead.
2. **Ongoing (heartbeat)** — `assumption-tracker` is not a one-time skill. You return to it every time new evidence arrives from discovery calls, beta sessions, pipeline movement, or internal experiments. When an assumption is invalidated, the tracker back-pressures on shipped and in-progress epics and surfaces the specific next action (re-run `epic-definer` or `prd-builder`).

All skills are conversational. They ask one question at a time, ground every recommendation in evidence from Projects 01–05, and show a complete preview before writing any file. Previews for `prd-builder` are two separate approvals (PRD and product-overview are two views of one decision, approved independently).

**Iteration is expected.** The PRD you write in week 1 will be wrong by week 8 — not because it was bad, but because 8 weeks of contact with reality changes what matters. Re-run `prd-builder` when the bet shifts. Re-run `epic-definer` after `assumption-tracker` surfaces invalidations. Re-run `roadmap-builder` every 4 weeks or after any Now epic ships.

## Skills

| Skill | Description |
|---|---|
| `prd-builder` | Produce a full PRD (13 sections) and the compressed `product-overview.md` extract. Supports a 30-minute bootstrap path that produces only the overview. |
| `epic-definer` | Break the PRD into a prioritized, ID-stable epic list. RICE scoring by default, MoSCoW as fallback. Schema is the contract with Project 07. |
| `assumption-tracker` | Maintain the canonical list of product assumptions with validation status, sources, and back-pressure on shipped work when invalidations occur. |
| `roadmap-builder` | Sequence epics into Now / Next / Later with a named Current Bet, capacity-checked, dependency-respecting, with explicit Not Doing and Previous Bets audit trail. |

## Recommended Flow

**First-time through:**

1. **`prd-builder`** — 60–90 minutes for full flow, 30 minutes for bootstrap. Reads Project 01's ICP and competitive landscape; pulls in Project 04 waitlist and Project 05 pipeline/prospect data as soft evidence. Writes the PRD and `product-overview.md`. Seeds `assumption-tracker.md` if it doesn't exist.
2. **`epic-definer`** — 45–60 minutes. Enumerates candidate epics from PRD pillars and user stories, sizes (S/M/L/XL), scores (RICE), validates dependencies, and writes `epic-list.md`. Refuses to run without the PRD.
3. **`roadmap-builder`** — 30–45 minutes. Names the Current Bet paragraph, sequences epics into Now / Next / Later, capacity-checks Now, and writes `roadmap.md`. Refuses to run without `epic-list.md`.

**Ongoing:**

4. **`assumption-tracker`** — 15–30 minutes per run. Returns whenever you have new validation evidence. Updates status, surfaces back-pressure, and names the next action. If the back-pressure points to `epic-definer` or `prd-builder`, re-run those.

**When to re-run the strategy skills:**

- Re-run `prd-builder` when Section 11 (Risks) or Section 5 (Goals) no longer matches reality — typically driven by invalidated assumptions affecting shipped work.
- Re-run `epic-definer` after shipping meaningful work (update statuses), after a re-priorization, or after `assumption-tracker` surfaces invalidations affecting in-progress epics.
- Re-run `roadmap-builder` every 4 weeks, after any Now epic ships, or after a capacity change (new hire, founder attention shift).

## Outputs

All saved in `projects/06-product-management/outputs/`:

- `product-requirements-document.md` — 13-section PRD (from `prd-builder`)
- `epic-list.md` — Prioritized epic backlog with stable IDs, RICE scores, dependencies, operational sections (from `epic-definer`)
- `assumption-tracker.md` — Canonical assumption list with validation status, sources, back-pressure (from `assumption-tracker`)
- `roadmap.md` — Now/Next/Later with Current Bet, triggers, open questions, Not Doing, Previous Bets (from `roadmap-builder`)

One file is written to global context:

- `global/context/product-overview.md` — Compressed product summary read by 6 downstream projects (from `prd-builder`)

## Cross-Project Reads (schemas are load-bearing)

Three outputs are read directly by downstream projects. Their schemas are enforced and versioned:

- `global/context/product-overview.md` → read by Projects 05, 07, 08, 09, 11, 12
- `outputs/epic-list.md` → read by Project 07's `epic-requirements-builder` (parses the table)
- `outputs/assumption-tracker.md` → read by Project 08's beta feedback synthesis (routes evidence to assumption IDs)

Schema changes to any of these require coordinating with the consuming project and bumping `schema_version` in the frontmatter.

## Validation

This project is in a workable state when:

- `product-requirements-document.md` exists with all 13 sections non-empty, at least 3 goals + 3 non-goals, at least 3 success metrics with baselines and targets, at least 5 user stories grouped by pillar, at least 5 assumptions with linked scope, and a named #1 risk.
- `global/context/product-overview.md` exists, all 9 sections populated, headline value prop is one sentence (not a paragraph), differentiation references named competitors from `competitive-landscape.md`, and Key Assumptions link to `assumption-tracker.md` by ID.
- `epic-list.md` exists with frontmatter intact, ≤5 P0 epics, every P0/P1 linked to user stories, no dependency cycles or priority contradictions, and operational sections (Counts, Next Up, Blocked, Recently Shipped) refreshed.
- `roadmap.md` exists with a one-paragraph Current Bet, at least 1 Now epic respecting capacity, every Next epic with a named trigger, every Later epic with an open question, and at least 1 Not Doing entry with rationale.
- `assumption-tracker.md` exists, seeded from PRD Section 10, with every status transition having a source identifier and no custom statuses ("partially validated" etc. rejected).

A good Project 06 outcome is one where Project 07 can run `epic-requirements-builder` without ambiguity, Project 05's outbound messaging can quote the product-overview verbatim, and `assumption-tracker` is catching 2–3 invalidations per month that back-pressure on engineering or pricing decisions early enough to matter.

Weak signals that this project's work is thin: a PRD with empty non-goals, a product-overview with a paragraph-long value prop, an epic list with 8+ P0 epics, a roadmap with no Current Bet, or an assumption tracker that hasn't been updated in 60+ days. When you see those, re-run the affected skill.

**Note on scope:** Engineering scoping (turning epics into detailed specs) is Project 07. Pricing and packaging decisions are Project 09. Beta recruitment and feedback synthesis are Project 08. This project produces the strategic structure; those projects act on it.

---

## Don't See What You Need?

The skills in this project cover the most common tasks for this stage, but they are not exhaustive.
If you need a capability that isn't covered, Claude Code includes two native built-in tools for this:

- **Skill creator** — Claude Code's built-in skill authoring tool. Use it to create a new custom skill
  and save it in this project's `.claude/skills/` directory (project-only) or in the root
  `.claude/skills/` directory (available across all projects).
- **MCP builder** — Claude Code's built-in MCP server builder. Use it if you want to connect
  Claude Code to an external tool or API.

Custom skills and MCP servers you create will live in your private fork and will not affect
the upstream repo. If you build something you think would benefit other founders, see CONTRIBUTING.md
for how to suggest it.
