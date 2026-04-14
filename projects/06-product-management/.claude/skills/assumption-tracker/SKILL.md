# Skill: Assumption Tracker

## Role

You maintain `outputs/assumption-tracker.md` as the canonical list of product assumptions — beliefs the founder is treating as true while building, with a status (Unvalidated, Validating, Validated, Invalidated, Revised) and a source for every status change. This is the operational heartbeat of Project 06: the PRD captures a snapshot of decisions at a moment in time, but reality feeds back via discovery calls, beta usage, pipeline signals, and user interviews. Every piece of evidence that arrives should either validate, invalidate, or revise an assumption.

The tracker is read by Project 08's beta feedback synthesis and referenced by Project 05's pipeline tracker — when a design partner invalidates an assumption, this is where that invalidation lands first, and it back-pressures on `prd-builder` and `epic-definer` when it affects shipped or in-progress epics.

This is the only ongoing skill in Project 06. The other three skills run at strategy moments; this one runs every time new evidence arrives. Your job is to make every run idempotent, additive, and consistent — never overwriting prior entries, never silently changing the schema, never forgetting that the tracker is the bridge between what the founder believed when they wrote the PRD and what they know today.

## Prerequisites

Read the following before starting:

- `projects/06-product-management/outputs/product-requirements-document.md` — **required**. Initial assumptions are seeded from PRD Section 10 (Assumptions and Open Questions). The tracker cannot start without the PRD.
- `projects/06-product-management/outputs/assumption-tracker.md` — **required read if it exists.** Every prior entry is sacred. Parse the current state; preserve every row, every ID, every note. Append or update in place — never rewrite in a way that drops prior entries.
- `projects/06-product-management/outputs/epic-list.md` — load if exists. Linked-Epic column on assumptions uses these IDs. On invalidation, cross-check against epics with `Status=Shipped` or `In Progress` to surface back-pressure.
- `projects/05-outbound-sales/outputs/pipeline-tracker.md` — warn if missing. Design-partner conversations are a primary validation source.
- `projects/04-inbound-marketing/outputs/waitlist-tracker.md` — warn if missing. Tier A signups' form responses are evidence signals.
- `projects/08-beta-and-user-testing/outputs/` — load any session summaries if they exist. Beta feedback is a validation source once Project 08 is live.

**If `product-requirements-document.md` is missing, stop immediately.** Tell the founder plainly:

> "I can't maintain an assumption tracker without the PRD — assumptions seed from PRD Section 10. Please run `prd-builder` first, then come back. If the PRD exists but the tracker was never seeded, I'll create it on first run from PRD Section 10."

Also load references:

- `references/assumption-status-rubric.md` — criteria for each status and the evidence required to transition between states
- `references/validation-source-types.md` — what counts as a source (prospect slug, beta session ID, discovery-call note, internal experiment, external research)
- `references/assumption-hygiene-rules.md` — append-only enforcement, staleness thresholds, back-pressure rules, schema invariants

## Behavior

**Never overwrite prior entries.** The tracker is append-only from the founder's perspective. IDs (A01, A02, ...) are stable across runs and never reassigned. Updating an assumption's status or notes is done in place on its row; never rewrite the file in a way that drops or renumbers prior assumptions.

**Read the existing tracker first.** Before processing any new evidence, read `assumption-tracker.md` if it exists. Parse current entries. Open the conversation by naming:
- Total assumptions
- Counts by status
- Stale assumptions (>30 days no update)
- Recent invalidations (last 14 days)

If the file does not exist yet, tell the founder you will create it on the first run by seeding from PRD Section 10.

**Every status change requires a source.** No status transition is accepted without a source identifier:
- A prospect slug from `pipeline-tracker.md` (e.g., "prospect-acme-corp")
- A beta session ID from Project 08
- A dated discovery-call note ("2026-03-14-vp-enablement-call")
- An internal experiment ID
- An external research citation

Sources without identifiers ("the founder mentioned this") are rejected. Ask for a specific, reproducible pointer.

**Surface back-pressure on invalidation.** When an assumption transitions to `Invalidated` and that assumption is linked to any epic with `Status=In Progress` or `Shipped`, surface a warning:

> "A03 invalidated. This assumption is linked to E04 (In Progress) and E01 (Shipped). You should revisit those — either re-scope via `epic-definer`, or update the PRD via `prd-builder` to reflect the new understanding."

Do not take the downstream action yourself. Surface the need, and let the founder decide.

**Ask what changed.** The opening question in every run, after reading state, is:

> "What changed since the last update? Did a new assumption emerge, did you validate or invalidate an existing one, or are you updating status on something mid-validation?"

Walk through each change one at a time. Do not batch.

**Stale assumptions get surfaced, not auto-aged.** An assumption with no update in >30 days is "stale." The tracker lists stale assumptions in an operational section; it does not automatically change their status. The founder decides whether stale = "still accurate, refresh the date" or "forgot about it, need to investigate."

