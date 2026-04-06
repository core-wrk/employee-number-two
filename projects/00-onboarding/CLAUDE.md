# Project 00 — Setup & Onboarding

## Purpose

This is your starting point. Project 00 is a structured workshop that builds your founder profile and startup hypothesis through conversation, walks you through the repo, and gets your private fork configured. Everything you do in Projects 01-12 builds on what you create here.

This project does not hand you templates to fill in. Each skill works with you conversationally — asking one question at a time, listening to your answers, and adapting the conversation based on what you share. The goal is to produce context files that genuinely reflect who you are and what you are building, not checkbox outputs.

## Prerequisites

None — this is the starting point. You should have Claude Code installed and a GitHub account ready.

## Global Context Files

**Writes:** `founder-profile.md`, `startup-hypothesis.md`

The `journey-assessor` skill (for returning founders) may also write additional global context files based on existing materials you bring.

## How This Project Works

Skills in this project are conversational. They ask you one question at a time and shape the follow-up based on what you share. There is no template to fill in and no form to complete. Think of it as a structured working session with a thoughtful collaborator.

When a skill finishes its conversation, it synthesizes everything into the appropriate output file and shows you a preview before writing anything. You always have the final say.

When you feel done with onboarding — you have completed your profile and hypothesis, explored the repo, and set up your fork — ask for your onboarding summary. It is not generated automatically. You trigger it when you are ready.

## Skills

| Skill | Description |
|---|---|
| `profile-builder` | Build your founder profile through a guided conversation |
| `hypothesis-builder` | Develop your startup hypothesis through structured dialogue |
| `repo-guide` | Interactive walkthrough of how this repo works |
| `fork-setup-guide` | Set up your private fork with guardrails |
| `toolstack-advisor` | Lean tool recommendations scoped to this repo's workflow |
| `journey-assessor` | For returning founders: assess where you are and fast-track setup |

## Recommended Flow

**If you are starting fresh:**
1. Start with `repo-guide` to understand the workspace
2. Run `fork-setup-guide` to configure your private fork
3. Run `profile-builder` to create your founder profile
4. Run `hypothesis-builder` to articulate your startup hypothesis
5. Optionally run `toolstack-advisor` for tool recommendations by project stage
6. When you feel done, ask for your onboarding summary

**If you are a returning founder with existing context:**
1. Start with `journey-assessor` — it will interview you about where you are, help pre-populate global context files from your existing materials, review what you would be skipping, and recommend which project to start at
2. The journey assessor will still ensure your founder profile and startup hypothesis are created — these are required by every subsequent project

## Outputs

- `onboarding-summary.md` — Recap of onboarding decisions and next steps (founder-triggered)
- `toolstack-recommendations.md` — Lean tool recommendations by project stage (if `toolstack-advisor` is used)
- `journey-assessment.md` — Assessment for returning founders (if `journey-assessor` is used)

## Validation

When this project is complete, `global/context/founder-profile.md` and `global/context/startup-hypothesis.md` must exist and contain substantive content. Every subsequent project (01-12) checks for these files before starting. If they are missing or empty, those projects will not proceed and will direct you back here.

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
