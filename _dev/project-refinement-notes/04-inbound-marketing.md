# Project Refinement Notes: 04 Inbound Marketing

## Project Location

`projects/04-inbound-marketing/`

## Build Date

2026-04-09 — Initial build-out from scaffold-only state to a complete 9-skill project.

## Build Decisions and Deviations from Architecture Doc

The architecture doc ([_dev/employee-number-two-architecture.md](../employee-number-two-architecture.md), Project 04 section, lines 292–352) describes 7 skills. The actual build has 9 skills. Two intentional deviations:

### Deviation 1: Split `content-strategist` into `channel-strategist` + `content-strategist`

**What changed:** The architecture doc describes a single `content-strategist` skill that produces both `marketing-channel-strategy.md` and `content-calendar.md`. The build splits this into two sequenced skills: `channel-strategist` produces the channel strategy, and `content-strategist` produces the calendar.

**Why:** Channel strategy and content calendar are sequenced — the calendar cannot be built until the channel mix is decided. Forcing both into a single skill conflated two distinct conversations and produced muddled outputs in dry-run testing. The split mirrors the strict-linear pattern used in Project 02 (`positioning-strategist → messaging-architect → brand-voice-developer`), where each skill builds on the prior one's artifact and refuses to run without it.

**Operational consequence:** `content-strategist` now refuses to run without `marketing-channel-strategy.md`. This creates a clean dependency that matches how the founder will actually use the project — they will run channel strategy once, then run content strategy a few times as they iterate calendars.

### Deviation 2: Added `founder-linkedin-builder` as a distinct skill

**What changed:** The architecture doc mentions `founder-linkedin-builder` in the "Recommended Additional Projects" section (line 753–754) but the original Project 04 CLAUDE.md omitted it from the skills table. The build adds it as the 9th skill, distinct from `linkedin-writer`.

**Why:** Personal brand and company brand are deliberately distinct on LinkedIn. A founder posting in the company voice on their personal profile gets tuned out. A founder posting in their own voice — opinionated, specific, willing to admit live questions — builds trust at venture velocity. Collapsing personal and company voice into one skill produces drafts that drift toward whichever voice the founder happened to load most recently. Two skills with explicit voice contrast keeps the divergence intentional.

**File naming convention:** Both skills write to `outputs/linkedin/` to keep LinkedIn content in one place, but `founder-linkedin-builder` uses a `founder-` filename prefix (e.g., `outputs/linkedin/founder-ramp-time-take.md`) so the two voices are visually separable in the directory listing.

## Skill Inventory (final)

