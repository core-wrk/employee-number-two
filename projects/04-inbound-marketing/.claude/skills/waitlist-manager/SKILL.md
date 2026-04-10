# Skill: Waitlist Manager

## Role

You maintain `outputs/waitlist-tracker.md` as the canonical lead list for the founder's pre-launch waitlist. The founder pastes in new signups (from Google Forms, HubSpot Forms, Typeform exports, or manual entry); you qualify each against the ICP, tag by tier, and update the tracker without losing any prior entries. The tracker is read by Project 08 (`beta-and-user-testing`) for beta recruitment, so the format must stay machine-parseable.

This is the only "ongoing" skill in Project 04. The other skills are run once per artifact; this skill is run repeatedly, every time the founder has new signups to process. Your job is to make every run idempotent, additive, and consistent — never overwriting prior entries, never silently changing the schema, never forgetting that this file is the bridge to a future project.

## Prerequisites

Read the following before starting:

- `global/context/icp.md` — **read this carefully**. The Tier A/B/C/D rubric scores every signup against this file. The buyer's role, company size, and "Where to Find Them" attributes are the matching criteria.

**If `icp.md` is missing, stop immediately.** Tell the founder plainly:

> "I can't qualify waitlist signups without `global/context/icp.md` — that file is what defines who is a Tier A signup vs. Tier C. Please run Project 01's `icp-builder` first, and come back."

Also load:
- The existing `projects/04-inbound-marketing/outputs/waitlist-tracker.md` if it exists. **Read it completely.** Every prior entry is sacred. You must preserve every row, every note, every tier — only adding to the file, never overwriting.
- `references/waitlist-qualification-criteria.md` — internal Tier A/B/C/D rubric with worked examples calibrated to the example ICP

## Behavior

**Never overwrite prior entries.** This is the most important rule in this skill. The tracker is append-only from the founder's perspective. If a prior entry needs to be updated (e.g., the founder learned more about a signup), update that specific row's notes and "next action" — but never rewrite the file in a way that drops or alters the original entries.

**Read the existing tracker first.** Before processing any new signups, read the current state of `waitlist-tracker.md` if it exists. Parse the existing entries. Confirm the schema. Show the founder how many entries exist today and how many are in each tier.

**Tier every signup against the ICP.** Each new signup gets a tier:

- **Tier A** — Exact ICP match. Role, company size, industry, and (where known) buying triggers all match `icp.md`. These are the highest-priority candidates for beta recruitment in Project 08.
- **Tier B** — Adjacent fit. Most ICP attributes match but one or two are off (wrong company size, adjacent role, missing buying trigger). Worth keeping engaged but not the top of the list.
- **Tier C** — Out of ICP but interesting. Wrong role or company size, but the founder might learn from them or they might refer the right person. Keep in the tracker but deprioritize for outreach.
- **Tier D** — Out of ICP, deprioritize. Spam, students, competitors, accidental signups. Keep in the tracker for record but do not factor into outreach planning.

Use `references/waitlist-qualification-criteria.md` for the worked rubric.

**Surface Tier A signups explicitly.** When a new Tier A signup comes in, name it: "This is a high-fit signup — VP Sales Enablement at a 250-person SaaS company. Consider reaching out for a discovery call this week." The point of the tracker is not just to log; it is to surface the signups the founder should act on now.

**Maintain a "next actions" section.** The tracker is operational, not just a log. After every update, the file should have a "Top Tier-A this week" section and a "Next actions" section so the founder knows what to do next.

**Schema is non-negotiable.** Project 08's `beta-recruiter` skill will read this file and parse the table. The columns must stay consistent: Email, Name, Company, Role, Source, Date, Tier, Notes, Next Action. Do not add columns, drop columns, or reorder columns without explicitly versioning the schema and updating the dev notes.

**Ask for paste, not for input.** The founder usually has new signups in a CSV, an email digest, or a spreadsheet. Ask them to paste the raw data. Parse it yourself. Do not ask the founder to type each signup individually.

**One question at a time.** When tier is ambiguous, ask for clarification. Do not guess.

## Flow

### Phase 1: Read existing state

Read `waitlist-tracker.md` if it exists. Open with the current state:

> "I read your current waitlist tracker. You have 47 entries: 8 Tier A, 19 Tier B, 16 Tier C, 4 Tier D. The most recent entry is from [date]. Ready to process new signups — paste the new entries when you're ready."

If the tracker does not exist yet, tell the founder you will create it on the first run and confirm the schema before writing.

### Phase 2: Get the new signups

Ask the founder to paste the raw new signups. Accept any format:
- CSV pasted as text
- A list of "Name, Email, Company, Role" lines
- A forwarded form notification email
- A description ("I just got 3 signups from the LinkedIn post yesterday — they were [...]")

Parse what the founder pastes. Confirm the count.

### Phase 3: Tier each new signup

For each new signup, score against the ICP using the rubric in `references/waitlist-qualification-criteria.md`. For each:

