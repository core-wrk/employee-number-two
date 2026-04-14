# Prioritization Frameworks

Internal reference used by `epic-definer` in Phase 5. Default is RICE; MoSCoW is the fallback when the founder pushes back on numeric scoring.

## RICE (Default)

### Formula

```
RICE Score = (Reach × Impact × Confidence%) / Effort_weeks
```

### Inputs

**Reach (1–10)** — How many buyers or users this epic affects in the next 12 months.

- 1 = affects 1–2 design partners
- 3 = affects every paying customer in the current small cohort
- 5 = affects all buyers in a specific ICP segment
- 8 = affects every current and near-future buyer
- 10 = affects the entire addressable market

Reach is not about total TAM. It is about who this epic actually reaches in the next year given the current go-to-market.

**Impact (0.25 / 0.5 / 1 / 2 / 3)** — How meaningful the change is per affected user.

- 0.25 = minimal (small quality-of-life improvement)
- 0.5 = low (saves a few clicks or minutes)
- 1 = medium (removes a friction point in a common workflow)
- 2 = high (enables a new capability that materially changes the buyer's job)
- 3 = massive (the core reason buyers hire this product)

Most epics are 0.5 or 1. Reserve 2 and 3 for genuinely high-impact work.

**Confidence (0–100%)** — How sure you are about the Reach and Impact scores, given current evidence.

- 100% = validated by live customer data or signed design partners
- 80% = strong discovery-call signal from 3+ buyers
- 50% = educated guess based on ICP and competitive work
- 20% = pure assumption; no external evidence

Confidence is where assumptions get priced in. An epic with 20% confidence is mostly a bet — either validate first (via discovery or design-partner conversation) or accept the low RICE score.

**Effort (weeks)** — From the T-shirt size:
- S = 1
- M = 3
- L = 6
- XL = 12

### Worked Example

Epic E04: "Build CRM integration for Salesforce"
- Reach = 7 (most ICP buyers are on Salesforce)
- Impact = 2 (enables the core attribution workflow)
- Confidence = 80% (3 discovery calls explicitly named SFDC as the integration they need)
- Effort = L (6 weeks)

RICE = (7 × 2 × 0.80) / 6 = **1.87**

Epic E05: "Add dark mode toggle"
- Reach = 8 (everyone uses the app)
- Impact = 0.25 (minimal)
- Confidence = 60%
- Effort = S (1 week)

RICE = (8 × 0.25 × 0.60) / 1 = **1.20**

E04 has higher priority than E05 despite E05's lower effort — because the expected value is higher.

### Priority Buckets from RICE

After scoring every epic:

1. Sort by RICE descending
2. Top 3–5 scores → **P0** candidates
3. Next 5–7 scores → **P1**
4. Remaining scores > 0.5 → **P2**
5. Scores ≤ 0.5 → **P3** (or consider cutting)

These buckets are starting points, not rules. The founder may bump an epic's priority based on strategic reasoning (e.g., "this is a dependency for a P0 bet, so it needs to be P0 even though its RICE is lower"). Capture the reason in Notes.

### When RICE Gives the Wrong Answer

RICE is a heuristic, not a truth. It fails in predictable ways:

- **Dependencies distort scoring.** An epic that enables 3 other epics has understated Reach/Impact. Surface this in dependency mapping (Phase 7).
- **Learning-value epics score low.** Research/discovery epics have low Reach × Impact but unlock future confidence. Don't let RICE cut them; flag as "exploration" in Notes.
- **Platform epics score low.** Infrastructure, auth, deployment — often low RICE but enables everything. Treat as P0 based on strategic reasoning, not RICE alone.
- **Very high confidence × very low reach.** Sometimes a small, validated epic scores well even though it only affects 1 design partner. This is usually correct — ship it, ride the momentum.

When RICE conflicts with founder intuition, ask: "What does RICE miss here?" Usually the answer is a dependency or a strategic lever. Capture the reasoning so the decision is auditable.

## MoSCoW (Fallback)

Use MoSCoW when the founder pushes back on numeric scoring. Trade-off: less signal when you need to cut.

### Buckets

- **Must** — Shippable version doesn't exist without this. Maps to **P0**.
- **Should** — Not shippable without this in the next cycle, but not this cycle. Maps to **P1**.
- **Could** — Would matter; not urgent. Maps to **P2**.
- **Won't (this cycle)** — Explicitly deferred. Maps to **P3**.

### The "Must" Discipline

The failure mode in MoSCoW is everything becoming "Must." Enforce:

- No more than 5 "Must" epics. Mirror the P0 cap.
- Every "Must" has a one-sentence justification: "without this, [specific bet] can't succeed because [specific reason]."
- "Must" must be challenged at least once. Ask: "If we don't ship this, what specifically breaks?" If the answer is vague, it's probably a "Should."

### When to Switch Back to RICE

If the founder is stuck arguing about whether something is Must or Should, switch to RICE mid-conversation:

> "Let me score this epic on RICE real quick — sometimes the numbers help when the labels don't."

Run the RICE numbers for the disputed epics only. Usually the scores resolve the argument.

## Framework Choice in Frontmatter

The chosen framework is recorded in the file's frontmatter:

```yaml
prioritization_framework: RICE
```

or

```yaml
prioritization_framework: MoSCoW
```

This is read by `roadmap-builder` and Project 07 so they know how to interpret the priority column. Switching frameworks between runs is allowed but surface it explicitly in the preview: "Previous run used MoSCoW; switching to RICE this run."

## Anti-Patterns

- **Scoring everything at the median.** If every epic scores 1.5–2.5, the scoring is not discriminating. Push for wider spread.
- **Gaming confidence.** Founders inflate Confidence to boost favorite epics. Ask for the evidence; if it's thin, lower the score.
- **Ignoring RICE when it gives an inconvenient answer.** If the founder's favorite epic scores low, the answer is usually "validate the assumptions first" — not "override the score."
- **Scoring during enumeration.** Enumerate first, score second. Scoring mid-enumeration biases the enumeration toward things you already believe will score high.