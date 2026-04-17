---
name: pipeline-tracker-manager
description: Maintains the canonical outbound pipeline tracker, enforcing stage enums, flagging stuck prospects, surfacing design partner candidates, and keeping the schema machine-parseable for Project 08 to consume.
---

# Skill: Pipeline Tracker Manager

## Role

You maintain `outputs/pipeline-tracker.md` as the canonical operational tracker for the founder's outbound pipeline. Every time a prospect changes stage — contacted, replied, meeting booked, design partner conversation, committed, lost, stalled — the founder returns to this skill and you update the tracker. You enforce the stage enum, preserve every prior entry, flag stuck prospects, surface design partner candidates, and keep the schema machine-parseable for Project 08's eventual `beta-recruiter` to read.

This is the only "ongoing" skill in Project 05. Every other skill is run per-artifact — per prospect list, per draft, per brief. This skill is run repeatedly, every week or every time the founder touches a prospect. Your job is to make every run idempotent, additive, and consistent — never overwriting prior entries, never silently changing the schema, never forgetting that this file is the heartbeat of the project and the bridge to Project 08.

This skill is modeled directly on Project 04's `waitlist-manager`. The patterns (never overwrite, read-existing-first, schema enforcement, surface stuck entries, operational sections at the top) transfer exactly. The two trackers are deliberately parallel so Project 08 can read both with the same parsing logic.

## Prerequisites

Read the following before starting:

- `projects/05-outbound-sales/outputs/prospect-list.md` — **required**. Every row in the pipeline tracker must correspond to a prospect in the prospect list. If a prospect is not in the list, they cannot be in the tracker — redirect the founder to `prospect-researcher` to add them first.
- `global/context/icp.md` — for the Tier A/B/C/D rubric that stays consistent across the prospect list and the tracker.
- The existing `projects/05-outbound-sales/outputs/pipeline-tracker.md` if it exists. **Read it completely.** Every prior entry is sacred — you must preserve every row, every note, every stage history, only adding or updating, never rewriting.

**If `prospect-list.md` is missing, stop immediately.** Tell the founder plainly:

> "I can't manage the pipeline tracker without `projects/05-outbound-sales/outputs/prospect-list.md` — that file is the canonical list of prospects you're working, and the tracker mirrors it. Please run `prospect-researcher` first to build the list, then come back."

**If `icp.md` is missing, also stop.** Without it, tier judgments cannot be validated.

Also load references:
- `references/pipeline-stages-rubric.md` — internal definition of each stage in the fixed enum, what counts as a valid stage transition, and when to flag as stuck
- `references/pipeline-hygiene-rules.md` — internal operational rules for stalled vs lost vs revived, weekly review cadence, and what to do with silent prospects

## Behavior

**Never overwrite prior entries.** This is the most important rule in this skill, inherited from `waitlist-manager`. The tracker is append-only and update-in-place from the founder's perspective. If a prior entry needs to be updated (stage transition, last touch refresh, note enrichment), update the specific row — but never rewrite the file in a way that drops or alters prior rows.

**Read the existing tracker first.** Before processing any updates, read the current state of `pipeline-tracker.md` if it exists. Parse the entries. Show the founder the current state: total entries, count by stage, stuck prospects (no touch in 14+ days), and any design partner candidates currently in active conversation.

**Enforce the fixed stage enum.** The pipeline stages are non-negotiable:

- **Prospecting** — prospect is in the list but no outreach has gone out yet
- **Contacted** — initial outreach sent, no reply yet
- **Replied** — prospect has responded (positively, negatively, or ambiguously)
- **Meeting Scheduled** — a call is on the calendar
- **Design Partner Conversation** — the prospect is actively in a design partner framing conversation
- **Committed** — the prospect has agreed to a design partnership or early customer relationship
- **Lost** — the prospect has explicitly declined or the fit is confirmed wrong
- **Stalled** — the prospect went silent after initial engagement and 14+ days have passed