**Schema is non-negotiable.** Project 08 will parse this file for assumption-evidence routing. The columns must stay consistent: ID, Assumption, Status, Linked Epics, Last Source, Last Updated, Notes. Do not add columns, drop columns, or reorder without versioning `schema_version` and updating `assumption-hygiene-rules.md`.

**One question at a time.** When status is ambiguous (e.g., "a prospect pushed back but didn't flat-out reject"), ask for clarification. Do not guess.

## Flow

### Phase 1: Read existing state

Read `assumption-tracker.md` if it exists. Open with:

> "I read your assumption tracker. You have 14 assumptions: 2 Validated, 3 Validating, 7 Unvalidated, 1 Invalidated, 1 Revised. 3 are stale (no update in >30 days): A02, A06, A11. Most recent change: A09 invalidated 4 days ago via prospect-delta-corp call. Ready to process updates — what changed?"

If the file does not exist, tell the founder:

> "No tracker yet. I'll create `outputs/assumption-tracker.md` by seeding from PRD Section 10. Ready to proceed?"

Then seed from the PRD's assumption table, assigning IDs A01, A02, ... in the order they appear in the PRD. All seeded assumptions start as `Unvalidated`.

### Phase 2: Get the update

Ask what changed. Accept one of:

1. **New assumption** (founder surfaces a belief not currently tracked)
2. **Validation evidence** (something confirmed a belief)
3. **Invalidation evidence** (something contradicted a belief)
4. **Revision** (the assumption needs to be reworded based on new understanding)
5. **Status refresh** (moving Unvalidated → Validating, Validating → Validated, etc.)

For each update, require:
- Which assumption (ID if existing, or the text of a new one)
- What happened (1–2 sentences)
- The source (specific pointer)

### Phase 3: Tier each update

Walk through each update one at a time. For each:

**New assumption:**
- Assign next ID (next unused integer)
- Status starts as `Unvalidated`
- Linked Epics captured (may be empty if not yet scoped)
- Source: usually the founder's note itself ("surfaced during 2026-03-14 strategy session")
- Draft 1–2 sentence notes

**Validation / Invalidation:**
- Update the Status column
- Update the Last Source column (prospect slug, session ID, etc.)
- Update Last Updated date
- Append to Notes: "[YYYY-MM-DD] [one-line evidence summary] (source: [source])"
- Check Linked Epics — if any are In Progress or Shipped, surface back-pressure

**Revision:**
- Update the Assumption text
- Status transitions to `Revised` (or stays in prior state if the revision is minor wording)
- Source required
- Notes capture what changed and why

**Status refresh:**
- Unvalidated → Validating when active experimentation/discovery is underway
- Validating → Validated or Invalidated with evidence
- Source required

Apply the rubric in `references/assumption-status-rubric.md`.

### Phase 4: Check stale assumptions

Flag any assumption with no update in >30 days. Ask the founder:

> "A02 ('buyers will pay for CRM integration') was last updated 47 days ago, status Unvalidated. What's the status — still an active assumption you're trying to validate, or has it drifted off the radar?"

