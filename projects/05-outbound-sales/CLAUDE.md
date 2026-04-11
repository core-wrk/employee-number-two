# Project 05 — Outbound Sales & Prospecting

## Purpose

This is where you stop waiting for demand to come to you and start generating it deliberately. The goal is to identify high-fit prospects one at a time, reach out personally, and build a pipeline of real conversations with people who could become design partners, early customers, or champions. Outbound at this stage is not a numbers game — it is a learning game. Every conversation is an opportunity to validate the hypothesis, hear how the buyer talks about the problem, and find out whether your product is worth building at all.

By the end of this project you will have a prospect list grounded in your ICP, a set of personalized first-touch outreach drafts, an objection playbook that prepares you for moment-of-truth pushbacks, pre-call briefs for every meeting, a design-partner framework for reframing sales conversations as co-development relationships, a pipeline tracker that tells you what to do next on any given Monday morning, and a CRM-importable export when you are ready to graduate to a real CRM. This project is **not** where you generate inbound demand (that is Project 04) or where you recruit from your waitlist (that is Project 08). It is where you go find specific named humans and have real conversations with them.

## Prerequisites

Complete **Project 01** (market research — produces `icp.md` and `competitive-landscape.md`) and **Project 02** (brand strategy — produces `brand-voice.md`). The skills here load those files as ground truth and will refuse to run if `icp.md` or `brand-voice.md` is missing or empty. If you have not yet completed those projects, the skills will tell you exactly which one to run first.

**Project 06** (product management — produces `product-overview.md`) is recommended but not required. In practice, founders often start outbound before the formal PRD work is done because outbound conversations are themselves one of the best inputs to product management. When `product-overview.md` is missing, the skills will warn you and fall back to `startup-hypothesis.md` for the value proposition — but outreach claims and objection answers will be sharper once you have the product overview in place.

## Global Context Files

**Loads:** `icp.md`, `brand-voice.md`, `competitive-landscape.md`, `founder-profile.md`, `startup-hypothesis.md`, `product-overview.md` (when available)

**Writes:** none — all outputs are project-scoped. (Project 08 reads `outputs/pipeline-tracker.md` directly as a cross-project reference, so its schema needs to stay machine-parseable.)

## How This Project Works

Skills in this project fall into three groups:

1. **Research (linear)** — `prospect-researcher` runs first and produces `prospect-list.md`, the canonical list of prospects you are working. Every execution skill downstream reads this file and refuses to run without it. Start here.
2. **Strategy and execution (parallel)** — `email-drafter`, `pre-call-brief-builder`, `design-partner-advisor`, and `objection-handler` are independent. You run whichever ones you need for the prospects and conversations you are actively working on. All four read brand voice and ICP as ground truth; none of them invent claims about your product.
3. **Operational and ongoing** — `pipeline-tracker-manager` is the heartbeat of the project. You return to it every time a prospect changes stage (contacted, replied, meeting booked, committed, lost). `crm-sync-advisor` is on-demand — you run it when you are ready to export your pipeline into a real CRM like HubSpot.

All skills are conversational. They ask you one question at a time, ground every recommendation in the global context, and show you a preview of any file before writing it. You always have the final say.

**Iteration is expected.** Your first prospect list will be wrong in small ways — some prospects will turn out to be poor fit, some roles you thought were not the buyer will turn out to be, some companies you never thought of will start showing up in real conversations. Re-run `prospect-researcher` as you learn. The skills are designed to be re-run.

## Skills

| Skill | Description |
|---|---|
| `prospect-researcher` | Build the canonical prospect list via targeted web search. Tier every prospect A/B/C/D against the ICP and capture firmographic data and publicly available contact info |
| `email-drafter` | Draft personalized outbound for one prospect at a time — cold email or cold LinkedIn DM, at any position in a 4-touch sequence (initial, FU1, FU2, breakup) |
| `pre-call-brief-builder` | Produce structured pre-call briefs for any prospect who has agreed to a meeting. Company snapshot, inferred pain, discovery questions, and what success looks like |
| `design-partner-advisor` | Build your canonical design partner framework — what you offer, what you ask, how to reframe sales conversations as co-development relationships |
| `objection-handler` | Build and maintain your personalized objection playbook across the 7 standard categories (pricing, timing, trust, competition, fit, authority, proof) |
| `pipeline-tracker-manager` | Maintain the canonical pipeline tracker. Enforce the stage enum, preserve history, flag stuck prospects, surface design partner candidates |
| `crm-sync-advisor` | Export your prospects and pipeline into CRM-importable CSVs for HubSpot, Salesforce, or Airtable |

## Recommended Flow

**Research first:**
1. **`prospect-researcher`** — always first. You cannot draft outreach for prospects that do not exist yet. Expect 30–60 minutes to produce a first batch of 10–25 high-fit prospects. Do not try to build a 200-prospect list in week 1 — start small and iterate.

