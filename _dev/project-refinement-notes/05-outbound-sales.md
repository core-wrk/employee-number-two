# Project Refinement Notes: 05 Outbound Sales

## Project Location

`projects/05-outbound-sales/`

## Build Date

2026-04-11 — Initial build-out from scaffold-only state to a complete 7-skill project.

## Build Decisions and Deviations from Architecture Doc

The architecture doc ([_dev/employee-number-two-architecture.md](../employee-number-two-architecture.md), Project 05 section, lines 354–403) describes 5 skills. The actual build has 7 skills. Three intentional deviations:

### Deviation 1: Added `pipeline-tracker-manager` as the 6th skill (new)

**What changed:** The architecture doc lists `outputs/pipeline-tracker.md` as a file but does not assign a skill to own its ongoing maintenance. The build adds `pipeline-tracker-manager` as a dedicated skill that mirrors the `waitlist-manager` pattern from Project 04 exactly.

**Why:** Without an owning skill, `pipeline-tracker.md` becomes an orphaned file. Project 04 had the same gap until `waitlist-manager` was scoped to own `waitlist-tracker.md`. The pipeline tracker is the operational heartbeat of Project 05 — the founder returns to it every time a prospect changes stage — so it needs a dedicated skill that enforces the schema, preserves history, and flags stuck prospects.

**Operational consequence:** Project 08's eventual `beta-recruiter` will read both `waitlist-tracker.md` (from Project 04) and `pipeline-tracker.md` (from Project 05). Both files need the same A/B/C/D tier rubric and both need machine-parseable schemas. The two trackers are deliberately parallel in structure so the parser logic for Project 08 can handle them identically.

**Schema parity:** The pipeline tracker schema is `Email | Name | Company | Role | Source | Stage | Last Touch | Next Action | ICP Tier | Notes` with frontmatter `schema_version: 1`. The stage enum is fixed: `Prospecting | Contacted | Replied | Meeting Scheduled | Design Partner Conversation | Committed | Lost | Stalled`.

### Deviation 2: Added `objection-handler` as the 7th skill (new)

**What changed:** The architecture has `pre-call-brief-builder` (per-call prep) and `design-partner-advisor` (conversation framing) but nothing for moment-of-truth objection handling. The build adds `objection-handler` which produces a personalized objection playbook across 7 categories (pricing, timing, trust, competition, fit, authority, proof).

**Why:** Cold outreach generates objections at every stage. A founder who has not pre-thought their answers freezes mid-conversation or over-promises in real time. This cannot be addressed by `pre-call-brief-builder` alone (which is per-call) or by `design-partner-advisor` (which is about framing the engagement, not about answering specific pushbacks). The objection playbook is a single canonical document the founder references before every call, and the skill is re-runnable so new objections can be added as they surface in real conversations.

**Operational consequence:** `pre-call-brief-builder` reads `objection-playbook.md` if it exists and surfaces the top 3 objections most likely for each specific prospect. This creates a natural flow: build the playbook once, then every brief references it.

### Deviation 3: Kept `email-drafter` channel-agnostic (considered split into email + LinkedIn DM, rejected)

**What was considered:** Splitting `email-drafter` into `email-drafter` (cold email) + `linkedin-outreach-drafter` (cold LinkedIn DM). This would have mirrored how Project 04 split `linkedin-writer` and `founder-linkedin-builder`.

**Why not:** Cold email and cold LinkedIn DM share the same load-bearing logic (read prospect row, apply brand voice, personalize against the ICP, refuse mail-merge-token personalization). The differences are surface-level: character limits, subject line presence, opener conventions. These are handled by a format parameter inside one skill, with the per-channel rules captured in `references/outreach-formats.md`. This mirrors how `linkedin-writer` handles multiple post formats (text post, document carousel, poll, repost-commentary) within one skill rather than splitting them.

