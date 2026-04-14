# Project 11 — Fundraising Preparation

## Purpose

Identify funding sources, recruit advisors, develop a pitch deck, and prepare the founder for investor conversations. This is where upstream work converges — the ICP, product overview, pricing model, competitive landscape, company profile, and brand voice become a concrete fundraising path, a qualified prospect list, a pitch deck narrative, and personalized outreach.

The goal is not to raise money in this project — the goal is to prepare to raise, so that when the founder starts conversations, they go in with defensible evidence, qualified targets, honest framing, and a clear ask. Fundraising decisions made here are commercial, not legal; when term sheets appear, route them to a startup attorney.

## Prerequisites

Complete **Project 06** (product management — produces `product-overview.md`) and **Project 09** (pricing & packaging — produces `pricing-model.md`). Fundability math and pitch substance both require these.

**Project 10** (legal and company formation — produces `company-profile.md`) is required. Entity structure and cap table state determine which funding instruments are legally available.

**Project 01** (market research — produces `icp.md`, `competitive-landscape.md`) is required. Investor qualification, market sizing, and competitive positioning all reference these.

**Project 02** (brand and marketing — produces `brand-voice.md`) is strongly recommended. The pitch narrative reads better with a defined voice, and investor outreach hard-stops without it. If Project 02 is deferred, `pitch-deck-builder` will proceed with a generic professional voice and flag the gap; `investor-outreach-drafter` will hard-stop.

**Project 00** (onboarding — produces `founder-profile.md`) is strongly recommended. Advisor prospecting requires it; investor qualification is sharper with it.

## Global Context Files

**Loads:** `icp.md`, `competitive-landscape.md`, `product-overview.md`, `pricing-model.md`, `company-profile.md`, `brand-voice.md`, `founder-profile.md`

**Writes:** `competitive-landscape.md` — written by `funding-landscape-researcher` via the global `context-writer` skill when research surfaces new competitors, recent competitor funding events, or positioning shifts. The write is diffed and founder-approved before committing. If no new signal surfaces during a given run, the sync is skipped and `competitive_landscape_updated: no` is recorded in the skill's output frontmatter.

## How This Project Works

Skills fall into four arcs that map to the fundraising preparation journey:

1. **Landscape** — `funding-landscape-researcher` surveys the *actual* menu of funding instruments available at your stage (angels, accelerators, scouts, syndicates, micro-VCs, sector specialists, generalist VCs, RBF, grants, customer prepay, strategic). It resists the "raise a seed round from VCs" default and produces 1–3 finalist paths grounded in founder priorities (speed, control, optionality). As a byproduct, it syncs any new competitive signal back to `competitive-landscape.md`.

2. **Prospecting** — `investor-prospector` (if an equity path is a finalist) converts archetypes into a qualified, ranked list of named investors with warm-intro hypotheses, portfolio-conflict screening, and rubric-based qualification. `advisor-prospector` runs independently or in parallel, identifying expertise-gap-closing advisors organized by the specific gap each closes.

3. **Pitch narrative** — `pitch-deck-builder` produces the deck as two sequential artifacts: a slide-by-slide outline (founder-approved) followed by the narrative with speaker notes. Market sizing is bottoms-up with explicit assumptions; traction is framed honestly per the evidence hierarchy; competition is real.

4. **Outreach** — `investor-outreach-drafter` converts the prospect list into personalized messages (cold email, warm-intro request, LinkedIn DM, follow-up sequence) that match the founder's brand voice. First-touch messages are under 100 words and carry a non-obvious personalization hook per target.

All skills ground every recommendation in the loaded global context, preview before writing, and iterate with the founder. Re-running is expected — as the round progresses, each artifact should be refreshed.

## Skills

| Skill | Description |
|---|---|
| `funding-landscape-researcher` | Survey funding options at current stage; produce 1–3 finalist paths; sync new competitive signal to global context |
| `investor-prospector` | Build a qualified, ranked investor prospect list with archetypes, rubric scoring, portfolio-conflict screens, warm-intro hypotheses |
| `advisor-prospector` | Identify 5–12 advisors organized by expertise gap; distinguish formal vs informal; propose compensation frame and concrete first-ask per prospect |
| `pitch-deck-builder` | Produce pitch deck in two artifacts — slide outline (approved first), then narrative with speaker notes. Bottoms-up market sizing. Honest competitive and traction framing |
| `investor-outreach-drafter` | Draft personalized cold/warm/LinkedIn variants per High-priority prospect plus cohort templates for Medium; voice-matched; under 100 words first touch; 4-message sequence per prospect |

## Recommended Flow

**In order:**

1. **`funding-landscape-researcher`** — first skill. Expect 45–75 minutes. Surfaces the real menu of options and trims to 1–3 finalists. Also decides whether equity is even a finalist path. Output: `outputs/funding-landscape-overview.md` plus optional diff to `global/context/competitive-landscape.md`.

2. **`investor-prospector`** (if equity is a finalist) and **`advisor-prospector`** (independent) — can run in parallel. Investor prospecting produces 15–30 qualified named targets; advisor prospecting produces 5–12 organized by gap. Outputs: `outputs/investor-prospect-list.md` and `outputs/advisor-prospect-list.md`.

