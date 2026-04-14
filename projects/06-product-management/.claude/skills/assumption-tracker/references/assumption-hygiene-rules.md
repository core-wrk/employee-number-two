# Assumption Hygiene Rules

Internal reference used by `assumption-tracker`. Enforces the invariants that keep the tracker usable across months of operation and cross-project reads.

## Rule 1: Append-Only (from the founder's perspective)

The tracker is append-only. Operations are limited to:

1. **Add a new assumption** — gets the next unused ID
2. **Update specific cells on an existing row** — Status, Last Source, Last Updated, Notes
3. **Revise the Assumption text** — only when transitioning to Status=Revised, with explicit reasoning in Notes
4. **Refresh operational sections** at top of file

Never:
- Renumber IDs
- Delete rows
- Silently change Assumption text without transitioning to Revised
- Remove Linked Epic references without capturing in Notes
- Rewrite the file from scratch based on the current conversation

If a prior assumption is genuinely no longer relevant, the path is:

> Status → Revised
> Assumption text → "[DEPRECATED — originally: [old text]]. No longer tracked because [reason]."
> Notes → append dated cut note

## Rule 2: ID Stability

- A01 is A01 forever
- New assumptions get the next unused integer (if last is A12, next is A13)
- Cut / deprecated assumptions keep their ID
- Zero-padding: 2 digits up to A99; 3 digits from A100

## Rule 3: Schema Invariants

The table columns are fixed:

1. ID
2. Assumption
3. Status
4. Linked Epics
5. Last Source
6. Last Updated
7. Notes

No columns may be added, removed, or reordered without:

1. Bumping `schema_version` in frontmatter (1 → 2)
2. Coordinating with Project 08's beta feedback synthesis (which parses this file)
3. Documenting the change in `_dev/project-refinement-notes/06-product-management.md`

Enum values for Status are fixed: `Unvalidated`, `Validating`, `Validated`, `Invalidated`, `Revised`. No other values are valid.

Linked Epics format is comma-separated epic IDs (E01, E03) or `—` for none. No other formats.

## Rule 4: Staleness Threshold

- **30 days** since Last Updated → surface in "Stale Assumptions" operational section
- **60 days** since Last Updated for Validating status → surface as "stalled validation"; ask founder to restart or revise
- **90 days** since Last Updated for any Unvalidated/Validating → surface as "abandoned"; ask founder to either restart, cut (revise to deprecated), or refresh the date

Staleness is a surfacing signal, never an automatic state change. The founder always decides.

## Rule 5: Back-Pressure Is Mandatory on Invalidation

When an assumption transitions to `Invalidated`:

1. Check every epic ID in Linked Epics
2. For each epic, look up current status in `epic-list.md`
3. For any epic with `Status = In Progress` or `Shipped`, generate a back-pressure line in the operational section
4. Name the specific follow-up action:
   - In Progress → "re-scope via `epic-definer`"
   - Shipped → "revisit PRD via `prd-builder`"

This is not optional. The operational point of the tracker is surfacing these moments.

## Rule 6: Source Identifier Required for Every Transition

Every row-level change in Status or Assumption text must include a Last Source that is a valid source type (see `validation-source-types.md`). Exceptions:

- Initial PRD seed (source: `strategy-<PRD-date>`)
- Founder-surfaced new assumption at a strategy session (source: `strategy-<YYYY-MM-DD>`)

No other exceptions. If the source is invalid or vague, the transition is rejected until a valid source is captured.

## Rule 7: Notes Are Append-Only Within a Row

The Notes cell for an assumption grows over time as evidence accumulates. Rule:

- Every update to Status or Assumption appends a dated line to Notes
- Prior Notes lines are never removed or rewritten
- Format: `[YYYY-MM-DD] [one-line update] (source: [source identifier])`

Example:

```
[2026-04-14] Seeded from PRD Section 10. (source: strategy-2026-04-14)
[2026-03-10] Weak signal from discovery call; moving to Validating. (source: prospect-acme-corp)
[2026-03-22] Beta user confirmed; moving closer to Validated. (source: beta-2026-03-22-rvp-jenna)
[2026-04-01] Second beta user confirmed; transitioned to Validated. (source: beta-2026-04-01-ae-marco)
```

Never collapse the history. Future readers depend on the trail.

## Rule 8: Linked Epics Reference Integrity

On every run, verify that every epic ID in the Linked Epics column still exists in `epic-list.md`. If an epic has been cut and its ID removed (which shouldn't happen — cut epics keep their IDs with `Status=Cut`), surface the discrepancy.

If an epic has `Status=Cut`, the assumption's Linked Epics entry is still valid for historical reference. Do not remove.

## Rule 9: Operational Sections Refresh Every Run

The top-of-file operational sections must be fully recomputed every run:

- Counts by Status
- Top 3 Riskiest Unvalidated (requires founder judgment; surface and confirm)
- Stale Assumptions (computed from dates)
- Recently Invalidated (last 14 days)
- Recently Validated (last 14 days)

Never leave these sections stale across a run. If no changes happened to them, still update `last_updated` and confirm the counts.

## Rule 10: Schema Version Is Load-Bearing

The `schema_version` in frontmatter is the contract with downstream parsers (Project 08). Do not change column definitions, enum values, or the operational section structure without bumping the version AND updating:

1. `references/assumption-hygiene-rules.md` (this file) — document the schema change
2. `_dev/project-refinement-notes/06-product-management.md` — explain why
3. Any Project 08 skill that reads this file

## Rule 11: No "Partially Validated" or "It's Complicated"

The five statuses are exhaustive. Ambiguity means one of:

1. The assumption is really two assumptions — split it
2. The assumption needs narrowing — revise to a narrower scope
3. Evidence is insufficient — keep status at Unvalidated or Validating

Reject custom statuses ("Partially Validated," "Mostly Right," "TBD"). Force a decision.

## Rule 12: Context for Future Re-runs

Every run should read this file as if the previous run happened 6 months ago. That means:

- Notes must be readable without the conversation that created them
- Source identifiers must be self-contained (don't rely on "you know which prospect I mean")
- Operational sections tell the story of what happened since the last run

If a run's output doesn't stand on its own in 6 months, the hygiene failed.