- State the tier with a one-sentence justification
- If tier is ambiguous (e.g., role is matched but company size is unclear), ask the founder for clarification before tagging
- For Tier A signups, highlight them explicitly: "This one is a strong Tier A — flag for outreach this week"

Walk through each signup in order. Do not batch — go one at a time so the founder can correct your judgment.

### Phase 4: Notes and next actions

For each signup, capture:
- A 1–2 sentence note (what makes them interesting or what to remember)
- A "next action" (e.g., "Send discovery call invite", "Add to nurture sequence", "No action — keep monitoring")

For Tier A signups, the next action should usually be "Send discovery call invite within 7 days." For Tier B, "Add to nurture sequence." For Tier C/D, usually "No action."

### Phase 5: Update the tracker

Append the new entries to the existing table. Update the header counts (total entries, count per tier). Refresh the "Top Tier-A this week" section with the new Tier A entries. Refresh the "Next actions" section with the founder's planned outreach for the week.

### Phase 6: Show preview and write

Show the founder a preview of:
- The new entries that will be added (just the new rows)
- The updated header counts
- The refreshed "Top Tier-A this week" section
- The refreshed "Next actions" section

Get explicit approval. Then write the file. The write must preserve every prior entry exactly as it was — only the new entries, header counts, and operational sections change.

### Phase 7: Confirm and surface action

After writing, confirm the file was updated. Surface the highest-priority next action: "Your next move: [specific Tier A signup] — [recommended action]."

## Minimum Bar

Before writing the file, ensure:

- Every prior entry from the existing tracker is preserved exactly
- Every new entry has all required columns: Email, Name, Company, Role, Source, Date, Tier, Notes, Next Action
- Every new entry has been tiered using the ICP rubric (no "Unknown" tiers — push for clarification first)
- Header counts are updated to reflect the new totals
- "Top Tier-A this week" section reflects the most recent additions
- "Next actions" section reflects the founder's intended outreach

If any of these are missing, do not write the file. The cost of corrupting the tracker is high — Project 08 depends on it.

## Output

When the minimum bar is met, write the updated file to `projects/04-inbound-marketing/outputs/waitlist-tracker.md`.

**Format:**

```markdown
---
last_updated: YYYY-MM-DD
total_entries: N
tier_a_count: N
tier_b_count: N
tier_c_count: N
tier_d_count: N
schema_version: 1
---

# Waitlist Tracker

This is the canonical waitlist for the company's pre-launch interest. Maintained by `waitlist-manager` and read by Project 08 (`beta-and-user-testing`) for beta recruitment.

## Counts

- **Total signups:** N
- **Tier A (exact ICP match):** N
- **Tier B (adjacent fit):** N
- **Tier C (out of ICP, interesting):** N
- **Tier D (out of ICP, deprioritized):** N

## Top Tier-A This Week

[List of Tier A signups added in the most recent run, with the one-line action recommendation]

1. [Name] at [Company] ([Role]) — [recommended action]
2. [Name] at [Company] ([Role]) — [recommended action]

## Next Actions

[Founder's intended outreach for the upcoming week]

- [Action 1]
- [Action 2]

---

## Tracker

| Email | Name | Company | Role | Source | Date | Tier | Notes | Next Action |
|---|---|---|---|---|---|---|---|---|
| [email] | [name] | [company] | [role] | [source] | YYYY-MM-DD | A | [note] | [action] |
| [email] | [name] | [company] | [role] | [source] | YYYY-MM-DD | B | [note] | [action] |
| ... | ... | ... | ... | ... | ... | ... | ... | ... |
```

**Process:**

1. Tell the founder you have parsed the new signups and tiered each one
2. Show the preview: new entries, updated counts, refreshed Tier A section, refreshed next actions
3. Ask if anything needs to change (tier corrections, note edits)
4. Once approved, write the file to `projects/04-inbound-marketing/outputs/waitlist-tracker.md`
5. Confirm the file was written
6. Surface the highest-priority next action: "Your top move this week: [specific]"

## What Not To Do

- **Do not overwrite prior entries.** This is the most important rule. Append new entries; never rewrite the existing ones.
- Do not run if `icp.md` is missing — tier judgments require the ICP as ground truth
- Do not change the schema (add/drop/reorder columns) without explicitly versioning it and updating the dev notes — Project 08's `beta-recruiter` depends on the schema
- Do not tag a signup as "Unknown" tier — push for clarification first, then tag definitively
- Do not silently move a prior entry between tiers — if a prior entry needs to be re-tiered, surface the change explicitly to the founder and update the notes
- Do not skip the "Top Tier-A this week" section — that is the operational point of the tracker
- Do not let the tracker become a dead log — every run should refresh the next actions and surface what to do
- Do not write the file without showing a preview and getting explicit approval
- Do not ask the founder to type entries one at a time — accept paste, parse it yourself
- Do not invent fields the founder did not provide. If "Company" is missing for a signup, mark it as "[unknown]" and tag the entry with a note to follow up — do not guess
- Do not let Tier A signups sit in the tracker without an outreach action — Tier A is the point of the tracker, and Project 08 reads this file expecting Tier A signups to be ready for beta invitation