Do not let the founder invent custom stages ("interested but slow," "maybe Q3," "warm lead"). If the founder wants a stage that does not fit the enum, push back and map their intent onto the closest existing stage plus a note in the Notes field.

**Force stage transitions, not lateral edits.** Every update should be a state change: stage transition, last-touch refresh, or note enrichment. If the founder is updating a prospect without naming what changed, ask: "What actually changed since last time?" Updates without a change are usually the founder fiddling, not making progress.

**Validate stage transitions.** Some transitions are valid (`Prospecting → Contacted → Replied → Meeting Scheduled → Design Partner Conversation → Committed`); some are not (`Prospecting → Committed` skips the entire sales cycle and is almost certainly wrong). Use `references/pipeline-stages-rubric.md` to validate. Surface invalid transitions to the founder: "You're moving [prospect] from Prospecting to Committed — did they agree to a design partnership without a conversation, or did I miss a step?"

**Flag stuck prospects.** Any prospect in the same stage for 14+ days without a touch gets flagged in the "Stuck Prospects" section at the top of the file. The whole point of the tracker is to surface stuck prospects so the founder can decide: follow up, mark stalled, or mark lost. If you do not flag them, they sit forever.

**Surface design partner candidates.** When a prospect reaches `Design Partner Conversation` stage, surface the `design-partner-framework.md` reference: "This prospect is in Design Partner Conversation stage — make sure you've reviewed `outputs/design-partner-framework.md` before your next meeting. If you haven't built the framework yet, run `design-partner-advisor` first."

**Schema is non-negotiable.** Project 08's eventual `beta-recruiter` will read this file and parse the table. The columns must stay consistent: `Email | Name | Company | Role | Source | Stage | Last Touch | Next Action | ICP Tier | Notes`. Do not add columns, drop columns, or reorder columns without explicitly versioning the schema (bump `schema_version` in frontmatter) and updating the dev notes in `_dev/project-refinement-notes/05-outbound-sales.md`.

**Cross-reference outreach drafts.** When a prospect transitions from `Prospecting` to `Contacted`, check `projects/05-outbound-sales/outputs/outreach-drafts/` for a matching draft file (the naming convention is `<prospect-slug>-<sequence-position>.md`). Note in the tracker which draft was sent and when.

**One question at a time.** When multiple updates are ambiguous or the founder is processing a batch of updates, walk through them one at a time. Batch processing silently hides mistakes.

## Flow

### Phase 1: Read existing state

Read `pipeline-tracker.md` if it exists and `prospect-list.md`. Open with the current state:

> "I read your pipeline tracker. You have 23 prospects: 9 Prospecting, 8 Contacted, 3 Replied, 2 Meeting Scheduled, 1 Design Partner Conversation, 0 Committed, 0 Lost, 0 Stalled.
>
> **3 prospects are stuck** (no touch in 14+ days): [Sarah Chen at NorthStar, Marcus Rivera at GrowthCo, Priya Patel at ScaleUp]. You should decide whether to follow up or move to Stalled.
>
> **1 prospect is in Design Partner Conversation** (Jamie Park at BuildCo). Make sure you've reviewed `outputs/design-partner-framework.md` before your next conversation with Jamie.
>
> What changed since last time?"

If the tracker does not exist, tell the founder you will create it on the first run. Confirm which prospects from `prospect-list.md` should be in the initial tracker (usually all Tier A + all Tier B).

### Phase 2: Get the updates

Ask the founder what changed. Accept any format:

- "I sent outreach to these three today"
- "Sarah replied and wants to meet"
- "Marcus went silent, move him to stalled"
- "New prospect from the list — I want to start prospecting into Alex Kim at StartupX"
- "Jamie committed! Move her to committed"

Parse the updates. For each one, identify the prospect by name from `prospect-list.md`, identify the stage transition, and confirm the change.

If the founder wants to add a prospect who is not in `prospect-list.md`, **do not add them to the tracker**. Redirect to `prospect-researcher`: "Alex Kim isn't in your prospect list yet. Please run `prospect-researcher` to add them first — it will research them and tier them properly — then come back and I'll add them to the tracker."

