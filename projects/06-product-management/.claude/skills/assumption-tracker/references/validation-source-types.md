# Validation Source Types

Internal reference used by `assumption-tracker`. Every status transition requires a source identifier. This file enumerates the valid source types and the identifier format for each.

## Why Identifiers Matter

"A prospect validated this" is not a source. "Which prospect? When? What did they say?" is. Without a reproducible pointer, status changes rot — six months later, nobody remembers what the evidence was, and the validation collapses.

The rule: **if another person could not follow the source pointer and verify the evidence, it is not a valid source.**

## Valid Source Types

### 1. Prospect Slug

Format: `prospect-<slug>`

Reference to a specific prospect in `projects/05-outbound-sales/outputs/prospect-list.md`. The slug matches the entry in the prospect list.

**Example:** `prospect-acme-corp`, `prospect-delta-insurance`, `prospect-evergreen-saas`

**Valid evidence:**
- A discovery call note with a named date
- A pipeline-stage transition (e.g., prospect moved from "Discovery" to "Design Partner")
- A specific quote from the prospect captured in the pipeline notes

When citing, always pair the slug with a date and 1-line summary:

> Source: prospect-acme-corp — 2026-03-14 discovery call. "VP Enablement explicitly said cohort attribution was their top unmet need."

### 2. Beta Session ID

Format: `beta-<YYYY-MM-DD>-<participant-slug>`

Reference to a beta session in `projects/08-beta-and-user-testing/outputs/`. IDs are assigned by Project 08's beta skills.

**Example:** `beta-2026-03-22-rvp-jenna`, `beta-2026-04-01-ae-marco`

**Valid evidence:**
- Beta session recording or summary
- Usage log entries tied to the session
- Post-session survey responses

When citing, pair with the specific observation:

> Source: beta-2026-03-22-rvp-jenna — watched Jenna try to export cohort data and abandon after 3 attempts. Invalidates A07 (buyers will self-serve cohort exports).

### 3. Discovery Call Note

Format: `discovery-<YYYY-MM-DD>-<topic-slug>`

Used when the conversation wasn't with a tracked prospect (e.g., advisor conversation, friendly operator, peer founder). Recorded in the founder's notes system.

**Example:** `discovery-2026-03-14-advisor-sales-enablement`, `discovery-2026-03-20-friendly-rvp`

**Valid evidence:**
- Dated notes (in any system — Notion, Google Doc, etc.) that the founder can retrieve
- 1–2 direct quotes captured in the notes

**Weaker than prospect slug or beta session** because the source is less anchored. Use sparingly.

### 4. Internal Experiment ID

Format: `experiment-<YYYY-MM-DD>-<slug>`

Reference to an internal experiment (A/B test, landing page test, pricing-page variation, etc.) with a documented result.

**Example:** `experiment-2026-02-14-pricing-page-tier-test`

**Valid evidence:**
- Experiment design doc
- Results summary with a dated snapshot of the data
- Statistical significance noted (or noted as "directional only")

### 5. External Research Citation

Format: `research-<publication>-<year>` or `research-<url-fragment>`

Reference to published research specific enough to cite.

**Example:** `research-gartner-crm-survey-2025`, `research-first-round-state-of-founders-2026`

**Valid evidence:**
- Citation with URL or exact publication reference
- Specific data point quoted in Notes

**Weaker than first-party evidence** because the sample isn't your ICP. Usable for Tier 3 credibility only.

### 6. Usage Data Query

Format: `usage-<date>-<metric-slug>`

Reference to a specific query run against your product analytics or database.

**Example:** `usage-2026-04-01-activation-by-segment`, `usage-2026-03-28-cohort-export-attempts`

**Valid evidence:**
- The query itself (SQL, Amplitude/Mixpanel query, etc.)
- A snapshot of the result

Only applicable once the product has enough users for data to be meaningful.

### 7. Founder Note (Strategy Session)

Format: `strategy-<YYYY-MM-DD>`

Used **only** for new assumption surfacing — when a strategy session identifies a belief the founder is holding that wasn't in the PRD. Not a valid source for Validated or Invalidated status.

**Example:** `strategy-2026-04-14`

**Valid for:** Creating new Unvalidated assumptions
**Not valid for:** Validation or invalidation (external evidence required)

## Invalid Sources (Always Reject)

Push back if the founder cites any of these as a status transition source:

- "A prospect said"
- "The market feels like"
- "I've been thinking about this"
- "An advisor mentioned"  (unless formalized as a dated `discovery-*` note)
- "I read somewhere that"  (requires a citation)
- "Everyone knows"
- "Industry wisdom"
- Vague references to multiple conversations without specific pointers

For each, ask:
- Which specific person?
- Which specific date?
- Where is that written down so a future reader could find it?

If the answer is unclear, the source is not valid. Either:
1. The founder documents the conversation now (creates a `discovery-*` note)
2. The status transition doesn't happen

## Multiple Sources for One Transition

If multiple sources support the same transition, list all in the Last Source field (comma-separated) and summarize in Notes:

> Last Source: `prospect-acme-corp, prospect-delta-insurance, beta-2026-03-22-rvp-jenna`
>
> Notes: 2026-04-12 — Three independent sources confirmed the activation flow is too slow. Acme VP Sales noted "days not minutes," Delta's AE said "I gave up trying," and Jenna's beta session had a 4-minute activation that she described as "painful." Validates A09.

## When the Source Changes Over Time

Some assumptions accumulate evidence. The Last Source field is the **most recent** source, but Notes should retain the history:

```
Last Source: beta-2026-04-01-ae-marco
Notes:
- 2026-03-10 — prospect-acme-corp Stage 1 discovery (weak signal, Validating)
- 2026-03-22 — beta-2026-03-22-rvp-jenna confirmed workflow (Validating)
- 2026-04-01 — beta-2026-04-01-ae-marco confirmed workflow and reported high value (Validated)
```

This pattern is the append-only log and preserves traceability.