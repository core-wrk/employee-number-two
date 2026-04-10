# Project 04 — Inbound Marketing & Content Engine

## Purpose

This is where you turn the strategy from Projects 01–03 into content the market can actually see. The goal is twofold: drive awareness for your category and the wedge you have chosen, and capture early demand into a waitlist that will become the recruitment pool for Project 08 (beta and user testing).

By the end of this project you will have made an explicit channel bet (which 2–3 channels you are investing in and why), built a content calendar that maps to your messaging pillars, drafted the first weeks of content across formats, and set up a waitlist tracker that qualifies signups against your ICP as they come in. This is not where you do outbound prospecting (Project 05) and not where you actually recruit beta users (Project 08) — it is where you generate the inbound demand those projects then act on.

## Prerequisites

Complete Project 02 (brand strategy and voice) and Project 03 (brand identity). The skills here load `brand-voice.md` and `brand-identity.md` as ground truth and will refuse to run if either is missing or empty. If you have not yet completed those projects, the skills will tell you exactly which one to run first.

## Global Context Files

**Loads:** `brand-voice.md`, `brand-identity.md`, `icp.md`, `startup-hypothesis.md`, `founder-profile.md`, `competitive-landscape.md`

**Writes:** none — all outputs are project-scoped. (Project 08 reads `outputs/waitlist-tracker.md` directly as a cross-project reference, so its schema needs to stay machine-parseable.)

## How This Project Works

Skills in this project fall into three groups:

1. **Strategy (linear)** — `channel-strategist` runs first and decides which channels you are investing in, in what order, with what cadence. `content-strategist` runs second and turns the channel strategy into a concrete calendar tied to your messaging pillars. The second skill will refuse to run without the first one's output.
2. **Execution (parallel)** — `blog-writer`, `linkedin-writer`, `founder-linkedin-builder`, `reddit-engager`, `youtube-scriptwriter`, and `technical-report-writer` are independent drafters. You run whichever ones serve the channels you committed to in strategy. They all read brand voice and ICP as ground truth; none of them invent claims.
3. **Ongoing** — `waitlist-manager` is not a one-time skill. You return to it whenever you have new signups to qualify. The tracker it maintains is the canonical lead list and is read by Project 08.

All skills are conversational. They ask you one question at a time, ground every recommendation in the global context, and show you a preview of any file before writing it. You always have the final say.

**Iteration is expected.** A channel strategy that looked right in week one may look wrong in week six once you have real engagement data. Come back, re-run `channel-strategist`, update the calendar. The skills are designed to be re-run as you learn.

## Skills

| Skill | Description |
|---|---|
| `channel-strategist` | Decide which 2–3 channels to invest in, in what order, with what cadence — grounded in the ICP's "Where to Find Them" section and your realistic capacity |
| `content-strategist` | Turn the channel strategy into a 4–8 week content calendar mapped to your messaging pillars |
| `blog-writer` | Draft long-form blog posts in the brand voice, grounded in messaging pillars and ICP vocabulary |
| `linkedin-writer` | Produce LinkedIn posts in the **company brand voice** in multiple formats (text, document, poll, repost) |
| `founder-linkedin-builder` | Produce LinkedIn posts in the **founder's personal voice** for thought leadership — distinct from the company voice |
| `reddit-engager` | Draft authentic, value-first replies to specific Reddit threads the founder brings to the conversation |
| `youtube-scriptwriter` | Produce full video scripts with hook, body, CTA, and chapter markers, calibrated to YouTube intent patterns |
| `technical-report-writer` | Produce industry research reports — long-form, data-backed assets like "State of [X]" reports that justify a waitlist gate |
| `waitlist-manager` | Qualify new waitlist signups against the ICP, tag by tier, and maintain the canonical tracker that Project 08 reads |

## Recommended Flow

**Strategy first, in order:**
1. **`channel-strategist`** — always first. You cannot decide what to publish until you have decided where to publish it. Expect 30–60 minutes; the conversation surfaces tradeoffs about your real capacity that the founder usually has not thought through.
2. **`content-strategist`** — only after `marketing-channel-strategy.md` exists. The skill will refuse to run otherwise. Expect a focused working session that produces a 4–8 week calendar.

