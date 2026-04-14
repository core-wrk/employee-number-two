# Epic Template — Canonical Schema

Internal reference used by `epic-definer`. Defines the fixed schema of `outputs/epic-list.md`. Downstream parsers (Project 07's `epic-requirements-builder`) rely on these columns and enums — do not change without versioning `schema_version` in the frontmatter.

## Frontmatter (required)

```yaml
---
schema_version: 1
prioritization_framework: RICE | MoSCoW
generated_from: projects/06-product-management/outputs/product-requirements-document.md
last_updated: YYYY-MM-DD
---
```

## Operational Sections (top of file, refresh every run)

### Counts by Status

Rollup of all epics by status. Total must equal the row count in the backlog table.

### Next Up This Cycle

1–3 epics the founder is committing to start next. Each with a one-line rationale. This is the only section that accepts founder judgment rather than computed output.

### Blocked

Every epic with `Status=Blocked`. The blocker must be named explicitly — "waiting on integration partner," "needs design partner #3 to come online," etc.

### Recently Shipped (last 60 days)

Epics with `Status=Shipped` and `shipped_date` within 60 days of `last_updated`. Older shipped epics roll off into the main table only.

## Backlog Table (fixed columns)

| Column | Type | Notes |
|---|---|---|
| ID | string | `E01`, `E02`, ... stable across runs, never reassigned |
| Title | string | Active voice, short (≤8 words) |
| Problem | string | One-line problem statement |
| Priority | enum | `P0` / `P1` / `P2` / `P3` |
| RICE Score | number | (Reach × Impact × Confidence%) / Effort-weeks. Shown as "—" if framework=MoSCoW |
| Effort | enum | `S` / `M` / `L` / `XL` |
| Status | enum | `Not Started` / `Scoped` / `In Progress` / `Blocked` / `Shipped` / `Cut` |
| Dependencies | string | Comma-separated epic IDs, or `—` for none |
| Owner | string | Founder, contractor name, or future role |
| Linked User Stories | string | Comma-separated story IDs from PRD Section 7 |

## Enum Definitions

### Priority
- **P0** — Must ship for the current bet to succeed. ≤5 at a time.
- **P1** — Should ship in the current or next cycle. ≤8 at a time.
- **P2** — Could ship; would matter but not urgent.
- **P3** — Longer-horizon; often depends on learning from P0/P1 first.

### Effort
- **S** — ~1 week for a small team
- **M** — ~3 weeks
- **L** — ~6 weeks
- **XL** — ~12 weeks (should probably be decomposed)

### Status
- **Not Started** — No work begun; epic is in the backlog
- **Scoped** — Detailed requirements exist (Project 07 has processed); ready to work
- **In Progress** — Active engineering work
- **Blocked** — Work paused on external dependency (name the blocker)
- **Shipped** — Acceptance criteria met, in production
- **Cut** — No longer in scope; kept in tracker for historical reference. Include cut reason in Notes.

## Epic Details Section (per epic, below the table)

### Required sub-sections

**Problem** — 2–3 sentences. Why this epic exists. Who feels the gap. The "before" state.

**Acceptance** — Bulleted list of user-facing behaviors that must work for this epic to transition to `Shipped`. Each criterion is testable.

**Open Questions** — Things the founder/engineer needs to resolve before or during the work. Move to `assumption-tracker.md` if they become long-lived.

**Linked Assumptions** — IDs from `outputs/assumption-tracker.md` that this epic depends on. Format: `A03, A07` or `—` if none.

**Notes** — Free-form. Design partner feedback. Discarded approaches. Anything the future reader should know.

### Optional sub-sections

**Cut Reason** — If `Status=Cut`, explain why. Example: "Validated that buyers don't actually need cohort export — see A14 invalidation."

**Shipped Date** — If `Status=Shipped`, date in `YYYY-MM-DD`.

## ID Assignment Rules

1. IDs are permanent. `E01` is `E01` forever.
2. New epics get the next unused integer. If the last ID is `E12`, the next is `E13`.
3. Cut epics keep their ID; the ID is never recycled.
4. Zero-padding is 2 digits up to `E99`; 3 digits from `E100` onwards.

## RICE Score Formula

```
RICE = (Reach × Impact × Confidence%) / Effort_weeks
```

Where:
- **Reach** = 1–10 (how many buyers/users affected in next 12 months)
- **Impact** = 0.25 / 0.5 / 1 / 2 / 3 (minimal / low / medium / high / massive)
- **Confidence** = 0–100% (how sure about Reach and Impact)
- **Effort_weeks** = S=1, M=3, L=6, XL=12

Example: Reach=5, Impact=2, Confidence=70%, Effort=M (3 weeks) → (5 × 2 × 0.7) / 3 = **2.33**

Scores are comparative, not absolute. The top 3–5 by score are P0 candidates; the next 5–7 are P1; the rest are P2/P3.

## MoSCoW Fallback

If the founder pushes back on numeric scoring, use MoSCoW:
- **Must** — maps to P0
- **Should** — maps to P1
- **Could** — maps to P2
- **Won't (this cycle)** — maps to P3

`RICE Score` column becomes `—` for all rows. Note the framework choice in frontmatter.

## Linked User Story Format

IDs come from PRD Section 7. Format: `US-<pillar#>-<story#>`. Example: `US-1-3, US-2-1`.

Every P0/P1 epic must have at least 1 linked story. P2/P3 can be exploratory and may have no linked stories yet (but `Open Questions` should explain why).