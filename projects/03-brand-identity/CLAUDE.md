# Project 03 — Brand Identity & Visual Design System

## Purpose

Develop the visual language of the brand. Define color palette, typography, logo direction, and a design system that can be applied consistently across all assets.

## Prerequisites

Complete Project 02 (brand and marketing).

## Global Context Files

**Loads:** `brand-voice.md`, `icp.md`
**Writes:** `brand-identity.md`

## Skills

| Skill | Description |
|---|---|
| `color-system-builder` | Define color palette with psychology and accessibility |
| `typography-selector` | Recommend typefaces and typographic hierarchy |
| `logo-direction-advisor` | Produce a structured logo creative brief |
| `brand-identity-synthesizer` | Terminal synthesis step — consolidates the three primitives into the design system, brand kit, and global brand identity |

The first three skills can be run in any order; each detects sibling outputs at runtime and adapts. `brand-identity-synthesizer` runs last and requires all three upstream outputs to exist before it will proceed.

## Outputs

- `color-palette.md`
- `typography-guide.md`
- `logo-concepts.md`
- `design-system.md`
- `brand-kit-instructions.md`

**Note:** Claude Code cannot render or generate images. This project produces structured design briefs, hex codes, font recommendations, and creative direction documents that you take to any design tool or hand to a designer.

**The brand kit is platform-agnostic and machine-consumable.** Both `brand-kit-instructions.md` and the global `brand-identity.md` contain a canonical Design Tokens JSON block that any downstream skill or tool can parse without ambiguity — including future skills like `/canvas-design` and the content/product workflows in Projects 04 and 07. The kit is not scoped to Canva, Figma, or any single tool.

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
