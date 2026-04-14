# Capacity Calibration Guide

Internal reference used by `roadmap-builder` in Phase 3 and Phase 7. Determines how many epics fit in Now given the current team size and epic mix.

## Team-Size Baselines

| Team | Typical parallel Now epics | Total effort ceiling in Now |
|---|---|---|
| Solo founder | 1 | 1 L (6 wks) or 2 M (6 wks total) |
| 2-person team | 1–2 | 1 L + 1 M (9 wks) or 2 M |
| 3-person team | 2–3 | 1 L + 2 M (12 wks) or 3 M |
| 4+ person team | 2–4 | scales linearly; watch for coordination overhead |

These are defaults. Adjust for:

- **Seniority:** A senior-only 2-person team can sometimes run 2L in parallel. A team with 1 senior + 1 junior usually can't.
- **Full-stack vs. specialist:** Full-stack engineers can fully own an epic. Specialists (frontend-only, backend-only) require pairing — 2 specialists = 1 "full epic slot," not 2.
- **Context-switching cost:** Parallel epics add ~20% overhead. 2 in parallel is NOT 2× throughput.
- **Founder overhead:** If the founder is also running sales, fundraising, and product management, their engineering hours are unreliable. Assume 50% of stated capacity.

## Why "Now" is ~6 weeks, Not ~2 Weeks

Six weeks is long enough to ship something meaningful, short enough that the bet stays current, and matches the typical M or L epic effort. Two-week sprints are a tactical unit; they don't make strategic sense for roadmap sequencing. Quarterly plans (13 weeks) are too long — reality changes in between.

## Why Solo = 1 Epic in Parallel

Every "2 epics in parallel for a solo founder" claim has collapsed to "one epic mostly shipped, the other mostly stalled" in practice. Solo founders have sharp attention and linear capacity. Running 2 parallel engineering epics is almost always worse than running 2 sequentially.

The only exception: if one "epic" is small maintenance that can fit in background hours (fixing a critical bug, handling an urgent customer request). Capture as an Infrastructure note, not as a second parallel epic.

## Effort Math

When evaluating Now capacity, convert T-shirt sizes to weeks:

- S = 1 week
- M = 3 weeks
- L = 6 weeks
- XL = 12 weeks (don't fit XL in Now — decompose)

Sum the effort weeks of all epics in Now. Compare to team capacity × 6 weeks, with adjustments:

```
capacity_in_now = team_size_adjusted × 6 × (1 - context_switching_penalty)
```

Where `context_switching_penalty` = 0 if 1 epic in parallel, 0.2 if 2, 0.35 if 3, 0.5 if 4+.

### Example: 2-person team with 2 epics in Now

- Raw capacity: 2 engineers × 6 weeks = 12 eng-weeks
- With 20% context-switching penalty: 9.6 eng-weeks
- Two M epics (3 weeks each, 6 eng-weeks total for the team) — **fits**
- One L + one M (6 + 3 = 9 eng-weeks for the team) — **just barely fits; risky**
- Two L epics (12 eng-weeks) — **does not fit; cut one to Next**

### Example: Solo founder with 1 epic in Now

- Raw capacity: 1 × 6 × 50% founder overhead = 3 eng-weeks
- One M epic (3 weeks) — **fits**
- One L epic (6 weeks) — **does not fit in 6-week window; either promote L to Next, or tolerate 12-week Now and re-run the roadmap at week 6**

Note: a solo founder running an L epic effectively has a 12-week Now. Name this explicitly in the roadmap — don't pretend Now is 6 weeks when the math says otherwise.

## Effort Certainty Discount

Effort estimates are optimistic. Apply a discount:

- If the epic has shipped a similar effort before: × 1.0 (estimates are calibrated)
- If the epic is in a familiar domain but new capability: × 1.3
- If the epic is in an unfamiliar domain or uses new technology: × 1.8
- If the epic depends on external parties (new integration, new vendor): × 2.0

Apply the highest applicable multiplier. Founders who skip this step consistently over-scope Now.

## Capacity and the Founder's Other Obligations

Inbound marketing, outbound sales, fundraising, hiring, customer support — all compete for founder time. If the founder is full-time on product and engineering, their capacity is one engineer. If they are splitting, their capacity is 0.3–0.5 of an engineer.

Ask explicitly in Phase 3:

> "In the next 6 weeks, how much of your time is genuinely on product execution? Not strategic planning — actual shipping. Is it 40 hours a week or is it 10?"

Get a number. Apply it as the founder's engineering capacity.

## Signals That Now is Over-Scoped

During or after Phase 7 capacity reconciliation, watch for:

- Total effort in Now exceeds calculated capacity
- Multiple epics marked "In Progress" that have been stalled more than 2 weeks
- Founder expresses anxiety about shipping everything ("we just need to move faster")
- Dependencies between Now epics that can't be parallelized
- Same Now epics carried over from the prior roadmap with no progress

In any of these cases, cut the lowest-RICE epic from Now to Next. Surface the cut explicitly; don't do it silently.

## Signals That Now is Under-Scoped

Rarer but real:

- Capacity budget has 2+ weeks of slack
- No epic in Now advances the Current Bet
- Founder is spending time on non-shipping work (meetings, planning, learning)

Usually this means promoting an epic from Next to Now, or that the Current Bet is actually already being executed and the roadmap needs a new bet. Surface either interpretation.

## Capacity Changes Across Runs

When the team grows (new hire, new contractor), capacity changes. Re-run the roadmap — parallel slot count goes up, and some Next epics may promote to Now.

When the team shrinks (someone leaves, founder splits attention for fundraising), capacity shrinks. Also re-run the roadmap — demote Now epics to Next, not silently delay them.

Capacity changes are the #1 reason to re-run `roadmap-builder` off the default 4-week cadence.