**Execution, in any order:**
3. Pick the writer skills that match the channels you committed to in strategy. If LinkedIn and blog are your two primary channels, run `linkedin-writer`, `founder-linkedin-builder`, and `blog-writer` regularly. Skip the others until your strategy changes.
4. `reddit-engager` is reactive — run it whenever the founder finds a thread worth engaging with, not on a schedule.
5. `technical-report-writer` is event-driven — run it once per quarter at most, when you have genuine new data to publish. Do not run it without real data; the skill will push back.

**Ongoing:**
6. `waitlist-manager` — return whenever you have new signups. The tracker is the bridge to Project 08.

If you find that a channel you committed to is not producing signal after 60 days, go back to `channel-strategist` and reconsider. Cutting a channel is not failure; it is the point of having kill criteria.

## Outputs

All saved in `projects/04-inbound-marketing/outputs/`:

- `marketing-channel-strategy.md` — Channel-by-channel rationale, cadence, sequencing, kill criteria, and capacity budget (from `channel-strategist`)
- `content-calendar.md` — 4–8 week calendar mapped to messaging pillars and channels (from `content-strategist`)
- `blog/<slug>.md` — Long-form blog post drafts (from `blog-writer`)
- `linkedin/<slug>.md` — Company-voiced LinkedIn post drafts (from `linkedin-writer`)
- `linkedin/founder-<slug>.md` — Founder-voiced LinkedIn post drafts (from `founder-linkedin-builder`)
- `reddit-engagement/<thread-slug>.md` — Reddit reply drafts with thread URL, rationale, and timing (from `reddit-engager`)
- `youtube/<slug>.md` — Full video scripts with cues and chapter markers (from `youtube-scriptwriter`)
- `technical-reports/<slug>.md` — Industry research reports with executive summary and distribution plan (from `technical-report-writer`)
- `waitlist-tracker.md` — Canonical lead list, tagged by ICP tier (from `waitlist-manager`)

This project does not write to `global/context/`. Everything stays project-scoped. The waitlist tracker is the only output that is read directly by another project (Project 08).

## Validation

This project is in a workable state when:

- `marketing-channel-strategy.md` exists, names 2–3 primary channels (not more), and ties each channel to evidence in `icp.md`'s "Where to Find Them" section. Each channel has a cadence, a 60-day kill criterion, and a capacity cost in founder hours per week.
- `content-calendar.md` exists and covers at least 4 weeks. Every entry maps to a messaging pillar from `projects/02-brand-and-marketing/outputs/messaging-framework.md`. Repetition is built in (each pillar appears 3+ times across formats).
- The first 4 weeks of the calendar have actual drafts produced — not all of them, but enough to validate that the writer skills produce content the founder is willing to publish.
- `waitlist-tracker.md` exists with the schema specified by `waitlist-manager`, even if it has zero entries. The schema must be machine-parseable so Project 08 can read it.

A good Project 04 outcome is one where the founder is publishing on their committed channels at the cadence they set, has a tracker that captures every signup, and is ready to hand the highest-tier waitlist signups to Project 08 for beta recruitment. Hollow content, vanity metrics, and a calendar that nobody actually executes against are signs the channel strategy was over-ambitious — go back and cut.

**Note on scope:** Outbound prospecting (cold outreach to specific prospects) is Project 05, not here. Beta recruitment from the waitlist is Project 08. This project produces inbound demand and qualifies it; the next two projects act on that demand in different ways.

---

## Don't See What You Need?

The skills in this project cover the most common tasks for this stage, but they are not exhaustive.
If you need a capability that isn't covered, Claude Code includes two native built-in tools for this:

- **Skill creator** — Claude Code's built-in skill authoring tool. Use it to create a new custom skill
  and save it in this project's `.claude/skills/` directory (project-only) or in the root
  `.claude/skills/` directory (available across all projects).
- **MCP builder** — Claude Code's built-in MCP server builder. Use it if you want to connect
  Claude Code to an external tool or API.

Custom skills and MCP servers you create will live in your private fork and will not affect
the upstream repo. If you build something you think would benefit other founders, see CONTRIBUTING.md
for how to suggest it.