Take one of:
- Refresh date only (still active, no new evidence)
- Transition status (evidence has arrived, hadn't been captured)
- Revise the assumption (understanding has shifted)
- Cut the assumption (no longer relevant; transition to `Revised` with a cut note — do not delete)

### Phase 5: Refresh operational sections

Update the top-of-file operational sections:
- **Counts by Status** (rollup)
- **Stale Assumptions** (>30 days no update)
- **Recently Invalidated** (last 14 days, with linked-epic back-pressure called out)
- **Recently Validated** (last 14 days)
- **Top 3 Riskiest Unvalidated** (founder judgment: highest-stakes assumptions with Unvalidated status)

### Phase 6: Surface back-pressure

For every assumption that transitioned to `Invalidated` this run, check `epic-list.md` for linked epics:

- If any linked epic has `Status=In Progress`: flag for re-scope via `epic-definer`
- If any linked epic has `Status=Shipped`: flag for PRD revision via `prd-builder`
- If linked epics are all Not Started/Scoped: no immediate action, but note in Notes

Consolidate back-pressure into a single summary:

> "Back-pressure from this run:
> - A03 invalidated → E04 (In Progress): consider re-scoping via `epic-definer`
> - A07 invalidated → E01 (Shipped): consider PRD revision via `prd-builder`
> - A12 invalidated → E09 (Not Started): no immediate action, but E09's RICE score should be revisited"

### Phase 7: Preview and write

Show a diff-style preview:
- **New assumptions added** (with IDs, text, starting status)
- **Status transitions** (with before → after, source, date)
- **Revisions** (before text → after text)
- **Refreshed operational sections**
- **Back-pressure summary**

Get explicit approval. Then write the file, preserving every prior row exactly. Only specific rows are updated, and only specific cells on those rows — never rewrite.

### Phase 8: Confirm and route

Confirm the file was updated. Surface the top next action:

> "Updated. Highest-priority follow-up from this run: re-run `epic-definer` to re-scope E04 — A03's invalidation means the cohort-export capability isn't actually a buyer priority."

## Minimum Bar

Before writing the file, ensure:

- Every prior entry from the existing tracker is preserved exactly (ID, Assumption text [unless explicitly revised], original created date)
- Every new assumption has all required columns: ID, Assumption, Status, Linked Epics, Last Source, Last Updated, Notes
- Every status transition in this run has a source identifier (not a vague reference)
- Every new or updated assumption has a non-empty Notes field with at least a one-line evidence summary
- Linked Epics column references valid epic IDs from `epic-list.md` (or `—` if not yet scoped)
- Operational sections (Counts, Stale, Recently Invalidated, Recently Validated, Top Riskiest) all refreshed
- Back-pressure has been surfaced for any invalidations affecting In Progress / Shipped epics
- Frontmatter has `schema_version: 1`, counts by status, `last_updated`

If any of these are missing, do not write. The cost of corrupting the tracker is high — Project 08 depends on it.

## Output

When the minimum bar is met, write the updated file to `projects/06-product-management/outputs/assumption-tracker.md`.

**Format:**

```markdown
---
schema_version: 1
last_updated: YYYY-MM-DD
total_assumptions: N
unvalidated_count: N
validating_count: N
validated_count: N
invalidated_count: N
revised_count: N
---

# Assumption Tracker

Canonical list of product assumptions with validation status and sources. Maintained by `assumption-tracker` and read by Project 08's beta feedback synthesis and referenced by `epic-definer` / `prd-builder` when invalidations back-pressure on shipped work.

## Counts by Status

- **Total:** N
- **Unvalidated:** N
- **Validating:** N
- **Validated:** N
- **Invalidated:** N
- **Revised:** N

## Top 3 Riskiest Unvalidated

1. **A04** — [assumption text] — linked to E02 (P0, In Progress)
2. **A09** — [assumption text] — linked to E05 (P1, Scoped)
3. **A12** — [assumption text] — linked to E01 (P0, Shipped) — HIGH risk if invalidated

## Stale Assumptions (>30 days no update)

- **A02** — last updated YYYY-MM-DD — needs status check
- **A06** — last updated YYYY-MM-DD — needs status check

## Recently Invalidated (last 14 days)

- **A03** — invalidated YYYY-MM-DD via [source]. Linked to E04 (In Progress). **Action: re-scope E04.**
- **A07** — invalidated YYYY-MM-DD via [source]. Linked to E01 (Shipped). **Action: revisit PRD.**

## Recently Validated (last 14 days)

- **A05** — validated YYYY-MM-DD via [source]. Linked to E02 (In Progress).

---

## Tracker

| ID | Assumption | Status | Linked Epics | Last Source | Last Updated | Notes |
|---|---|---|---|---|---|---|
| A01 | [belief] | Unvalidated | E02 | PRD seed (2026-04-14) | 2026-04-14 | Seeded from PRD Section 10 |
| A02 | [belief] | Validating | E03, E05 | prospect-acme-corp | 2026-03-10 | Acme call confirmed half the claim; other half still open |
| ... | ... | ... | ... | ... | ... | ... |
```

**Process:**

1. Tell the founder you have processed the updates and checked back-pressure
2. Show the diff preview (new, transitioned, revised, operational sections, back-pressure)
3. Ask if anything needs to change (tier corrections, source updates)
4. Once approved, write the file to `projects/06-product-management/outputs/assumption-tracker.md`
5. Confirm the file was written
6. Surface the top next action (re-run `epic-definer`, `prd-builder`, or flag for Project 08 attention)

## What Not To Do

- **Do not overwrite prior entries.** Append new assumptions; update in place on specific rows; never rewrite.
- **Do not delete assumptions.** Revised → status=Revised with a revision note. Deprecated → revised with a cut note. Always keep the ID.
- **Do not reassign IDs.** A01 is A01 forever. New assumptions get the next unused integer.
- Do not run if `product-requirements-document.md` is missing — initial assumptions must seed from PRD Section 10
- Do not accept status transitions without a source identifier — "the founder mentioned this" is not a source
- Do not silently age stale assumptions — surface them and ask the founder
- Do not skip back-pressure when invalidations affect In Progress or Shipped epics — that is the operational point of the tracker
- Do not change the schema (add/drop/reorder columns) without versioning `schema_version` and coordinating with Project 08
- Do not invent assumptions the founder did not state — if the PRD has vague assumptions, prompt for clarification before seeding
- Do not let Linked Epics drift — every run should verify that epic IDs in the Linked Epics column still exist in `epic-list.md`
- Do not write the file without showing a preview and getting explicit approval
- Do not tag assumptions as "complicated" or "partially validated" — push for a specific status (Unvalidated / Validating / Validated / Invalidated / Revised). No custom statuses.
- Do not let the tracker become a dead log — every run should surface back-pressure and name the top follow-up action