# Global Context

This directory contains shared context files used across multiple projects. Each project's `CLAUDE.md` specifies which files from `global/context/` to load.

## Context Files

| File | Description |
|---|---|
| `founder-profile.md` | Founder background, goals, and working style |
| `startup-hypothesis.md` | Problem statement, proposed solution, initial assumptions |
| `icp.md` | Ideal Customer Profile |
| `brand-voice.md` | Brand voice and tone guide |
| `brand-identity.md` | Colors, typography, logo direction, style rules |
| `product-overview.md` | High-level product summary and value proposition |
| `competitive-landscape.md` | Competitor map and capability gaps |
| `pricing-model.md` | Pricing and packaging decisions |
| `company-profile.md` | Legal entity, domain, structure |

## Templates

The `templates/` directory contains reusable document templates referenced by project skills.

## Usage

- These files are populated as you work through projects in sequence.
- You can edit any file directly at any time.
- The `context-loader` skill reads only the files relevant to your current project.
- The `context-writer` skill updates these files with a diff preview before saving.