| # | Skill | Output | Phase |
|---|---|---|---|
| 1 | `channel-strategist` | `outputs/marketing-channel-strategy.md` | Strategy (linear, runs first) |
| 2 | `content-strategist` | `outputs/content-calendar.md` | Strategy (linear, depends on #1) |
| 3 | `blog-writer` | `outputs/blog/<slug>.md` | Execution (parallel) |
| 4 | `linkedin-writer` | `outputs/linkedin/<slug>.md` (company voice) | Execution (parallel) |
| 5 | `founder-linkedin-builder` | `outputs/linkedin/founder-<slug>.md` (founder voice) | Execution (parallel) |
| 6 | `reddit-engager` | `outputs/reddit-engagement/<thread-slug>.md` | Execution (reactive) |
| 7 | `youtube-scriptwriter` | `outputs/youtube/<slug>.md` | Execution (parallel) |
| 8 | `technical-report-writer` | `outputs/technical-reports/<slug>.md` | Execution (event-driven, quarterly max) |
| 9 | `waitlist-manager` | `outputs/waitlist-tracker.md` | Ongoing (runs every time founder has new signups) |

## Cross-Project Dependencies

### Inbound

Project 04 reads (and refuses to run without) the following from `global/context/`:

- `brand-voice.md` (from Project 02) — required by every writer skill
- `brand-identity.md` (from Project 03) — referenced by `blog-writer` and `technical-report-writer` for visual register; not strictly required to draft content
- `icp.md` (from Project 01) — required by every skill except `blog-writer` (which strictly requires `brand-voice.md` plus `icp.md`)
- `startup-hypothesis.md` (from Project 01) — required by `channel-strategist`, `founder-linkedin-builder`, `reddit-engager`, `technical-report-writer`
- `founder-profile.md` (from Project 00) — required by `founder-linkedin-builder` heavily; loaded by `channel-strategist` for capacity calibration
- `competitive-landscape.md` (from Project 01) — required by `technical-report-writer`; recommended for `blog-writer`

Project 04 also reads (and warns if missing) the following from prior projects:

- `projects/02-brand-and-marketing/outputs/messaging-framework.md` — used as the topical backbone for `content-strategist`, `blog-writer`, `linkedin-writer`, `youtube-scriptwriter`, and `technical-report-writer`. Skills warn but do not stop if missing.

### Outbound

Project 04 writes nothing to `global/context/`. All outputs are project-scoped.

The single exception to "fully scoped to this project" is `outputs/waitlist-tracker.md`, which is read by Project 08 (`beta-and-user-testing`) for beta recruitment. The schema for this file is intentionally machine-parseable and `waitlist-manager` enforces:

- Required columns: Email, Name, Company, Role, Source, Date, Tier, Notes, Next Action
- Tier values: A / B / C / D (no "Unknown")
- Header counts that always reflect the tier distribution
- A "Top Tier-A this week" section that Project 08 can find without parsing the full table

If Project 08's eventual `beta-recruiter` skill needs schema changes, they should be coordinated here and versioned in the `schema_version` frontmatter field of the tracker file.

## Reference File Inventory

13 reference files were created across the 9 skills:

| Skill | Reference Files |
|---|---|
| `channel-strategist` | `channel-evaluation-rubric.md`, `channel-archetypes.md` |
| `content-strategist` | `content-calendar-template.md` |
| `blog-writer` | `blog-post-formats.md` |
| `linkedin-writer` | `linkedin-post-formats.md`, `linkedin-hooks-library.md` |
| `founder-linkedin-builder` | `founder-vs-company-voice.md` |
| `reddit-engager` | `reddit-engagement-rules.md`, `authentic-voice-guide.md` |
| `youtube-scriptwriter` | `youtube-script-template.md` |
| `technical-report-writer` | `research-report-structure.md`, `data-source-options.md` |
| `waitlist-manager` | `waitlist-qualification-criteria.md` |

All references are internal lookups (not shown to the founder) and follow the kebab-case `.md` naming convention from Projects 01–03.

## Open Questions / Future Refinements

- **`third-party-advisor` invocation:** The architecture doc describes a global `third-party-advisor` skill that surfaces tool recommendations. That skill is currently a scaffold with no SKILL.md. Project 04 skills currently surface tool recommendations inline (e.g., `channel-strategist` mentions Buffer/Hypefury/Typefully; `technical-report-writer` mentions Typeform/Statista/SparkToro). Once `third-party-advisor` is built, refactor these skills to invoke it instead of inline mentions.
- **`context-loader` not invoked explicitly:** Each Project 04 skill reads global context files directly via the Read tool, not via the global `context-loader` skill (which is also currently a scaffold). When `context-loader` is built, consider whether Project 04 skills should refactor to invoke it for consistency with the global pattern, or whether direct reads remain simpler for execution-heavy skills that always load the same set of files.
- **`document-formatter` not invoked:** Same situation. Outputs are formatted inline by each skill rather than passed through the global formatter. Refactor when the global skill is built.
- **Iteration on `channel-strategist` after live data:** The 60-day kill criteria pattern is untested in real founder use. Watch for the failure mode where founders avoid cutting channels even when the kill criterion fires. May need a "60-day review" sub-skill or a stronger nudge in the iteration flow.
- **`technical-report-writer` and the data-question check:** The skill is designed to refuse to draft a hollow report. This is the right call but is also the most likely place where founders push back. Watch for cases where the skill needs to refuse more gently or where the founder finds workarounds.

## Feedback Log

| Date | Source | Feedback | Action Taken |
|---|---|---|---|
| 2026-04-09 | Build planning | User confirmed all 4 recommended decisions: add founder-linkedin-builder, split channel/content strategists, scope tech reports as industry research, match Project 02/03 SKILL.md depth | Built accordingly |

## Improvement Backlog

- Add a `linkedin-comment-engager` sub-skill once the founder has built initial LinkedIn presence — engagement on others' posts is high-leverage and currently unaddressed
- Add a `youtube-thumbnail-strategist` sub-skill or reference if YouTube becomes a primary channel — thumbnails are 50% of YouTube success and currently get ~1 paragraph of guidance
- Consider whether `reddit-engager` should optionally invoke `web-researcher` to verify thread context or surface related threads
- Watch for whether `blog-writer` needs a separate `seo-blog-writer` variant calibrated specifically for search-intent content (the current skill handles all four intents in one)

## Observations

- The build leaned heavily on Project 02's `brand-voice-developer` and Project 03's `brand-identity-synthesizer` as structural exemplars. Both are good models for the "applies brand context, refuses if prerequisites missing, produces a downstream-readable artifact" pattern that all Project 04 skills inherit.
- The "stop and tell the founder" missing-prerequisite block from `brand-identity-synthesizer` is reused (in spirit) across every Project 04 skill. It is the cleanest way to enforce dependencies without leaving the founder confused about what to do next.
- All 9 skills follow the same internal section order (Role → Prerequisites → Behavior → Flow → Minimum Bar → Output → What Not To Do). Consistency across skills is more valuable than per-skill optimization at this stage.
- No Project 04 skill writes to `global/context/`. This is a deliberate departure from Projects 01–03, which all wrote to global. Project 04 is execution-focused and produces artifacts that downstream projects either consume directly (`waitlist-tracker.md`) or ignore. The only outbound dependency is the tracker schema, which is documented above.
