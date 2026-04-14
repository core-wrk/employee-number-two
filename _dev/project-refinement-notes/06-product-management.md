# Project Refinement Notes: 06 Product Management

## Project Location

`projects/06-product-management/`

## Build Date

2026-04-14 — Initial build-out from scaffold-only state to a complete 4-skill project.

## Build Context

The prior remote agent run targeting this work (branch name `claude/plan-project-06-OgaH5`) errored before pushing any commits — no prior state to recover. This build started from the empty scaffold (CLAUDE.md stub + three empty skill directories with `.gitkeep`). The user provided an agreed-upon plan before build started; this document captures deviations from the architecture doc and the rationale for each.

## Build Decisions and Deviations from Architecture Doc

The architecture doc ([_dev/employee-number-two-architecture.md](../employee-number-two-architecture.md), Project 06 section) describes 3 skills. The actual build has 4 skills. Four intentional deviations:

### Deviation 1: Added `assumption-tracker` as 4th skill

**What changed:** The architecture doc specifies `prd-builder`, `epic-definer`, and `roadmap-builder` only. The build adds `assumption-tracker` as a 4th, ongoing skill.

**Why:** Project 06 sits between the static artifacts of Projects 01–05 (ICP, competitive landscape, pipeline data) and the live feedback loops of Projects 07 (engineering) and 08 (beta testing). Without an explicit assumption-tracking mechanism, invalidations surfaced in discovery calls, beta sessions, or pipeline movement have nowhere to land — they either rot in scattered notes or get silently baked into a revised PRD without traceability.

The `assumption-tracker` skill is the operational heartbeat that:
1. Seeds from PRD Section 10 (Assumptions and Open Questions)
2. Accepts evidence from Project 05 (pipeline) and Project 08 (beta) via source identifiers
3. Back-pressures on shipped and in-progress epics when assumptions are invalidated
4. Routes specific follow-up actions to `epic-definer` (re-scope) or `prd-builder` (revise)

Pattern: follows `waitlist-manager` from Project 04 (tracker/schema-enforcing, append-only, operational sections at top).

### Deviation 2: `prd-builder` writes PRD and `product-overview.md` atomically

**What changed:** The architecture doc implies separate outputs for PRD and product-overview, potentially produced by different skills or different runs. The build has `prd-builder` produce both in a single run with two separate preview-and-approval gates.

**Why:** The PRD and product-overview are two views of one decision. If they're produced by different skills or different runs, they drift — the PRD evolves and the product-overview lags, or vice versa. Downstream projects (especially Project 05 outbound and Project 11 fundraising) read the product-overview as authoritative; if it lags the PRD, outbound messaging and pitch narratives become stale relative to current strategy.

The atomic-write design enforces consistency: both files are written in the same run, after both have been previewed and approved separately. The founder sees each file's preview, approves independently, and both write in one atomic step.

### Deviation 3: `prd-builder` supports a minimal bootstrap short-circuit

**What changed:** The architecture doc assumes founders arrive at Project 06 ready for a full PRD. In practice, founders arrive at different readiness states. The build adds a 30-minute bootstrap path that produces only `product-overview.md`.

**Why:** Six downstream projects (Projects 05, 07, 08, 09, 11, 12) read `product-overview.md` as ground truth. A founder working on Project 05 (outbound sales) or Project 09 (pricing) might need `product-overview.md` to exist *before* they have enough evidence to write a full PRD. Forcing them through the full flow too early produces a weak PRD; forcing them to wait produces a blocked Project 05 or Project 09.

The bootstrap short-circuit resolves the tension: a 30-minute conversation covering JTBD, value prop, capabilities, differentiation, negative scope, and top-3 assumptions. Produces only `product-overview.md`. The founder returns later for the full PRD flow.

The short-circuit is offered at the start of every `prd-builder` run. The founder explicitly chooses: full PRD or bootstrap overview. No silent defaults.

### Deviation 4: 16 reference files vs. 4 named in architecture

**What changed:** The architecture doc names 4 references: `prd-template`, `user-story-guide`, `epic-template`, `roadmap-sequencing-principles`. The build has 16 references across the 4 skills.

**Why:** Projects 04 and 05 averaged 13–16 references proportional to skill complexity. The `prd-builder` skill especially needs multiple references because the PRD-building conversation is the highest-stakes strategic conversation in the entire repo — scope-gate rubrics, success-metrics patterns, and anti-patterns catalogs all prevent specific failure modes that would otherwise propagate downstream. The tracker skills (`epic-definer`, `assumption-tracker`) need references that enforce schema invariants, prioritization frameworks, and hygiene rules because they are parsed by downstream skills.

The full reference inventory is documented below.

## Skill Inventory (final)

