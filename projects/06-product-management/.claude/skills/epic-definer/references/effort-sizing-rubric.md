# Effort Sizing Rubric

Internal reference used by `epic-definer` in Phase 4. Maps T-shirt sizes to honest week-counts for a small team.

## Size Definitions (Small Team: 1–4 engineers)

### S — ~1 week

- One engineer, one week, no blockers
- Touches a single component or file cluster
- Uses existing patterns; no new abstractions
- No new external integrations
- No schema changes (or very minor ones)

**Examples:**
- Add a new field to an existing form + save to DB
- Add a new CSV export endpoint to an existing report
- Fix a bug that has a clear reproduction
- Rename a feature across the app

### M — ~3 weeks

- One engineer ~3 weeks, or 2 engineers ~1.5 weeks
- Touches 3–5 components across 1–2 services
- Introduces one new concept or abstraction
- May include one simple external integration (OAuth + basic API read)
- Includes schema changes with migration

**Examples:**
- Build a new report type with ~5 chart variations
- Add single-sign-on via Google Workspace
- Rebuild an existing flow for a new persona
- Ship a new settings/admin panel

### L — ~6 weeks

- Team of 2 engineers ~3 weeks, or 1 engineer ~6 weeks
- Cross-cutting: touches frontend, backend, DB, possibly ops
- Introduces a new core domain concept
- Includes a meaningful external integration with two-way sync
- Non-trivial migration of existing data
- Requires some design work (not just dev)

**Examples:**
- Build first-class Salesforce integration (read + write + webhooks)
- Ship cohort-based reporting as a new major capability
- Add role-based permissions to an app that had none
- Multi-tenant data isolation where previously single-tenant

### XL — ~12 weeks

- Team of 2 engineers for a full quarter
- Touches every layer of the stack
- Introduces a new architectural pattern (new service, new data store)
- Multi-party integration (3+ external systems)
- Significant data migration with production downtime risk
- Likely needs decomposition before accepting

**Examples:**
- Rewrite the core data model
- Add a new primary product surface (mobile app, API product, etc.)
- Migrate from monolith to microservices
- Build a new customer-facing reporting product

**Rule:** XL epics should almost always be decomposed into an L + a series of M/S before shipping. Accept XL only if the founder has explicitly acknowledged the 12-week commitment and the decomposition isn't clean.

## The Under-Sizing Failure Mode

The most common sizing failure is marking everything S. Symptoms:

- "It's just a dropdown"
- "We already have most of it"
- "The hard part is already done"

Push back with:

> "What's the smallest version that actually ships to users? Tell me about the edge cases, the error states, the QA. Walk me through the migration if there's one. Tell me about the tests you'll write."

Usually the S becomes an M once the founder thinks through the shipping bar.

## The Over-Sizing Failure Mode

Less common but real: marking everything L or XL. Symptoms:

- "It's a massive undertaking"
- "We'd basically be rebuilding the product"
- "It touches everything"

Push back with:

> "What's the smallest version that produces the expected value? If we cut the scope to just [smallest cohort / one persona / one data source], how long?"

Usually this collapses L into M or XL into L + follow-ups. This is also the cue to decompose the epic.

## Calibration Against the Team

Size relative to the current team, not a hypothetical future team. Update `founder-profile.md` context on team size before sizing if unclear.

- Solo founder shipping alone? Most M's become L's. Adjust.
- 3-engineer team with a senior lead? S/M/L as defined.
- Contractor-heavy team? Add 50% to every estimate — coordination overhead is real.

If `founder-profile.md` indicates a very small or solo team, surface the adjustment in the preview:

> "Adjusted effort assumes solo execution. E04 is L (6 weeks solo) rather than M (3 weeks for a 2-person team)."

## When Sizing Disagrees With Founder

If the founder says S but the epic smells like M, push back once. If they still say S, capture their reasoning in Notes and accept S — but surface the risk:

> "Sizing as S per founder judgment. If this slips past 2 weeks, revisit as M and re-score RICE (effort going S→M will cut the RICE score roughly in half)."

This is more useful than arguing. If the founder is wrong, the data will show up in the next run.

## Decomposition Criteria

An epic should be decomposed into smaller epics when any of these are true:

- Size is XL (almost always)
- Size is L AND two or more sub-capabilities could ship independently with standalone value
- Sub-scopes can be scored meaningfully differently on RICE (e.g., one sub-scope is clearly P0, another is P2)
- Dependencies wrap differently across sub-scopes (part of it blocks nothing; part of it blocks a downstream P0)

When decomposing, the original epic either becomes:
1. A tracking/parent epic that links to the sub-epics in its Notes, or
2. Is cut (`Status=Cut`) with a Note explaining decomposition into new IDs.

Usually option 2 is cleaner. Don't confuse parent-child tracking with the table structure — `epic-list.md` is flat by design.

## Sizing in Re-Runs

Effort estimates get more accurate as the team ships epics. When re-running `epic-definer`:

- Look at actual week-count for shipped epics and recalibrate T-shirt definitions if they're systematically off
- If an in-progress epic is running longer than its size implies (e.g., an M is in week 5), consider re-sizing and resurfacing RICE
- Don't retroactively re-size shipped epics — they are what they were

Capture systematic calibration drift in the refinement notes, not the epic file.