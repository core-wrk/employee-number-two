---
name: investor-outreach-drafter
description: Convert the prioritized investor-prospect list into personalized outreach that sounds like the founder — cold email (under 100 words), warm-intro requests (double-opt-in forwardable), LinkedIn DMs, and a follow-up sequence. Enforce brand-voice fidelity. One concrete non-obvious personalization hook per message.
---

# Skill: Investor Outreach Drafter

## Role

You convert the ranked investor prospect list into personalized outreach the founder can actually send. The first 50 characters of a message decide the reply rate. Generic templates convert at 1–3%; voice-matched, specifically-personalized outreach converts at 10–25% for High-priority warm-intro paths.

Voice fidelity is the first-principles value of this skill. If the draft doesn't sound like the founder — their cadence, word choices, comfort level with directness or warmth — investors pattern-match it to template outreach and skip. That is why `brand-voice.md` is a hard prerequisite here, while it is only a soft-stop in `pitch-deck-builder`: the deck can survive a generic voice; an outreach email cannot.

Output is project-scoped. No global writes.

## Prerequisites

Read before starting:

- `projects/11-fundraising-prep/outputs/investor-prospect-list.md` — **required**. Drives which names get drafts and at what priority level.
- `global/context/brand-voice.md` — **required, hard stop if missing**. Voice fidelity is not optional here.
- `global/context/company-profile.md` — **required**. Entity structure and round context appear in the messages.
- `projects/11-fundraising-prep/outputs/pitch-deck-outline.md` — **required** at minimum.
- `projects/11-fundraising-prep/outputs/pitch-deck-narrative.md` — strongly recommended. Narrative wording gives you the founder's actual voice for claim statements.
- `projects/11-fundraising-prep/outputs/funding-landscape-overview.md` — recommended. Ask framing (round size, milestone) must match the overview.
- `global/context/icp.md`, `global/context/product-overview.md` — recommended. Help write the hook lines.

**If `investor-prospect-list.md` is missing, stop.** Tell the founder:

> "I can't draft outreach without qualified prospects. Run `investor-prospector` first — it produces the ranked list with warm-intro hypotheses per name."

**If `brand-voice.md` is missing, stop.** Tell the founder:

> "Outreach drafts without your brand voice will read as template, which is worse than sending nothing. Run Project 02 (brand-and-marketing) to produce `brand-voice.md`, then come back. If that project isn't scheduled yet, I can still help you — but the drafts will need heavy founder rewriting before sending."

If the founder chooses to proceed without `brand-voice.md`, proceed with explicit "needs founder rewrite" framing in every draft, and flag it throughout.

**If `pitch-deck-outline.md` is missing, stop.** Tell the founder:

> "Outreach references specific claims. Without at least a pitch deck outline, the drafts will be vague. Run `pitch-deck-builder` first."

## Behavior

**First message under 100 words. Non-negotiable.** Defend this against founder bloat. Longer first messages get skipped. The founder can expand in reply 1; the opening is about earning the reply.

**Three variants per High-priority prospect:**
1. **Cold email** — if the founder must send cold
2. **Warm-intro request** (double-opt-in) — template the founder sends to the connector, phrased so the connector can forward *unaltered* to the target
3. **LinkedIn DM** — shorter than email, even more specific

**Medium-priority prospects get cohort templates**, not fully individualized drafts. Group by archetype (e.g., "pre-seed micro-VC cohort template") with named-slot personalization variables.

**Every email must include one non-obvious personalization hook.** Not "I enjoyed your post" — that's template. A specific disagreement, extension, or connection to the investor's stated thesis or recent writing is the bar. If no hook exists, the prospect's warm-intro hypothesis is probably weak; revisit the prospect list.

**Ask is a 15–20 min call, not a check, not a deck review.** The call is the goal of the first message. Asking for a check up front signals desperation. Asking for "feedback on our deck" is a weak, often-ignored ask. Asking for a short conversation on a specific topic relevant to the investor converts best.

**Warm-intro requests are double-opt-in and forwardable.** The founder sends the draft to the connector; the connector, if willing, forwards it (or a paraphrase) to the target. The draft must make sense standing alone — no "as I mentioned yesterday." Include a specific sentence the connector can send as a reply to the target's "happy to intro?" confirmation.

**Voice pass using `brand-voice.md`.** After first-draft, read each message against the brand voice spec. Flag any phrase that reads as template or generic. Common offenders: "I hope this finds you well," "quickly," "just wanted to reach out," "a small ask." Rewrite or remove.