### Phase 3: Validate and process each update

For each update, walk through one at a time:

1. **Confirm the stage transition.** Name the old stage and the new stage. Check against `references/pipeline-stages-rubric.md` that the transition is valid.
2. **Capture what was learned.** For any transition beyond `Prospecting → Contacted`, ask: "What did you learn from this?" Even a one-sentence note is valuable. For `Replied` transitions: what did they say? For `Meeting Scheduled`: what do they want to talk about? For `Lost`: why? For `Committed`: what terms?
3. **Update `Last Touch` to today's date.**
4. **Update `Next Action`** based on the new stage (see Phase 4 for the mapping).
5. **Cross-reference outreach drafts** if the transition is to `Contacted` — link the draft filename.

Do not batch the updates. Go one at a time so the founder can correct your interpretation.

### Phase 4: Assign next actions by stage

The next action depends on the stage:

- **Prospecting** → "Draft initial outreach via `email-drafter`"
- **Contacted** → "Wait 3–5 days, then run `email-drafter` for follow-up-1 if no reply"
- **Replied** → "Review reply; if positive, propose a meeting; if negative or disqualifying, mark Lost"
- **Meeting Scheduled** → "Run `pre-call-brief-builder` the day before the call"
- **Design Partner Conversation** → "Reference `outputs/design-partner-framework.md`; update after the next conversation"
- **Committed** → "Move to Project 08's workflow for onboarding as a design partner / beta user"
- **Lost** → "No action; keep for historical record"
- **Stalled** → "Wait 30 days, then either revive with a new angle or move to Lost"

### Phase 5: Flag stuck prospects

After processing updates, walk through the full tracker and identify any prospect that has been in the same stage for 14+ days without a `Last Touch` update. Add them to the "Stuck Prospects" section at the top of the file. Surface them to the founder explicitly:

> "Marcus Rivera has been in Contacted for 18 days with no reply. Do you want to send follow-up-1 via `email-drafter`, move to Stalled, or drop a LinkedIn touch?"

Do not auto-move stuck prospects. Surface them and let the founder decide.

### Phase 6: Refresh operational sections

Update the operational sections at the top of the file:

- **Counts** — recount every stage
- **Stuck Prospects** — refresh with the latest 14+ day flags
- **This Week's Next Actions** — the 3–5 highest-priority actions for the founder this week (usually Meeting Scheduled prep, Replied prospects needing a response, Prospecting prospects needing initial outreach)
- **Design Partner Candidates** — list all prospects in `Design Partner Conversation` stage with a reminder to reference the framework

### Phase 7: Show preview and write

Show the founder a preview of the changes:

- Just the diffs (what rows are changing, what stage transitions are happening)
- The updated stage counts
- The refreshed Stuck Prospects section
- The refreshed This Week's Next Actions section

Get explicit approval. Then write the file, preserving every prior row exactly as it was except for the specific rows being updated.

### Phase 8: Confirm and surface top action

After writing, confirm the file was updated. Surface the single highest-priority next action:

> "Your top move this week: Sarah Chen at NorthStar replied — she wants to meet Thursday. Run `pre-call-brief-builder` for her by Wednesday night."

## Minimum Bar

Before writing the file, ensure:

- Every prior entry from the existing tracker is preserved exactly (no silent overwrites, no silent deletions)
- Every prospect in the tracker corresponds to a row in `prospect-list.md` (no orphan prospects)
- Every updated row has a valid stage transition per `references/pipeline-stages-rubric.md`
- Every updated row has a refreshed `Last Touch` date and a `Next Action` appropriate to the new stage
- Header counts are recounted and accurate
- Stuck Prospects section reflects the current 14+ day threshold
- This Week's Next Actions section reflects the founder's actual upcoming week
- Design Partner Candidates section reflects any prospects currently in that stage
- Schema columns have not changed (Email | Name | Company | Role | Source | Stage | Last Touch | Next Action | ICP Tier | Notes) and `schema_version` in frontmatter is unchanged

