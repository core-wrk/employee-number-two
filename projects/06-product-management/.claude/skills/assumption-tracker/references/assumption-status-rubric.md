# Assumption Status Rubric

Internal reference used by `assumption-tracker`. Defines the five valid statuses and the evidence required to transition between them.

## The Five Statuses

| Status | Meaning | Typical duration |
|---|---|---|
| **Unvalidated** | A belief with no supporting or contradicting evidence yet | Days to weeks |
| **Validating** | Active experimentation or discovery is underway | Weeks to 1 quarter |
| **Validated** | Credible evidence confirms the belief | Permanent (until contradicted) |
| **Invalidated** | Credible evidence contradicts the belief | Permanent (triggers revision) |
| **Revised** | The assumption was reworded based on new understanding | Typically transitions back to Unvalidated/Validating |

## Status Definitions in Detail

### Unvalidated

The default state for new assumptions. Means: "the founder believes this, but has no evidence beyond intuition and upstream artifacts (PRD, ICP, competitive landscape)."

- **Entry:** New assumption seeded from PRD, or surfaced during strategy conversations
- **Exit to Validating:** Active discovery or experiment underway to test the assumption
- **Exit to Validated:** Uncommon. Evidence arrived spontaneously (e.g., prospect volunteered data) — skip Validating state
- **Exit to Invalidated:** Uncommon but possible — evidence disproved the assumption before a deliberate test

### Validating

A deliberate effort is underway to test this assumption. Active discovery calls are oriented around the question, an experiment is running, a pilot is being set up, etc.

- **Entry from Unvalidated:** Founder commits to a specific validation path (e.g., "I'm going to test this by running 3 discovery calls with VP Sales Enablement buyers")
- **Entry criteria:** Source must include the validation method, not just the assumption text
- **Exit to Validated:** Evidence gathered from ≥2 independent sources all point the same direction
- **Exit to Invalidated:** Evidence from ≥1 credible source directly contradicts
- **Exit to Revised:** Evidence suggests the assumption is partially right but the framing is wrong

### Validated

Credible evidence from multiple independent sources confirms the belief.

- **Entry criteria:**
  - ≥2 independent sources (different prospects, different beta sessions, different research citations)
  - OR 1 source of very high credibility (signed design partner with usage data, published research specific to the ICP)
- **Source identifiers required:** Each validating source cited in Notes
- **No automatic expiration:** Validated status persists indefinitely, but can transition to Invalidated if new contradicting evidence arrives
- **Epic implications:** Validated assumptions de-risk linked epics — consider bumping Confidence in `epic-definer` RICE scoring

### Invalidated

Credible evidence contradicts the belief. This is the status that triggers back-pressure on shipped and in-progress epics.

- **Entry criteria:**
  - 1 source of very high credibility (signed design partner firmly rejects the assumption), OR
  - 2 independent sources both push back, OR
  - Beta/pilot usage data directly contradicts
- **Exit to Revised:** If the invalidation suggests the assumption wasn't wrong but was mis-stated (e.g., "buyers don't want X" → "buyers don't want X in the current form, but they want Y which is adjacent"). Rewrite the assumption text and set status to Revised.
- **Source identifier required:** Specific prospect slug, session ID, or data query. Vague sources rejected.
- **Back-pressure required:** On transition, cross-check Linked Epics. Any with `Status=In Progress` or `Shipped` surface as action items.

### Revised

The assumption's text has been reworded based on new understanding. Usually happens after partial invalidation — the belief wasn't wrong but was too crude.

- **Entry criteria:** Explicit rewrite of the Assumption text, with a Notes entry explaining what changed and why
- **Source required:** What triggered the revision
- **Next transition:** Usually Revised → Validating or Revised → Unvalidated — the new framing needs new evidence
- **Linked Epics preserved:** Epic links carry forward; the founder may choose to also revisit scope via `epic-definer`

## Transition Matrix

```
        From:       Unvalidated  Validating  Validated  Invalidated  Revised
To:
Unvalidated         —            rare*       rare*      no           common
Validating          common       —           rare*      no           common
Validated           possible     common      —          rare†        rare*
Invalidated         possible     common      possible‡  —            rare*
Revised             common       common      rare†      common       —
```

- `*` = unusual transition; capture reasoning in Notes
- `†` = requires strong new evidence to justify; usually means prior status was premature
- `‡` = validated → invalidated is possible when context changes (e.g., ICP sharpens, and prior validation was in a broader population)

## Evidence Credibility Tiers

Not all sources are equal. Use this tiering when applying the rubric:

### Tier 1: Highest credibility
- Signed design partner usage data
- Beta users' actual behavior (not self-reported)
- Internal experiment results (e.g., A/B test with statistical significance)
- Published research specific to the ICP

### Tier 2: High credibility
- Dated, detailed discovery call with a named, in-ICP prospect
- Waitlist form responses at scale (20+ responses)
- Qualitative interview with ≥3 in-ICP buyers

### Tier 3: Supporting credibility
- General industry research (not specific to ICP)
- Adjacent-market analogs
- Founder's prior domain experience

### Tier 4: Low credibility (weak signal only)
- Single conversation with no identifier
- Hypothetical discussions
- Advisor opinions without data

**Rule:** Validated status requires ≥2 Tier 1 or 2 sources, OR 1 Tier 1. Invalidated status requires ≥1 Tier 1 source OR ≥2 Tier 2 sources in agreement.

## Common Failure Modes

- **Premature Validated:** One prospect said yes in a sales call. That's Tier 2, and one source. Not enough for Validated; it's Validating at best.
- **Self-confirming invalidation:** The founder selectively surfaces invalidating evidence for an assumption they already wanted to kill. Surface the pattern if it's showing up — ask if the founder has also sought confirming evidence.
- **Stale Validating:** An assumption has been Validating for 90+ days with no source updates. The validation effort has stalled. Either restart, cut the assumption (revise to reflect new understanding), or move back to Unvalidated with a Notes entry.
- **Validated assumptions treated as permanent truth:** Even Validated assumptions can be invalidated when context shifts (ICP narrows, market changes). Watch for this when prior-run Validated assumptions start showing contradicting evidence.

## When Status Is Genuinely Ambiguous

Sometimes evidence is mixed — 2 prospects validate, 1 contradicts. Options:

1. **Split the assumption.** The underlying belief is probably two beliefs in one sentence. Revise into two assumptions.
2. **Narrow the scope.** Validate for a specific sub-segment of the ICP, leave Unvalidated for the rest. Revise the text to reflect the narrower scope.
3. **Stay in Validating.** Gather more evidence before transitioning.

Avoid "partially validated" as a status. It doesn't exist. Force one of the above.