**Strategic prep (do this early, re-run as you learn):**
2. **`design-partner-advisor`** — produce your canonical `design-partner-framework.md` before you start booking calls. It is a single document you reference across every conversation. Run it once, then update when your framing evolves.
3. **`objection-handler`** — produce your first `objection-playbook.md` before your first real call. Re-run every time you encounter a new objection in the wild and add it to the playbook.

**Execution (per prospect, in any order):**
4. **`email-drafter`** — one draft at a time, per prospect, per sequence position. Do not try to batch. Personalization that is real takes time.
5. **`pre-call-brief-builder`** — for any prospect who agrees to a call. Run it the day before the call, not the morning of.

**Ongoing:**
6. **`pipeline-tracker-manager`** — every time a prospect changes stage. This is the heartbeat. If you are not running this skill regularly, the tracker goes stale and stuck prospects stop getting flagged.

**On-demand:**
7. **`crm-sync-advisor`** — run it when you are ready to move your pipeline into a real CRM. Most founders do this somewhere between 25 and 100 prospects.

If a prospect in your list turns out not to be a fit, mark them Lost in the pipeline tracker with a note about what you learned. That note is valuable — it improves your ICP over time.

## Outputs

All saved in `projects/05-outbound-sales/outputs/`:

- `prospect-list.md` — Canonical prospect list with ICP tiers and firmographic data (from `prospect-researcher`)
- `outreach-drafts/<prospect-slug>-<sequence-position>.md` — Personalized outbound drafts per prospect and touch (from `email-drafter`)
- `pre-call-briefs/<prospect-slug>-<YYYY-MM-DD>.md` — Per-call preparation briefs (from `pre-call-brief-builder`)
- `design-partner-framework.md` — Single canonical framework for reframing sales conversations (from `design-partner-advisor`)
- `objection-playbook.md` — Personalized objection playbook across 7 categories (from `objection-handler`)
- `pipeline-tracker.md` — Canonical operational pipeline tracker with stage enum (from `pipeline-tracker-manager`)
- `crm-export/contacts.csv`, `companies.csv`, `README.md` — CRM-importable export (from `crm-sync-advisor`)

This project does not write to `global/context/`. Everything stays project-scoped. The pipeline tracker is the only output that is read directly by another project (Project 08), and its schema is non-negotiable for that reason.

## Validation

This project is in a workable state when:

- `prospect-list.md` exists and contains at least 10 prospects, each with an ICP tier (A/B/C/D) and a one-sentence "why this prospect" rationale citing `icp.md`.
- `objection-playbook.md` exists with at least 8 objections across at least 4 of the 7 standard categories. Every objection has a specific answer in the founder's voice and a failure mode to avoid.
- `design-partner-framework.md` exists as a single canonical document with the asymmetric exchange named explicitly (what you offer, what you ask).
- At least 5 personalized drafts exist in `outreach-drafts/` and each one references something specific about the prospect that is not mail-merge-token personalization.
- `pipeline-tracker.md` exists with the correct schema, even if it has zero entries. The schema must be machine-parseable so Project 08 can read it.

A good Project 05 outcome is one where you are having real conversations with named humans every week, your pipeline tracker shows which prospects are moving and which are stuck, and every new conversation teaches you something that sharpens the ICP, the objection playbook, or the outreach drafts. Cold lists, empty trackers, and drafts that sound like every other B2B cold email are signs you are prioritizing volume over learning — slow down and make every touch count.

**Note on scope:** Inbound demand generation is Project 04, not here. Beta recruitment from your waitlist is Project 08. This project is specifically about going out and finding the humans you want to talk to, not about responding to the ones who come to you. The `pipeline-tracker.md` output bridges into Project 08 the same way Project 04's `waitlist-tracker.md` does — Project 08's `beta-recruiter` reads both to assemble its beta cohort.

---

## Don't See What You Need?

The skills in this project cover the most common tasks for this stage, but they are not exhaustive.
If you need a capability that isn't covered, Claude Code includes two native built-in tools for this:

- **Skill creator** — Claude Code's built-in skill authoring tool. Use it to create a new custom skill
  and save it in this project's `.claude/skills/` directory (project-only) or in the root
  `.claude/skills/` directory (available across all projects).
- **MCP builder** — Claude Code's built-in MCP server builder. Use it if you want to connect
  Claude Code to an external tool or API. This is an advanced option most relevant when you want
  to integrate a CRM (HubSpot, Salesforce), an email platform (Gmail, Outlook), or a prospecting
  database (Apollo, ZoomInfo) directly into the project.

Custom skills and MCP servers you create will live in your private fork and will not affect
the upstream repo. If you build something you think would benefit other founders, see CONTRIBUTING.md
for how to suggest it.