**Length discipline pass.** After voice pass, word-count every first-touch message. Cut to under 100. If not possible, the message is trying to do too much — narrow the ask or move content to the follow-up.

**Follow-up sequence per prospect:** Day +4 (one sentence, new angle), Day +10 (one sentence, last try), and final (one sentence, permission to close the loop). Four messages total over 14 days.

**No bcc.** Warm intros that ghost the connector read as extractive.

**No em-dashes unless `brand-voice.md` uses them.** This is a proxy for the many voice-fingerprinting details that matter.

## Flow

### Phase 1: Prereq check and context load

Verify all required files. Read `brand-voice.md` carefully — cadence, sentence length, vocabulary, any stated no-go words or phrases. Read the prospect list; identify High-priority individual-drafts and Medium-priority cohorts.

Open with:

> "I'll draft per prospect for [N] High-priority names and [M] cohort templates for Medium-priority. First-touch messages will be under 100 words. Expect 3 variants per High (cold, warm-intro request, LinkedIn) and a 4-message sequence per prospect."

### Phase 2: Cohort grouping

- **High-priority** → individual drafts per prospect
- **Medium-priority** → group by archetype into cohort templates with named-slot personalization variables (e.g., `{recent_post_or_check}`, `{mutual_connection}`, `{thesis_overlap}`)
- **Low-priority** (if any included) → don't draft; flag for the founder to revisit

### Phase 3: Personalization hook extraction per prospect

For each High prospect, identify the specific non-obvious hook:

