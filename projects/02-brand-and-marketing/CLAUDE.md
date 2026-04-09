# Project 02 — Brand Strategy & Voice

## Purpose

This is where you turn the research from Project 01 into the brand's strategic foundation: a defensible positioning statement, a messaging hierarchy that speaks to both buyer and user, and a brand voice that downstream projects can read as ground truth.

By the end of this project you will know: what claim you are making to the market and why it is defensible against the named gaps in `competitive-landscape.md`, how you will talk about the product to the people who buy it versus the people who use it, and how the brand sounds in writing — concretely enough that any future marketing, sales, or product copy can be calibrated against it.

This is not where you decide your visual identity (Project 03) or where you build content campaigns (Project 04). This is the strategic brief that those projects need before they can do their work.

## Prerequisites

Complete Project 01 (market research). The skills here load `icp.md`, `competitive-landscape.md`, `startup-hypothesis.md`, and `founder-profile.md` and will not run if any of the first three are missing or empty.

## Global Context Files

**Loads:** `icp.md`, `competitive-landscape.md`, `startup-hypothesis.md`, `founder-profile.md`

**Writes:** `brand-voice.md`

## How This Project Works

Unlike Project 01 — where research streams could run in parallel — Project 02 is **strictly linear**. Each step depends on the previous one. You cannot meaningfully build a messaging hierarchy without a positioning statement, and you cannot meaningfully define brand voice without knowing what the brand is positioning itself as and what it is saying.

The three skills run in order:

1. **`positioning-strategist`** — reads the research, articulates a defensible positioning statement using established frameworks, and forces you to take a real position rather than a vague differentiation claim.
2. **`messaging-architect`** — builds the messaging hierarchy on top of the positioning: headline value prop, supporting pillars, proof points, objection handlers, calibrated separately to the buyer and the user.
3. **`brand-voice-developer`** — defines how the brand sounds: voice attributes, tone-by-context, do's and don'ts, vocabulary preferences, and worked before/after rewrites. Writes the distilled version to `global/context/brand-voice.md` for downstream projects.

All skills are conversational. They ask you one question at a time, quote the research back to you, and show you a preview of any file before writing it. You always have the final say.

**Iteration is expected.** After running `brand-voice-developer`, you may find that the voice you arrived at no longer feels coherent with the positioning or messaging you wrote earlier. That is a signal to revisit those skills, not to paper over the gap. Coherence across the three is the point.

## Skills

| Skill | Description |
|---|---|
| `positioning-strategist` | Articulate a defensible positioning statement grounded in real competitive gaps |
| `messaging-architect` | Build the messaging hierarchy: value prop, pillars, proof points, objection handlers — split between buyer and user |
| `brand-voice-developer` | Define brand voice attributes, tone-by-context, and vocabulary; write the distilled voice guide to global context |

## Recommended Flow

Run the skills in numbered order. Do not skip ahead.

1. **`positioning-strategist`** — first, always. Output is the foundation everything else builds on. Expect this to take more than one session if the founder is wrestling with a hard differentiation question.
2. **`messaging-architect`** — only after positioning is written and approved. The skill will refuse to run without `outputs/positioning-statement.md` present.
3. **`brand-voice-developer`** — only after both prior outputs exist. The skill will refuse to run without both `outputs/positioning-statement.md` and `outputs/messaging-framework.md` present. This is the skill that writes to global context.

If you finish the brand voice and feel that an earlier output no longer fits, go back. A 30-minute revision of the positioning statement is much cheaper than building Projects 03, 04, and 05 against a brand that does not hang together.

## Outputs

All saved in `projects/02-brand-and-marketing/outputs/`:

- `positioning-statement.md` — Positioning statement, 5 Pieces breakdown, market category, who the product is **not** for, and a competitor positioning contrast (from `positioning-strategist`)
- `messaging-framework.md` — Headline value prop, pillars with proof points, buyer-tier and user-tier variants, key vocabulary, objection handlers (from `messaging-architect`)
- `brand-voice-guide.md` — Full draft of the brand voice with worked before/after rewrites, rationale, and audit trail (from `brand-voice-developer`)

And the following global context update (written via the `context-writer` skill with preview and approval):

- `global/context/brand-voice.md` — The distilled brand voice for downstream projects, written by `brand-voice-developer`

## Validation

This project is complete when:

- `global/context/brand-voice.md` exists and contains specific voice attributes (3–5), explicit do's and don'ts, vocabulary preferences pulled from `icp.md`'s "How They Talk About the Problem" section, and at least 2 worked before/after rewrites
- `outputs/messaging-framework.md` is calibrated to **both** the buyer (VP Sales Enablement / RevOps) and the user (new sales rep) tiers from `icp.md` — not a single generic message
- `outputs/positioning-statement.md` takes a defensible position against the cross-tool capability gap identified in `competitive-landscape.md` (generic AI feedback) and explicitly names who the product is **not** for

A good Project 02 outcome is one where the three documents reinforce each other — where the voice sounds like the kind of company that would say the messaging, and the messaging sounds like the kind of company that would take the position. If they read as three disconnected documents, the project is not done yet.

**Note on scope:** Channel strategy (which channels to invest in, in what order, with what cadence) is handled in Project 04 (Inbound Marketing), not here. Project 04 reads `brand-voice.md` and `icp.md` to make those decisions co-located with execution. Do not look for channel strategy in this project's outputs.

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