3. **`pitch-deck-builder`** — third. Requires the landscape overview plus the core global context. Two-artifact output requires two founder approvals (outline, then narrative). Outputs: `outputs/pitch-deck-outline.md` and `outputs/pitch-deck-narrative.md`.

4. **`investor-outreach-drafter`** — last. Requires the prospect list, deck outline, and `brand-voice.md` (hard stop). Output: `outputs/investor-outreach-drafts.md`.

**Parallelism:** Steps 2 and 3 can overlap once the landscape is set. Step 4 depends on both.

**If pre-Project-02 (no `brand-voice.md`):** `pitch-deck-builder` proceeds with generic professional voice and flags the gap. `investor-outreach-drafter` hard-stops. Best to schedule Project 02 before reaching Step 4.

**On re-run:** All skills detect existing outputs and surface deltas. Re-run triggers are specific per skill (time elapsed, new competitive event, new traction milestone, runway threshold). Check each output's `re_run_trigger` field.

## Outputs

All saved in `projects/11-fundraising-prep/outputs/`:

- `funding-landscape-overview.md` — stage call, founder priorities, source options (long list), tradeoff matrix, 1–3 finalist paths, competitive signal surfaced (from `funding-landscape-researcher`)
- `investor-prospect-list.md` — ranked 15–30 High/Medium prospects with archetype, rubric scoring, warm-intro hypotheses, portfolio-conflict notes, High-priority dossiers (from `investor-prospector`)
- `advisor-prospect-list.md` — gap matrix, formal/informal slot plan, 5–12 prospects with compensation frame and concrete first-ask per target (from `advisor-prospector`)
- `pitch-deck-outline.md` — slide-by-slide outline: purpose, key claim, evidence required, confidence, evidence gaps (from `pitch-deck-builder`)
- `pitch-deck-narrative.md` — full narrative per slide with speaker notes; honesty appendix documenting what the deck doesn't claim (from `pitch-deck-builder`)
- `investor-outreach-drafts.md` — per-prospect cold / warm-intro / LinkedIn drafts plus cohort templates and 4-message follow-up sequences; voice-matched (from `investor-outreach-drafter`)

**Writes to `global/context/`:** `competitive-landscape.md` — updated by `funding-landscape-researcher` via `context-writer` when research surfaces new signal (skipped otherwise).

**Cross-project consumption:** Project 12 (financial modeling) may reference `investor-prospect-list.md` for cap-table and dilution modeling.

## Validation

This project is in a workable state when:

- `funding-landscape-overview.md` exists with an explicit stage call, a founder-priority ranking, 1–3 named finalist paths, and a `competitive_landscape_updated` frontmatter field (yes or no).
- `investor-prospect-list.md` (if equity is a finalist) exists with 15–30 High/Medium prospects, each carrying archetype, rubric scoring, warm-intro hypothesis, and portfolio-conflict classification.
- `advisor-prospect-list.md` exists with a gap matrix covering all six categories, 2–3 target gaps explicitly selected, and 5–12 prospects with concrete first-asks.
- `pitch-deck-outline.md` exists with 12–16 slides, each carrying purpose / key claim / evidence / confidence. Evidence gaps are explicitly listed.
- `pitch-deck-narrative.md` exists, conforms to the outline, carries speaker notes per slide, and includes an Honesty Appendix.
- `investor-outreach-drafts.md` exists with first-touch messages under 100 words, non-obvious personalization hooks per High prospect, and a 4-message follow-up sequence per prospect.

A good Project 11 outcome is one where the founder could start outreach tomorrow and defend every claim in their deck, every number in their market sizing, every prospect on their target list, and every advisor commitment — all with cited evidence.

**Note on scope:** This project does not deliver fundraising itself (that is conversations the founder has, not files). It does not provide legal advice (term sheet review requires counsel). It does not model dilution and cap tables in detail (Project 12 does). And it does not produce a designed deck — the narrative is ready for a designer, Canva, Pitch, or Keynote, but visual polish is the founder's (or a designer's) job downstream.

---

## Don't See What You Need?

The skills in this project cover the most common tasks for this stage, but they are not exhaustive.
If you need a capability that isn't covered, Claude Code includes two native built-in tools for this:

- **Skill creator** — Claude Code's built-in skill authoring tool. Use it to create a new custom skill
  and save it in this project's `.claude/skills/` directory (project-only) or in the root
  `.claude/skills/` directory (available across all projects). Fundraising-adjacent skills to consider:
  data-room-preparer, investor-update-drafter, term-sheet-reader.
- **MCP builder** — Claude Code's built-in MCP server builder. Use it if you want to connect
  Claude Code to an external tool or API. Most relevant here when you want to integrate an investor-CRM
  (Affinity, Attio), a prospect-research tool (Signal NFX, PitchBook), or a scheduling tool for
  investor calls.

Custom skills and MCP servers you create will live in your private fork and will not affect
the upstream repo. If you build something you think would benefit other founders, see CONTRIBUTING.md
for how to suggest it.