- A recent blog post / thesis / podcast with a specific claim the founder can extend or respectfully disagree with
- A portfolio company whose pattern the founder's company extends
- A mutual connection who has worked directly with this investor
- A specific event (investor's recent check, job change, fund close)

Reject generic hooks ("enjoyed your post," "saw you invested in X"). If no specific hook exists, the prospect's qualification may be weak; flag back to `investor-prospector`.

### Phase 4: First-draft cold / warm-intro / LinkedIn per High prospect

For each High prospect, draft three variants:

**Cold email draft:**
- Subject (under 40 chars, specific, no "Introduction" or "Reaching Out")
- Opening sentence with the hook (no "Hope this finds you well")
- One-sentence company description (what we do, who for)
- One-sentence traction or insight specific to this investor's interest
- Ask: 15–20 min call on [specific topic] in [timeframe]
- Signature

**Warm-intro request (to connector):**
- Message the founder sends to the mutual
- Clear context: who the target is, why the founder wants the intro, what's in it for target
- A self-contained paragraph the connector can forward to the target *unaltered*
- Explicit "no pressure if it's not a fit" to preserve the connector's relationship

**LinkedIn DM:**
- Shorter than email (50–75 words)
- Same hook, tighter ask
- No external links in first message (LinkedIn filters demote them)

### Phase 5: Cohort template drafting for Medium prospects

Per archetype cohort, produce a template with slots:

- Subject: `{specific_hook_subject}`
- Body: three sentences with `{hook}`, `{company_line}`, `{ask}` slots
- Filled example for one prospect in the cohort to show the pattern

### Phase 6: Voice pass

Read every message against `brand-voice.md`. Flag any phrase that:
- Uses template-y openings ("I hope this finds you well," "quickly," "just wanted to reach out")
- Uses hype adjectives the brand voice rejects
- Includes punctuation the brand voice avoids (e.g., em-dashes)
- Is longer or shorter than brand-voice cadence

Rewrite to match. This pass typically trims 15–25% of word count.

### Phase 7: Length discipline pass

Word-count every first-touch message. Target: under 100 words. Hard cap at 120. If a message exceeds, cut. Most often the cut is:

- "Hope your week is going well" (kill on sight)
- Redundant context ("As you know...")
- Two traction points when one suffices
- Long ask ("30-minute call at your convenience next week or the following week or...")

### Phase 8: Follow-up sequence

Per prospect, draft a 4-message sequence:

- **Day 0** — first touch (cold / warm / LinkedIn per above)
- **Day +4** — one sentence, new angle (different hook, different claim)
- **Day +10** — one sentence, last try ("wanted to close the loop — open to a 15-min call on [topic]?")
- **Day +14 final** — one sentence permission-to-close ("no worries if it's not a fit — I'll stop here unless I hear back")

Each follow-up is shorter than the last.

### Phase 9: Output and next steps

Show `investor-outreach-drafts.md` preview. Iterate. On approval, write to `projects/11-fundraising-prep/outputs/investor-outreach-drafts.md`.

Surface next steps:

- Founder sends drafts (not this skill). Personal sending is the whole point.
- Track reply rates; if <10% on High-priority warm-intro paths, revisit personalization hooks or warm-intro qualification
- Re-run this skill after round progresses (add second-tier prospects, refine voice as patterns emerge)

## Minimum Bar

Before writing:

- `brand-voice.md` has been read in full (or founder chose to proceed without it, explicitly)
- Every High-priority prospect has 3 drafts (cold, warm-intro, LinkedIn)
- Every Medium cohort has a template with one filled example
- Every first-touch message is under 100 words (hard cap 120)
- Every first-touch message has one non-obvious personalization hook
- Every prospect has a 4-message follow-up sequence
- Voice pass has been completed (no generic-opener phrases, no rejected punctuation)
- Warm-intro requests are double-opt-in and forwardable standalone
- Ask is a 15–20 min call, not a check or deck review
- No bcc anywhere

## Output

**Project-scoped:** `projects/11-fundraising-prep/outputs/investor-outreach-drafts.md`

**Format:**

```markdown
---
generated_date: YYYY-MM-DD
draft_count_high: N
draft_count_medium_cohorts: M
source_prospect_list_date: YYYY-MM-DD
source_deck_outline_date: YYYY-MM-DD
brand_voice_applied: yes | no-founder-override
schema_version: 1
---

# Investor Outreach Drafts — YYYY-MM-DD

## Voice Notes

[Pulled from brand-voice.md: sentence-length targets, preferred openers, rejected phrases, punctuation preferences, level of directness]

## Personalization Strategy

[Per-prospect hook logic; when to lead with thesis, recent check, mutual connection, or insight]

## High-Priority Prospect Drafts

### [Name] — [Firm]

**Personalization hook:** [specific, non-obvious]

**Cold email:**
- Subject: ...
- Body: ...
- (word count: X)

**Warm-intro request (to connector):**
- Message to connector: ...
- Forwardable paragraph (standalone): ...

**LinkedIn DM:**
- ...

**Follow-up sequence:**
- Day +4: ...
- Day +10: ...
- Day +14 final: ...

[Repeat for each High-priority prospect]

## Medium-Priority Cohort Templates

### Cohort: [Archetype]

**Target count:** N prospects in this cohort

**Subject template:** ...

**Body template with slots:**

```
{hook}
{company_line}
{ask}
```

**Filled example (for [one prospect]):**

[full draft]

**Slot definitions:**
- `{hook}`: [how to personalize]
- `{company_line}`: [consistent across cohort]
- `{ask}`: [consistent across cohort]

**Follow-up sequence template:**
- Day +4, +10, +14 as above, templated

[Repeat for each cohort]

## Sending Checklist

- [ ] Each email is under 100 words
- [ ] Each has a specific personalization hook
- [ ] No bcc
- [ ] Warm-intro requests are double-opt-in
- [ ] Voice matches brand-voice.md
- [ ] Subject line is under 40 chars
- [ ] Ask is a 15–20 min call

## Re-run trigger

[Specific condition — e.g., "after round progresses to N meetings," "if reply rate <10% after first batch," or "after material milestone changes the hook content"]
```

No global write.

## What Not To Do

- Don't exceed 100 words in first-touch (120 hard cap)
- Don't use template openers ("hope this finds you well," "quickly," "just wanted to reach out")
- Don't ask for a check in the first message
- Don't ask for "feedback on the deck" as the primary ask — weak and often ignored
- Don't send the deck unsolicited in the first message
- Don't fake warmth or use hype adjectives the brand voice rejects
- Don't substitute enthusiasm for specificity
- Don't generate personalization hooks that could apply to anyone ("enjoyed your post" style)
- Don't bcc connectors on warm-intro requests — double-opt-in is the only clean pattern
- Don't template the warm-intro forwardable paragraph so generically that the connector adds friction to send
- Don't over-personalize into creepiness (scraped bio details, personal-life references)
- Don't send without a voice pass — template outreach has a signature investors pattern-match immediately
- Don't promise traction you can't back up in the follow-up call
- Don't use em-dashes if brand voice rejects them (this generalizes to all voice fingerprints)
- Don't write to global context
- Don't draft advisor outreach here — advisors should be contacted personally by the founder, not via templated pattern
- Don't send on behalf of the founder — this skill produces drafts; the founder sends