| # | Skill | Pattern | Output | Phase |
|---|---|---|---|---|
| 1 | `prd-builder` | Canonical single doc (content-strategist analog) + atomic dual-write | `outputs/product-requirements-document.md` + `global/context/product-overview.md` | Strategy (linear, runs first) |
| 2 | `epic-definer` | Tracker/schema-enforcing (waitlist-manager analog) | `outputs/epic-list.md` | Strategy (linear, depends on #1) |
| 3 | `assumption-tracker` | Tracker/append-only, back-pressure (waitlist-manager analog) | `outputs/assumption-tracker.md` | Ongoing (heartbeat, re-run as evidence arrives) |
| 4 | `roadmap-builder` | Canonical single doc, re-runnable with audit trail (design-partner-advisor analog) | `outputs/roadmap.md` | Strategy (linear, depends on #2) |

## Cross-Project Dependencies

### Inbound (hard block)

- `global/context/icp.md` (Project 01)
- `global/context/competitive-landscape.md` (Project 01)

These are hard-required by `prd-builder`. Missing either causes an early-exit with instructions to complete Project 01.

### Inbound (warn, don't block)

- `global/context/startup-hypothesis.md` (Project 01)
- `global/context/founder-profile.md` (Project 00)
- `projects/02-brand-and-marketing/outputs/messaging-framework.md` (Project 02)
- `projects/04-inbound-marketing/outputs/waitlist-tracker.md` (Project 04)
- `projects/05-outbound-sales/outputs/prospect-list.md` (Project 05)
- `projects/05-outbound-sales/outputs/pipeline-tracker.md` (Project 05)

These make the PRD meaningfully better when present. Skills warn but proceed when missing. Note: Project 05's tracker skills are not yet built as of this writing (Project 05 is scaffold-only); the soft-reads will activate once Project 05 is built out.

### Outbound (global context)

- `global/context/product-overview.md` — written by `prd-builder` (full flow or bootstrap path). Read by Projects 05, 07, 08, 09, 11, 12.

### Outbound (project-scoped cross-reads)

- `outputs/epic-list.md` → read by Project 07's `epic-requirements-builder` (parses the table to generate engineering specs)
- `outputs/assumption-tracker.md` → read by Project 08's beta feedback synthesis (routes evidence to assumption IDs)

Schema changes to either file require coordinating with the consuming project and bumping `schema_version` in the frontmatter.

## Reference File Inventory (16 total)

| Skill | Reference Files |
|---|---|
| `prd-builder` (6) | `prd-template.md`, `product-overview-template.md`, `user-story-guide.md`, `scope-gate-rubric.md`, `success-metrics-patterns.md`, `prd-anti-patterns.md` |
| `epic-definer` (4) | `epic-template.md`, `prioritization-frameworks.md`, `effort-sizing-rubric.md`, `dependency-validation-rules.md` |
| `assumption-tracker` (3) | `assumption-status-rubric.md`, `validation-source-types.md`, `assumption-hygiene-rules.md` |
| `roadmap-builder` (3) | `roadmap-sequencing-principles.md`, `capacity-calibration-guide.md`, `current-bet-patterns.md` |

All references are internal lookups (not shown to the founder) and follow the kebab-case `.md` naming convention from Projects 01–05.

## Schema Invariants (Downstream Contracts)

Three files have load-bearing schemas that downstream projects parse. Changes require coordinated version bumps.

### `global/context/product-overview.md` — schema_version: 1

9 sections. Headline Value Proposition (1 sentence), Target Buyer, Core Capabilities (3–5 capability-level bullets), Differentiation (2–3 named-competitor deltas), Primary Use Cases (3–5 JTBDs), What This Product Is Not, Pricing Posture, Current Stage, Key Assumptions (top 3 with ID links to tracker).

Consumed by: Projects 05, 07, 08, 09, 11, 12.

### `outputs/epic-list.md` — schema_version: 1

Frontmatter: `schema_version`, `prioritization_framework` (RICE | MoSCoW), `generated_from`, `last_updated`.

Backlog table columns (fixed order): ID | Title | Problem | Priority | RICE Score | Effort | Status | Dependencies | Owner | Linked User Stories.

Enums: Priority (P0/P1/P2/P3), Effort (S/M/L/XL), Status (Not Started / Scoped / In Progress / Blocked / Shipped / Cut).

Stable IDs (E01, E02, ...) — never reassigned.

Consumed by: Project 07's `epic-requirements-builder`.

### `outputs/assumption-tracker.md` — schema_version: 1

Frontmatter: `schema_version`, `last_updated`, counts by status.

Table columns (fixed order): ID | Assumption | Status | Linked Epics | Last Source | Last Updated | Notes.

Status enum: Unvalidated / Validating / Validated / Invalidated / Revised. No "partially validated" or custom statuses.

Stable IDs (A01, A02, ...) — never reassigned.

Consumed by: Project 08's beta feedback synthesis.

## Pattern Reuse

The build drew on these as structural exemplars:

- `projects/04-inbound-marketing/.claude/skills/channel-strategist/SKILL.md` — hard-block prerequisite pattern, "force a real bet" pushback, 60-day kill criterion analog (applied to PRD non-goals and epic P0 caps)
- `projects/04-inbound-marketing/.claude/skills/content-strategist/SKILL.md` — synthesis-from-upstream pattern, preview-before-write workflow
- `projects/04-inbound-marketing/.claude/skills/waitlist-manager/SKILL.md` — tracker schema enforcement, append-only discipline, operational sections at top, "Never overwrite prior entries" rule (applied to both `epic-definer` and `assumption-tracker`)
- `projects/03-brand-identity/.claude/skills/brand-identity-synthesizer/SKILL.md` — ~227-line SKILL.md structure, Minimum Bar section, What Not To Do checklist

All 4 skills follow the same internal section order: Role → Prerequisites → Behavior → Flow → Minimum Bar → Output → What Not To Do.

## Open Questions / Future Refinements

- **Project 05 tracker skills are not yet built.** `prd-builder` and `assumption-tracker` soft-read `pipeline-tracker.md` and `prospect-list.md` from Project 05, but those skills are scaffold-only as of this build. When Project 05 is built out, verify the schemas match what Project 06 expects (especially the prospect slug format used as source identifiers in `assumption-tracker`).

- **Project 07 doesn't exist yet.** `epic-definer`'s schema is designed as the contract with Project 07's `epic-requirements-builder`, but that skill is scaffolded-only. When Project 07 is built, the parser should be validated against this schema and any drift coordinated via `schema_version` bumps.

- **Project 08 feedback routing is untested.** `assumption-tracker`'s source types include `beta-<YYYY-MM-DD>-<participant-slug>`, but Project 08's beta skills will define the exact slug format. May need to revisit `validation-source-types.md` after Project 08 is built.

- **RICE vs. MoSCoW in practice.** RICE is the default in `epic-definer`, with MoSCoW as fallback. Untested in real founder use — watch for the failure mode where founders game Confidence to boost favorite epics. May need a "confidence justification required" addition to the rubric.

- **Capacity calibration accuracy.** `capacity-calibration-guide.md` uses heuristic multipliers (context-switching penalty, effort-certainty discount). These are reasonable defaults but will need calibration once real effort-vs-actual data accumulates from shipped epics. Consider adding a "calibration drift" subsection to this dev notes file after 2–3 re-runs with real data.

- **Bootstrap short-circuit usage pattern.** The 30-minute bootstrap path is novel to this build. Watch for the failure mode where founders run the bootstrap, get `product-overview.md`, and never come back for the full PRD. May need stronger "come back" nudges in Project 05 outbound or Project 09 pricing.

- **`context-writer` skill not invoked explicitly.** `prd-builder` writes `global/context/product-overview.md` directly via Write tool, matching the pattern from Projects 01–03. The global `context-writer` skill is a scaffold; when it's built, revisit whether `prd-builder` should refactor to invoke it (for diff preview consistency) or keep the direct write.

- **`document-formatter` not invoked.** Outputs are formatted inline. Refactor when the global formatter exists.

## Feedback Log

| Date | Source | Feedback | Action Taken |
|---|---|---|---|
| 2026-04-14 | User-provided plan | Confirmed all 4 deviations from architecture: add assumption-tracker, atomic PRD+overview write, bootstrap short-circuit, 16 references | Built accordingly |

## Improvement Backlog

- Consider adding a `prd-reviewer` sub-skill that re-reads a PRD after 30 days with fresh eyes, surfaces sections that feel stale, and prompts targeted re-runs. The PRD is a living document but re-runs are driven by assumption invalidations today — there's no "time-based staleness" check.
- Consider a `roadmap-communicator` sub-skill that produces a prospect-facing or investor-facing view of the roadmap (date-translated, scoped differently). The canonical `roadmap.md` stays platform-agnostic; the communicator would translate for external stakeholders without polluting the internal view.
- Watch whether `epic-definer`'s 5-P0 cap is the right number. Early-stage products with 2 engineers probably can't ship 5 P0s in 6 months — the cap may need to scale with team size.
- Watch whether `assumption-tracker`'s 30-day staleness threshold is too aggressive. For products with long sales cycles (enterprise, regulated industries), 30 days may not be enough time for validation evidence to arrive. Consider making it configurable per-project.

## Observations

- The build revealed that Project 05 (which this project expects to read as soft evidence) is scaffold-only. The `assumption-tracker` source types include pipeline and prospect pointers, but Project 05's tracker schemas don't exist yet. When Project 05 is built, confirm alignment — specifically, the `prospect-<slug>` format in `validation-source-types.md` should match whatever Project 05's `prospect-researcher` assigns.
- The PRD pattern borrowed from `content-strategist` (synthesis from upstream + preview + write) mapped cleanly onto `prd-builder`, but the atomic dual-write (PRD + product-overview) required a new pattern — two separate previews, two approvals, one atomic write. This pattern may be reusable for other skills that produce linked canonical + compressed-extract pairs.
- The tracker pattern (`waitlist-manager` → `epic-definer` + `assumption-tracker`) transferred almost verbatim. The append-only + schema-enforcing + operational-sections-at-top structure is robust enough to handle both sequential-growth (epics: E01, E02, ...) and status-churning (assumptions that transition across statuses multiple times).
- Project 06 writes to `global/context/` (specifically `product-overview.md`). This is a deliberate departure from Projects 04 and 05, which do not. Project 06 is the central strategic hub; writing the summary view to global context is the correct architectural choice. All downstream projects (05, 07, 08, 09, 11, 12) should read from this single source of truth.
