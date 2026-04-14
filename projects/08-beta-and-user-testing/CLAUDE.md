# Project 08 — Beta & User Testing

## Purpose

This is where the product meets real users for the first time. The goal is not to "get users" — it is to learn, with discipline, whether the product you built in Project 07 actually solves the problem you hypothesized in Project 01, for the people you defined in your ICP, in a way they would pay for. Every other project up to this point has been preparation; this is the project where preparation collides with reality.

By the end of this project you will have invited a deliberately chosen cohort of early-access users from the waitlist, collected structured feedback (not vibes) against explicit learning goals, synthesized that feedback into product-relevant themes tagged by ICP tier and product area, and maintained active engagement with the cohort to surface retention risk before it becomes churn. The distilled insights feed forward into Project 09 (pricing — willingness-to-pay signal is the primary input) and Project 11 (fundraising — customer validation evidence is the primary input). The full synthesis reports also loop back to Project 06 when they reveal the PRD needs to change.

User-facing copy in this project uses **"early access"** framing — it is lower-commitment than "beta" and less contractual than "design partner." Internal file and skill names retain `beta-*` naming for consistency with the architecture spec.

## Prerequisites

Complete **Project 06** (product management — produces `product-overview.md`) and **Project 07** (product development — at least one epic shipped and QA-reviewed). There needs to be a real product for early-access users to use.

**Project 04** (inbound marketing — produces `outputs/waitlist-tracker.md`) is strongly recommended. `beta-recruiter` reads the tracker as its primary input. If the waitlist does not exist yet, the skill can still run using a founder-supplied candidate list, but the typical pattern is to recruit from the tracker.

**Project 01** (market research — produces `icp.md`) is required. Every skill here tiers users and tags feedback against the ICP.

## Global Context Files

**Loads:** `icp.md`, `product-overview.md`, `founder-profile.md`, `brand-voice.md` (optional — soft-degrade if missing)

**Writes:** `validated-insights.md` — written by `feedback-synthesizer` via the `context-writer` skill after each synthesis round. This is a distilled summary (top themes, willingness-to-pay signals, ICP-tier breakdown) that Projects 09 and 11 auto-load. Each run appends a new dated section rather than overwriting, so insights accumulate across cohorts. Full synthesis reports stay project-scoped.

**Cross-project reads:**
- `projects/04-inbound-marketing/outputs/waitlist-tracker.md` — canonical candidate pool for `beta-recruiter`
- `projects/06-product-management/outputs/epic-list.md` — optional, used by `feedback-synthesizer` to tag feedback against planned epics

## How This Project Works

Skills fall into four groups that map to the arc of an early-access cohort:

1. **Recruit** — `beta-recruiter` selects Tier A waitlist users, drafts personalized invitations, and maintains `beta-user-tracker.md` as the canonical cohort record.
2. **Collect** — `feedback-collector` produces structured survey templates calibrated to explicit learning goals (usability, value perception, willingness-to-pay, feature gaps). You export or paste the survey into whatever tool you use (Google Forms, Typeform, paste-in).
3. **Synthesize** — `feedback-synthesizer` ingests raw feedback (survey exports, interview transcripts, ad-hoc notes) and produces a themed synthesis report. It then writes a distilled summary to `global/context/validated-insights.md` so downstream projects can read it.
4. **Retain** — `cs-engager` drafts structured check-in messages at defined intervals and surfaces retention-risk signals from the tracker. Check-ins are not just bug reports — they are the founder's mechanism for catching disengagement before it becomes churn.

All skills are conversational, load the right context, ground recommendations in `icp.md` and `product-overview.md`, and show a preview before writing any file. The cohort is not a one-shot — you return to these skills repeatedly as the cohort matures.

**Iteration is expected.** Your first survey will miss a question you wish you had asked. Your first synthesis will notice a theme you would not have predicted. Feed those learnings back — update your learning goals, re-run `feedback-collector` with sharper questions, tighten the synthesis tags over time. The skills are designed to be re-run.

## Skills

| Skill | Description |
|---|---|
| `beta-recruiter` | Pull Tier A users from the waitlist, draft personalized early-access invitations, maintain `beta-user-tracker.md` |
| `feedback-collector` | Build structured feedback survey templates calibrated to stage-specific learning goals |
| `feedback-synthesizer` | Synthesize raw feedback into a themed report tagged by product area, ICP tier, and willingness-to-pay; write distilled summary to `validated-insights.md` |
| `cs-engager` | Draft structured check-in messages for early-access users; surface retention-risk signals from the tracker |