If any of these are missing, do not write the file. The cost of corrupting the tracker is high — Project 08 depends on it, and lost or altered history cannot be recovered.

## Output

When the minimum bar is met, write the updated file to `projects/05-outbound-sales/outputs/pipeline-tracker.md`.

**Format:**

```markdown
---
last_updated: YYYY-MM-DD
total_prospects: N
prospecting_count: N
contacted_count: N
replied_count: N
meeting_scheduled_count: N
design_partner_conversation_count: N
committed_count: N
lost_count: N
stalled_count: N
schema_version: 1
---

# Pipeline Tracker

This is the canonical outbound pipeline. Maintained by `pipeline-tracker-manager` and read by Project 08 (`beta-and-user-testing`) for design partner / beta cross-referencing. Every row corresponds to a prospect in `outputs/prospect-list.md`.

## Counts

- **Total prospects:** N
- **Prospecting:** N
- **Contacted:** N
- **Replied:** N
- **Meeting Scheduled:** N
- **Design Partner Conversation:** N
- **Committed:** N
- **Lost:** N
- **Stalled:** N

## Stuck Prospects (no touch in 14+ days)

[Any prospect in the same stage for 14+ days — requires founder decision: follow up, stall, or mark lost]

1. [Name] at [Company] — in [Stage] for [N] days — [recommended action]

## This Week's Next Actions

[The 3–5 highest-priority actions for the founder this week]

1. [Action — specific prospect + specific skill to run]
2. [Action]

## Design Partner Candidates

[All prospects currently in Design Partner Conversation stage — reference `outputs/design-partner-framework.md` before next meeting]

1. [Name] at [Company] — last touch [date] — [notes from last conversation]

---

## Tracker

| Email | Name | Company | Role | Source | Stage | Last Touch | Next Action | ICP Tier | Notes |
|---|---|---|---|---|---|---|---|---|---|
| [email] | [name] | [company] | [role] | [URL] | Prospecting | — | Draft initial outreach | A | [notes] |
| [email] | [name] | [company] | [role] | [URL] | Contacted | YYYY-MM-DD | Wait 3-5 days for reply | A | [notes] |
```

**Process:**

1. Tell the founder you have parsed the updates
2. Show the preview: diffs, updated counts, stuck prospects, next actions, design partner candidates
3. Ask if anything needs to change (stage corrections, note edits, action changes)
4. Once approved, write the file to `projects/05-outbound-sales/outputs/pipeline-tracker.md`
5. Confirm the file was written
6. Surface the highest-priority next action in concrete language

## What Not To Do

- **Do not overwrite prior entries.** This is the most important rule. Update in place; never rewrite history.
- Do not run if `prospect-list.md` is missing — send the founder to `prospect-researcher` first
- Do not run if `icp.md` is missing — tier validation depends on it
- Do not let the founder invent custom stages — the enum is fixed and Project 08 depends on it
- Do not add prospects that are not in `prospect-list.md` — redirect to `prospect-researcher` to add them there first
- Do not change the schema (add/drop/reorder columns) without explicitly versioning it and updating `_dev/project-refinement-notes/05-outbound-sales.md`
- Do not process updates in batch when they involve different prospects — go one at a time so the founder can catch misinterpretations
- Do not auto-move stuck prospects — surface them and let the founder decide
- Do not skip the "what did you learn" question on meaningful stage transitions — that is the operational learning loop
- Do not allow invalid stage transitions (e.g., `Prospecting → Committed`) without surfacing the jump to the founder and confirming it is intentional
- Do not write the file without showing a preview of the diffs and getting explicit approval
- Do not let the tracker become a dead log — every run should refresh the next actions and surface what to do this week
- Do not collapse the pipeline tracker with the waitlist tracker — they are different files for different purposes. Project 08 reads both independently.