**The Project 04 split was different:** `linkedin-writer` and `founder-linkedin-builder` were split because of *voice* divergence (company voice vs. founder personal voice). For outbound, the voice is consistently the founder's voice across email and LinkedIn, so the split would not earn its own skill.

**Operational consequence:** Founders draft one prospect, one format (email OR LinkedIn DM), one sequence position (initial / FU1 / FU2 / breakup) per skill run. They run `email-drafter` multiple times for the same prospect as the sequence progresses.

## Skill Inventory (final)

| # | Skill | Output | Phase |
|---|---|---|---|
| 1 | `prospect-researcher` | `outputs/prospect-list.md` | Research (linear, runs first) |
| 2 | `email-drafter` | `outputs/outreach-drafts/<prospect-slug>-<sequence-position>.md` | Execution (parallel, depends on #1) |
| 3 | `pre-call-brief-builder` | `outputs/pre-call-briefs/<prospect-slug>-<YYYY-MM-DD>.md` | Execution (per-call) |
| 4 | `design-partner-advisor` | `outputs/design-partner-framework.md` | Strategic (single canonical doc, re-runnable) |
| 5 | `objection-handler` | `outputs/objection-playbook.md` | Strategic (re-runnable, append-only) |
| 6 | `pipeline-tracker-manager` | `outputs/pipeline-tracker.md` | Ongoing (heartbeat — runs every stage change) |
| 7 | `crm-sync-advisor` | `outputs/crm-export/contacts.csv`, `companies.csv`, `README.md` | Operational (on-demand export) |

## Cross-Project Dependencies

### Inbound

Project 05 reads (and refuses to run without) the following from `global/context/`:

- `icp.md` (from Project 01) — required by all skills except `crm-sync-advisor`
- `brand-voice.md` (from Project 02) — required by `email-drafter`, `objection-handler`, `design-partner-advisor`
- `competitive-landscape.md` (from Project 01) — required by `prospect-researcher`, `pre-call-brief-builder`, `objection-handler`
- `founder-profile.md` (from Project 00) — required by `prospect-researcher`, `design-partner-advisor`, `objection-handler`
- `startup-hypothesis.md` (from Project 01) — required by `design-partner-advisor`, `objection-handler`

Project 05 also reads (and warns if missing) the following:

- `global/context/product-overview.md` — recommended by `email-drafter`, `pre-call-brief-builder`, `design-partner-advisor`, `objection-handler`. **Critical caveat:** `product-overview.md` is produced by Project 06, which is sequenced *after* Project 05 in the architecture. In practice, founders often run Project 05 before Project 06 because outbound conversations are themselves valuable input to product management. The skills must warn but not block.
- `projects/02-brand-and-marketing/outputs/messaging-framework.md` — recommended for `email-drafter`, `objection-handler`

### Outbound

Project 05 writes nothing to `global/context/`. All outputs are project-scoped.

The single exception to "fully scoped to this project" is `outputs/pipeline-tracker.md`, which is read by Project 08 (`beta-and-user-testing`) for beta recruitment cross-referencing. The schema for this file is intentionally machine-parseable and `pipeline-tracker-manager` enforces:

- Required columns: Email, Name, Company, Role, Source, Stage, Last Touch, Next Action, ICP Tier, Notes
- Stage enum (fixed, non-negotiable): Prospecting / Contacted / Replied / Meeting Scheduled / Design Partner Conversation / Committed / Lost / Stalled
- ICP Tier values: A / B / C / D (matching `waitlist-manager`'s enum)
- Header counts that always reflect the stage distribution
- A "Stuck Prospects" section flagging prospects past their stage's stuck threshold
- A "Design Partner Candidates" section listing prospects in `Design Partner Conversation` stage
- Frontmatter with `schema_version: 1`

If Project 08's eventual `beta-recruiter` needs schema changes, they should be coordinated here and with `waitlist-manager`, and versioned in the `schema_version` frontmatter field.

## Reference File Inventory

16 reference files were created across the 7 skills:

| Skill | Reference Files |
|---|---|
| `prospect-researcher` | `lead-qualification-rubric.md`, `prospect-search-strategies.md` |
| `email-drafter` | `outreach-sequence-template.md`, `personalization-variables.md`, `outreach-formats.md`, `cold-outreach-anti-patterns.md` |
| `pre-call-brief-builder` | `pre-call-brief-template.md`, `discovery-question-bank.md` |
| `design-partner-advisor` | `design-partner-framework.md`, `design-partner-agreement-skeleton.md` |
| `objection-handler` | `common-objection-categories.md`, `objection-response-patterns.md` |
| `pipeline-tracker-manager` | `pipeline-stages-rubric.md`, `pipeline-hygiene-rules.md` |
| `crm-sync-advisor` | `crm-import-schemas.md`, `crm-tool-comparison.md` |

Four are architecture-named (`lead-qualification-rubric`, `outreach-sequence-template`, `personalization-variables`, `pre-call-brief-template`); twelve are new to this build.

All references are internal lookups (not shown to the founder) and follow the kebab-case `.md` naming convention from Projects 01–04.

## Open Questions / Future Refinements

- **`product-overview.md` sequencing tension:** Project 06 produces this file but Project 05 wants to read it. The skills warn but don't block on missing `product-overview.md`, falling back to `startup-hypothesis.md` for the value proposition. Watch for failure modes where the warning is ignored and drafts become vague. May need to iterate on how strongly the warning is surfaced.
- **`third-party-advisor` invocation:** Same inherited pattern from Project 04. The global `third-party-advisor` skill is still a scaffold. Project 05 skills surface tool recommendations inline (Apollo, ZoomInfo, Clay, LinkedIn Sales Navigator, Lemlist, HubSpot, Salesforce, Airtable, etc.). Refactor to invoke the global skill when it's built.
- **`context-loader` and `document-formatter` not invoked:** Same inherited pattern from Project 04. Skills read global context directly and format outputs inline. Refactor when the global skills are built.
- **`web-researcher` invocation:** Unlike the other global skills, `web-researcher` has a real SKILL.md (it is not just a scaffold). `prospect-researcher` should consider invoking it via the Skill tool for actual web searches rather than reimplementing search logic. Current build has `prospect-researcher` doing web searches directly; this is one place Project 05 could lean on the global skill for consistency. Flag for refactor.
- **Pipeline tracker / waitlist tracker dedup in Project 08:** Project 08's eventual `beta-recruiter` will need to handle prospects who appear in both `waitlist-tracker.md` (Project 04) and `pipeline-tracker.md` (Project 05) — e.g., someone who joined the waitlist AND was cold-outreached. Email is the natural dedup key. The plan does not solve this; it surfaces it as a Project 08 design decision. Both tracker schemas include email as a first-class field to make dedup feasible.
- **Cold outreach legal liability:** CAN-SPAM (US), GDPR (EU), CASL (Canada) all have implications for cold outreach. `email-drafter` mentions this inline once (on the founder's first run) and recommends running Project 01's `early-legal-checker`. This is a one-line callout, not a blocking check. Watch for failure modes where founders ignore it and later hit a regulatory problem.
- **The "validation not selling" framing in `pre-call-brief-builder`:** The skill is designed to refuse to produce a sales script and to force founders toward learning-oriented call success criteria. This is the right call but is also the most likely place where founders push back. Watch for cases where the skill needs to push back more gently or where the founder finds workarounds.
- **Whether `objection-handler` and `design-partner-advisor` should eventually merge:** Both are strategic prep skills that produce single canonical docs. They are kept separate because the conversations differ fundamentally (defense vs. reframing). Re-evaluate after real founder use — if founders are running both within the same session and the distinctions feel artificial, consider merging.
- **The "would I send this to a friend?" test in `email-drafter`:** This test is the final check before showing a draft preview. It is a judgment call, not a mechanical check. Watch for cases where the skill lets through drafts the founder later regrets — the test may need to be made more explicit or more skeptical.
- **Iteration on `pipeline-tracker-manager` after live data:** The stuck-prospect thresholds (14 days for most stages, 21 for Meeting Scheduled, 30 for Design Partner Conversation) are untested in real founder use. Watch for the failure mode where founders avoid the "move to Stalled or Lost" decision. May need a "forced decision" nudge for long-stuck prospects.

## Feedback Log

| Date | Source | Feedback | Action Taken |
|---|---|---|---|
| 2026-04-11 | Build planning | User confirmed all 3 recommended design decisions: add `pipeline-tracker-manager` and `objection-handler` as the 2 additions, keep `email-drafter` channel-agnostic with format parameter, warn-don't-block on missing `product-overview.md` | Built accordingly |

## Improvement Backlog

- Add a `follow-up-sequence-scheduler` reference or sub-skill if the 4-touch sequence timing (days 0, 3–5, 10, 21) needs more per-prospect calibration — currently handled inline inside `email-drafter`
- Consider a `competitor-intel-gatherer` skill for founders who want to run intelligence-gathering conversations with competitor employees (currently flagged as a prospect-list hard rule: never prospect into competitors without explicit founder confirmation)
- Add a `warm-intro-requester` skill if the founder's network is their primary sourcing strategy — drafting a message asking a mutual contact for an intro is a distinct craft from cold outreach, currently not covered
- Consider whether `prospect-researcher` should integrate deeper with Reddit/community sources (currently handled in `prospect-search-strategies.md` reference but could be a dedicated sourcing sub-skill)
- Watch for whether founders want a dedicated `sales-meeting-transcriber` or `call-notes-synthesizer` skill for processing meeting notes into `pipeline-tracker-manager` updates — currently the founder types notes into pipeline-tracker-manager manually
- Consider whether `email-drafter` should eventually read prior drafts for the same prospect when drafting follow-ups, to maintain thread continuity (currently it doesn't; each sequence position is drafted independently)

## Observations

- The build leaned heavily on Project 04's `channel-strategist` (for the "stop and tell the founder" prerequisite pattern, the phase-by-phase flow with explicit rationale, and the minimum bar gating) and Project 04's `waitlist-manager` (for `pipeline-tracker-manager`'s never-overwrite, read-existing-first, schema-enforcement pattern). Both were good exemplars for Project 05's needs.
- All 7 skills follow the same internal section order (Role → Prerequisites → Behavior → Flow → Minimum Bar → Output → What Not To Do). Consistency across skills is more valuable than per-skill optimization at this stage.
- Only one Project 05 skill writes to `global/context/` — none of them. All outputs stay project-scoped. This matches Project 04's deliberate departure from Projects 01–03 (which wrote to global). The only cross-project outbound dependency is `pipeline-tracker.md`, which is read directly by Project 08.
- The "warn but don't block on missing `product-overview.md`" pattern is a new kind of prerequisite handling compared to Project 04 (which uses hard blocks on all required files). This soft-warn pattern exists because Project 06 is sequenced after Project 05 in practice, even though the architecture lists it earlier. Watch for whether this creates confusing founder experience.
- The `pipeline-tracker.md` and `waitlist-tracker.md` schema parallelism (both use A/B/C/D tiers, both have operational sections at the top, both are machine-parseable) was deliberately designed to make Project 08's eventual parser logic simple. If either schema diverges, coordinate the change across both.
- `crm-sync-advisor` is the only Project 05 skill that produces non-markdown outputs (CSVs). Handle carefully — CSVs have their own quoting rules and the skill's output format must be CSV-valid, not just markdown-formatted text.
- The reference-file count (16) is higher than Project 04's (13). The higher count reflects Project 05's heavier dependence on internal frameworks for things like objection handling (2 references), CRM schema mapping (2 references), and email-specific patterns (4 references) that Project 04 did not need.