## Recommended Flow

**Cohort kickoff (in order):**
1. **`beta-recruiter`** — first skill per cohort. Select the first 8–15 Tier A users from `waitlist-tracker.md`, draft personalized invitations, create the tracker. Expect 30–60 minutes for the first cohort, less for subsequent rounds.
2. **`feedback-collector`** — before the first round of feedback is due. Define the primary learning goal for this cohort (usability? value perception? willingness-to-pay?) and produce a survey template that hits it directly. Shorter surveys complete more often — the skill will push back on bloat.

**Ongoing (run repeatedly as feedback arrives):**
3. **`feedback-synthesizer`** — whenever you have a meaningful batch of raw feedback to process (5+ survey responses, 3+ interviews, or a single high-signal deep-dive). The skill produces a full synthesis report project-locally and a distilled summary into `global/context/validated-insights.md`.
4. **`cs-engager`** — run at the cadence your playbook defines (typically every 1–2 weeks per active user). Surfaces retention-risk signals before disengagement hardens into churn.

If synthesis reveals the product is fundamentally mis-targeted, the right move is to go back to Project 06 (update PRD/epics) or Project 01 (revise the ICP), not to iterate on survey questions. The skills are honest about this — they will tell you when the gap is upstream.

## Outputs

All saved in `projects/08-beta-and-user-testing/outputs/`:

- `beta-outreach-drafts/<YYYY-MM-DD>-<slug>.md` — Personalized early-access invitation emails (from `beta-recruiter`)
- `beta-user-tracker.md` — Canonical cohort record with status, tier, engagement notes, next actions (from `beta-recruiter`, updated by `cs-engager`)
- `feedback-survey-templates/<YYYY-MM-DD>-<topic>.md` — Survey templates with learning goal, questions, and tool-specific formatting (from `feedback-collector`)
- `feedback-synthesis-reports/synthesis-<YYYY-MM-DD>.md` — Full synthesis reports: themes, ICP-tier breakdown, WTP signals, feature gaps, product area tags, recommended actions (from `feedback-synthesizer`)
- `cs-checkin-drafts/<YYYY-MM-DD>-<user-slug>.md` — Individualized check-in messages (from `cs-engager`)

**Writes to `global/context/`:** `validated-insights.md` (dated, append-only summaries from `feedback-synthesizer`).

## Validation

This project is in a workable state when:

- `beta-user-tracker.md` exists and names at least 5 invited early-access users with status, tier, invited-date, and current engagement state.
- At least one `feedback-survey-templates/*.md` exists with an explicit learning goal stated in the frontmatter — not a generic "get feedback" survey.
- At least one `feedback-synthesis-reports/synthesis-*.md` exists and includes explicit sections for **Willingness-to-Pay Signals** and **ICP-Tier Breakdown** (these are the fields Projects 09 and 11 will read).
- `global/context/validated-insights.md` exists and contains at least one dated synthesis summary.
- `cs-checkin-drafts/` has at least one drafted check-in per active user in the tracker.

A good Project 08 outcome is one where the founder can point to specific, dated evidence for what users said, which tier of the ICP said it, and what it implies for pricing and product direction. Thin cohorts with no synthesis — "five users signed up but I haven't talked to them yet" — are the fastest way to arrive at Project 09 with no signal and Project 11 with no story.

**Note on scope:** This project does not write code (that is the engineering repo, informed by Project 07), does not set pricing (that is Project 09, informed by this project's WTP signals), and does not revise the PRD (that is Project 06, though synthesis reports from here often trigger a PRD update). Keep synthesis rigorous and project-scoped; let the downstream projects act on it.

---

## Don't See What You Need?

The skills in this project cover the most common tasks for this stage, but they are not exhaustive.
If you need a capability that isn't covered, Claude Code includes two native built-in tools for this:

- **Skill creator** — Claude Code's built-in skill authoring tool. Use it to create a new custom skill
  and save it in this project's `.claude/skills/` directory (project-only) or in the root
  `.claude/skills/` directory (available across all projects).
- **MCP builder** — Claude Code's built-in MCP server builder. Use it if you want to connect
  Claude Code to an external tool or API. This is an advanced option most relevant when you want
  to integrate a survey platform (Typeform, Tally), a research repository (Dovetail), or a CRM
  directly into the project.

Custom skills and MCP servers you create will live in your private fork and will not affect
the upstream repo. If you build something you think would benefit other founders, see CONTRIBUTING.md
for how to suggest it.
