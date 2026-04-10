# Content Calendar Template

This is an internal reference for the `content-strategist` skill. It is the structural template for the `content-calendar.md` output file. **Do not show this document to the founder.** Use it as the canonical structure for the file you write.

---

## Why The Calendar Is Structured This Way

A content calendar fails if it is just a list of dates and topics. It needs to make four things visible at a glance:

1. **Pillar coverage** — which messaging pillar is being served by which entry. If a pillar is missing, the calendar is off-strategy.
2. **Channel cadence** — does the calendar match the cadence from `marketing-channel-strategy.md`? Over- or under-publishing on a channel signals a strategy mismatch.
3. **Capacity feasibility** — can the founder actually do all this in their stated weekly hours? If not, the calendar is wishful.
4. **Repetition** — does each pillar appear multiple times across formats? If a pillar appears once, the founder is under-repeating.

The template below is structured to surface all four. Do not omit sections.

---

## Section Order

1. **Title** — `# Content Calendar`
2. **Period** — Date range and duration
3. **Pillars in Rotation** — Pulled from `messaging-framework.md`
4. **Capacity Budget** — Available vs. used
5. **Calendar table** — The main artifact
6. **Repetition Map** — Pillar count across formats
7. **Production Workflow** — Which writer skill produces each entry type
8. **Notes for Future Re-runs** — How to revisit and update this file

---

## Calendar Table Schema

The table is the load-bearing part of the file. Use this exact column structure so the calendar is consistent across re-runs and so it can be compared week-to-week:

| Column | Type | Notes |
|---|---|---|
| Week | integer | 1, 2, 3, ... — anchors the entry to a specific week |
| Date | YYYY-MM-DD | Specific date if known; otherwise empty and filled in at production time |
| Channel | string | LinkedIn, Blog, Reddit, YouTube, Tech Report — match channel names from `marketing-channel-strategy.md` |
| Format | string | Text post, Document carousel, Long-form, Reply, Talking head video, Research report, etc. |
| Topic | string | The specific angle, not a category. "Why ramp time is a CRO problem" not "ramp time" |
| Pillar | string | Pillar name from `messaging-framework.md`; or "Founder POV" / "Industry observation" if not pillar-anchored |
| Status | enum | Planned / Drafted / Scheduled / Published / Skipped — starts as "Planned" |

Sort the table by Week, then by Date within a week. Group rows by week visually using the Week column — each new week is a separator.

---

## Repetition Map Format

Below the table, list each pillar with the count and formats it appears in:

```markdown
## Repetition Map
- **Pillar 1: [name]** — Appears 4 times: 2 LinkedIn text posts (week 1, week 4), 1 long-form blog (week 1), 1 Reddit reply (week 2)
- **Pillar 2: [name]** — Appears 3 times: 1 LinkedIn text post (week 2), 1 LinkedIn document carousel (week 5), 1 Reddit reply (week 3)
- **Pillar 3: [name]** — Appears 3 times: 1 LinkedIn text post (week 3), 1 long-form blog (week 6), 1 Reddit reply (week 7)
```

A pillar appearing 1–2 times is a red flag. A pillar appearing 5+ times is over-rotation and the founder should consider redistributing to other pillars.

---

## Capacity Budget Format

```markdown
## Capacity Budget
- **Available:** 6 hours/week (from marketing-channel-strategy.md)
- **Used by this calendar:** 5.5 hours/week average
- **Headroom:** 0.5 hours/week — accounts for editing, scheduling, response handling
```

If "Used" exceeds "Available", the calendar is broken. Cut entries before writing the file.

---

## Production Workflow Format

```markdown
## Production Workflow
- **LinkedIn text posts (company voice)** → `linkedin-writer`
- **LinkedIn text posts (founder voice)** → `founder-linkedin-builder`
- **Long-form blog posts** → `blog-writer`
- **Reddit replies** → `reddit-engager` (founder brings the thread URL)
- **YouTube videos** → `youtube-scriptwriter`
- **Industry research reports** → `technical-report-writer`
```

This is a constant block — copy it from this template into every calendar file the skill produces. Adjust for which writer skills are actually being used (only include rows for channels in the calendar).

---

## Notes for Future Re-runs Format

```markdown
## Notes for Future Re-runs
- After [end date], return to this file. Mark each entry as Published, Drafted, Scheduled, or Skipped.
- The Skipped column tells you whether the calendar was over-ambitious. If more than 25% of entries were skipped, the next calendar should reduce volume by that amount.
- If a pillar is consistently underperforming on engagement, the issue may be with the pillar itself (`messaging-architect`) rather than with the topics here. Surface the pattern when running `channel-strategist` for the next period.
- Do not let this file rot. A stale content calendar is worse than no calendar — it represents a false plan.
```

This block is also a constant — include it on every calendar.
