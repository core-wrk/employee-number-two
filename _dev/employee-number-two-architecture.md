# Employee Number Two — Repository Architecture

## Overview

Employee Number Two is a Claude Code repository that guides startup founders through the full journey from idea validation to fundraising. It is structured as a monorepo with project-based subdirectories, a shared global context layer, and a library of reusable skills.

The public repo on GitHub is effectively read-only. Founders fork it to their own GitHub account, work through projects in sequence, and commit their outputs to their private fork. Each project builds on deliverables from prior projects. Shared context files accumulate over time and are referenced by subsequent projects automatically.

Community contributions (new skills, templates, project ideas) flow back through GitHub Pull Requests. The maintainer reviews and approves all PRs before anything merges to `main`. This architecture document and all other development notes live in `_dev/`, which is gitignored and never published.

---

## Guiding Design Principles

1. **Progressive context loading.** No project loads more context than it needs. Skills use progressive disclosure: SKILL.md stays lean and references deeper files only when needed.
2. **Human-readable shared state.** All shared context lives in flat text or JSON files that a founder can read, edit, and version-control directly.
3. **Graceful degradation.** Every agent works without third-party tools. Where a tool (Apollo, HubSpot, ZoomInfo) would amplify results, the agent informs the founder and explains the benefit.
4. **Project specificity within global coherence.** Global context files capture what needs to be shared. Project-scoped files stay inside their project directory.
5. **Founder is the decision-maker.** Agents surface options, tradeoffs, and recommendations. They do not make irreversible decisions autonomously.

---

## Repository Structure

```
employee-number-two/
│
├── CLAUDE.md                          # Root: repo orientation, how to navigate, global conventions
├── README.md                          # Human-readable onboarding for GitHub
├── CONTRIBUTING.md                    # How to fork, use, and contribute back to the repo
│
├── global/                            # Shared context — read by multiple projects
│   ├── CLAUDE.md                      # Instructions for loading global context
│   ├── context/
│   │   ├── founder-profile.md         # Name, background, goals, risk tolerance
│   │   ├── startup-hypothesis.md      # Problem statement, proposed solution, initial assumptions
│   │   ├── icp.md                     # Ideal Customer Profile (built in Project 01, refined over time)
│   │   ├── brand-voice.md             # Brand voice guide (built in Project 03)
│   │   ├── brand-identity.md          # Colors, fonts, logo direction, style rules (Project 03)
│   │   ├── product-overview.md        # High-level product summary + value proposition (Project 05)
│   │   ├── competitive-landscape.md   # Competitor map, capability gaps (Project 01)
│   │   ├── pricing-model.md           # Pricing and packaging decisions (Project 07)
│   │   └── company-profile.md         # Legal name, domain, structure (Project 08)
│   └── templates/
│       ├── market-research-report.md
│       ├── competitive-analysis.md
│       ├── one-pager.md
│       └── email-outreach.md
│
├── _dev/                              # Private development notes — gitignored, never published
│   ├── README.md                      # Explains purpose of this directory
│   ├── decisions/                     # Architecture decision records (ADRs)
│   ├── skill-refinement-notes/        # Per-skill testing notes and iteration log
│   ├── project-refinement-notes/      # Per-project feedback and improvement backlog
│   └── roadmap.md                     # Internal roadmap for repo development
│
├── .claude/
│   └── skills/                        # Global skills available across all projects
│       ├── web-researcher/
│       │   └── SKILL.md
│       ├── context-loader/
│       │   └── SKILL.md
│       ├── context-writer/
│       │   └── SKILL.md
│       ├── document-formatter/
│       │   └── SKILL.md
│       └── third-party-advisor/
│           └── SKILL.md
│
└── projects/
    ├── 01-market-research/
    ├── 02-brand-and-marketing/
    ├── 03-brand-identity/
    ├── 04-inbound-marketing/
    ├── 05-outbound-sales/
    ├── 06-product-management/
    ├── 07-product-development/
    ├── 08-beta-and-user-testing/
    ├── 09-pricing-and-packaging/
    ├── 10-legal-and-company-formation/
    ├── 11-fundraising-prep/
    └── 12-financial-modeling/
```

---

## Global Context Files — What They Are and Who Writes Them

| File | Written By | Read By |
|---|---|---|
| `founder-profile.md` | Founder (manually, on setup) | All projects |
| `startup-hypothesis.md` | Project 01 agent | All projects |
| `icp.md` | Project 01 agent, refined in 02 and 05 | 02, 04, 05, 08, 11 |
| `brand-voice.md` | Project 02 agent | 03, 04, 05 |
| `brand-identity.md` | Project 03 agent | 04, 07 |
| `product-overview.md` | Project 06 agent | 05, 07, 08, 11, 12 |
| `competitive-landscape.md` | Project 01 agent, updated in 11 | 02, 05, 11, 12 |
| `pricing-model.md` | Project 09 agent | 11, 12 |
| `company-profile.md` | Project 10 agent | 11, 12 |

---

## Global Skills

These skills live in `.claude/skills/` and are available across all projects.

### `web-researcher`
General-purpose web search and synthesis. Used by multiple project-specific agents when they need current information. Includes instructions for evaluating source credibility, avoiding hallucination, and formatting findings as structured markdown.

### `context-loader`
Reads the relevant subset of `global/context/` files for the current task and injects them into working context. Knows which files are relevant to which project types. Prevents over-loading context with irrelevant global state.

### `context-writer`
After a project produces a deliverable that should update global context, this skill handles writing or updating the appropriate file in `global/context/` in a consistent, human-readable format. Includes a diff-preview step so the founder can review before the file is overwritten.

### `document-formatter`
Applies consistent markdown formatting, heading structure, and file naming conventions across all output documents. Ensures deliverables are clean, readable, and version-control friendly.

### `third-party-advisor`
When a task would benefit from a third-party tool (Apollo, HubSpot, ZoomInfo, Stripe, Clerk, etc.), this skill surfaces the tool name, what it does, why it would help, approximate cost tier, and what the founder would need to do to connect it. Does not require the tool to be present.

---

---

## Private Development Directory (`_dev/`)

The `_dev/` directory is for your use as the repo maintainer. It is listed in `.gitignore` and will never be published to the public GitHub repo. Its purpose is to hold working notes, iteration logs, and architecture thinking that inform how the repo evolves without exposing that thinking to the community.

```
_dev/
├── README.md                        # What this directory is and how to use it
├── decisions/                       # Architecture Decision Records (ADRs)
│   └── adr-template.md             # Standard format for recording decisions
├── skill-refinement-notes/          # One file per skill, tracking what works and what doesn't
│   └── _template.md
├── project-refinement-notes/        # One file per project, tracking feedback and backlog
│   └── _template.md
└── roadmap.md                       # Internal roadmap: what's planned, what's in progress
```

**`.gitignore` entry:**
```
_dev/
```

This is the right place to save things like: notes from testing a skill with a real founder, observations about where the context-loader over- or under-loads, decisions about why a skill was scoped the way it was, and ideas for new skills or projects that aren't ready to build yet. Keeping this in the repo (rather than a separate notes app) means it stays co-located with the code it's about and benefits from version control on your local machine.

---

## Project Definitions

---

### Project 01 — Market Research & Problem Validation

**Purpose:** Validate the founder's hypothesis. Understand the problem deeply before building anything. Identify who experiences the pain, how severely, and what already exists to solve it.

**CLAUDE.md loads:** `founder-profile.md`, `startup-hypothesis.md`

**Outputs to global context:** `startup-hypothesis.md` (refined), `icp.md` (v1), `competitive-landscape.md`

**Project structure:**
```
01-market-research/
├── CLAUDE.md
├── outputs/
│   ├── reddit-research-report.md
│   ├── news-sentiment-report.md
│   ├── competitor-analysis.md
│   ├── icp-draft.md
│   └── naming-availability-report.md
└── .claude/
    └── skills/
        ├── reddit-researcher/
        │   ├── SKILL.md
        │   └── references/
        │       └── subreddit-list-template.md
        ├── news-analyst/
        │   └── SKILL.md
        ├── competitor-mapper/
        │   ├── SKILL.md
        │   └── references/
        │       └── competitive-analysis-framework.md
        ├── icp-builder/
        │   ├── SKILL.md
        │   └── references/
        │       └── icp-template.md
        └── naming-validator/
            ├── SKILL.md
            └── references/
                └── naming-checklist.md
```

**Agents / Skills:**

`reddit-researcher` — Searches Reddit for threads related to the problem space. Surfaces posts expressing frustration, workarounds, unmet needs. Formats findings into a structured report with signal strength ratings. Informs founder about Reddit's API and tools like Gummy Search as amplifiers.

`news-analyst` — Searches news sources and industry publications for coverage of the problem domain. Tracks sentiment trends, emerging players, regulatory signals, and market momentum. Produces a narrative summary with key quotes and source links.

`competitor-mapper` — Builds a structured competitor matrix: who they are, what they do, pricing (where available), what users say about them, and where the gaps are. Uses the competitive-analysis-framework.md reference for consistent structure.

`icp-builder` — Synthesizes research outputs into a structured Ideal Customer Profile. Includes demographic and firmographic attributes, pain intensity ranking, buying behavior signals, and decision-making context. Writes v1 of `global/context/icp.md`.

`naming-validator` — Guides the founder through product naming. Checks domain availability via web search, searches USPTO trademark database (via web), and surfaces any obvious conflicts. Produces a naming availability report with recommended and flagged names.

---

### Project 02 — Brand Voice & Marketing Strategy

**Purpose:** Translate market research into a coherent brand position and messaging framework. Define who the founder is talking to, what they are saying, and why it will resonate.

**CLAUDE.md loads:** `icp.md`, `competitive-landscape.md`, `startup-hypothesis.md`, `founder-profile.md`

**Outputs to global context:** `brand-voice.md`

**Project structure:**
```
02-brand-and-marketing/
├── CLAUDE.md
├── outputs/
│   ├── positioning-statement.md
│   ├── messaging-framework.md
│   └── brand-voice-guide.md
└── .claude/
    └── skills/
        ├── positioning-strategist/
        │   ├── SKILL.md
        │   └── references/
        │       ├── positioning-frameworks.md
        │       └── positioning-quality-rubric.md
        ├── messaging-architect/
        │   ├── SKILL.md
        │   └── references/
        │       ├── messaging-hierarchy-template.md
        │       └── proof-point-types.md
        └── brand-voice-developer/
            ├── SKILL.md
            └── references/
                ├── voice-attribute-examples.md
                └── brand-voice-template.md
```

**Scope change (2026-04-07):** `marketing-channel-strategy.md` was originally scoped to Project 02 but moved to Project 04 (Inbound Marketing). Channel selection is more naturally co-located with channel execution, where the founder is already deciding cadence, format, and content. Project 02 retains positioning, messaging, and voice; Project 04 now owns both the strategy *and* the execution of channel decisions, reading `brand-voice.md` and `icp.md` to make the call.

**Agents / Skills:**

`positioning-strategist` — Works with the founder to articulate a clear positioning statement using established frameworks (category, differentiation, target, benefit). Surfaces competitive positioning to ensure uniqueness.

`messaging-architect` — Builds the messaging hierarchy: primary value proposition, supporting pillars, proof points, objection handlers. Tailored to each ICP tier from `icp.md`.

`brand-voice-developer` — Guides the founder through defining their brand personality and voice: tone attributes, what the brand sounds like, what it does not sound like, and example before/after rewrites. Output becomes `global/context/brand-voice.md`.

---

### Project 03 — Brand Identity & Visual Design System

**Purpose:** Develop the visual language of the brand. Define color palette, typography, logo direction, and a design system that can be applied consistently across all assets.

**CLAUDE.md loads:** `brand-voice.md`, `icp.md`

**Outputs to global context:** `brand-identity.md`

**Project structure:**
```
03-brand-identity/
├── CLAUDE.md
├── outputs/
│   ├── color-palette.md
│   ├── typography-guide.md
│   ├── logo-concepts.md
│   ├── design-system.md
│   └── brand-kit-instructions.md
└── .claude/
    └── skills/
        ├── color-system-builder/
        │   ├── SKILL.md
        │   └── references/
        │       └── color-psychology-guide.md
        ├── typography-selector/
        │   └── SKILL.md
        └── logo-direction-advisor/
            ├── SKILL.md
            └── references/
                └── logo-brief-template.md
```

**Note on visual outputs:** Claude Code cannot render or generate images. This project produces structured design briefs, hex codes, font recommendations, and creative direction documents that the founder takes to a design tool (Canva, Figma) or a designer. The `brand-kit-instructions.md` output explains how to build a Canva brand kit from the specifications produced here.

---

### Project 04 — Inbound Marketing & Content Engine

**Purpose:** Build an organic content strategy and execute content across channels. Drive awareness and waitlist signups before launch.

**CLAUDE.md loads:** `brand-voice.md`, `brand-identity.md`, `icp.md`, `startup-hypothesis.md`

**Outputs:** Channel-specific content drafts saved within this project. Waitlist management context saved to `outputs/waitlist-tracker.md`. Channel strategy (which channels to invest in, in what order, with what cadence) is also produced here, in `outputs/marketing-channel-strategy.md` — moved from Project 02 on 2026-04-07 so that channel selection sits alongside channel execution rather than being decoupled from it. Channel strategy should be produced before content production begins, reading `global/context/brand-voice.md` and `global/context/icp.md` (especially the "Where to Find Them" section) to make grounded prioritization decisions.

**Project structure:**
```
04-inbound-marketing/
├── CLAUDE.md
├── outputs/
│   ├── marketing-channel-strategy.md
│   ├── content-calendar.md
│   ├── waitlist-tracker.md
│   ├── blog/
│   ├── linkedin/
│   ├── reddit-engagement/
│   ├── youtube/
│   └── technical-reports/
└── .claude/
    └── skills/
        ├── content-strategist/
        │   ├── SKILL.md
        │   └── references/
        │       └── content-calendar-template.md
        ├── blog-writer/
        │   └── SKILL.md
        ├── linkedin-writer/
        │   ├── SKILL.md
        │   └── references/
        │       └── linkedin-post-formats.md
        ├── reddit-engager/
        │   ├── SKILL.md
        │   └── references/
        │       ├── reddit-engagement-rules.md
        │       └── authentic-voice-guide.md
        ├── youtube-scriptwriter/
        │   ├── SKILL.md
        │   └── references/
        │       └── youtube-script-template.md
        ├── technical-report-writer/
        │   └── SKILL.md
        └── waitlist-manager/
            ├── SKILL.md
            └── references/
                └── waitlist-qualification-criteria.md
```

**Agents / Skills:**

`reddit-engager` — Distinct from `reddit-researcher` in Project 01. This agent drafts authentic, value-adding responses to Reddit threads in the founder's voice. It does not post directly (Claude Code cannot do that) but produces ready-to-post drafts with the target thread URL and the recommended timing. Includes guardrails against spammy or promotional-sounding language.

`linkedin-writer` — Produces LinkedIn posts in multiple formats (text post, document post, poll concept) tailored to LinkedIn's algorithm patterns. Loads brand voice from global context. Includes post length guidance and recommended hashtag strategy.

`youtube-scriptwriter` — Produces full video scripts including hook, body, CTA, and chapter markers. Calibrated to YouTube search intent vs. awareness content.

`waitlist-manager` — Tracks waitlist signups captured through external forms (Google Forms, HubSpot Forms, Typeform). Founder pastes in new signup data; agent qualifies each against the ICP, tags by tier, and maintains `waitlist-tracker.md` as the canonical lead list for user testing outreach.

---

### Project 05 — Outbound Sales & Prospecting

**Purpose:** Identify and reach high-fit prospects. Generate personalized outreach. Build and manage a pipeline of design partners and early customers. Feed leads into CRM if available.

**CLAUDE.md loads:** `icp.md`, `brand-voice.md`, `product-overview.md` (once available), `competitive-landscape.md`

**Outputs:** Lead lists, outreach drafts, pre-call briefs — all within this project. Deal context summaries may be shared with Project 08 (beta testing).

**Project structure:**
```
05-outbound-sales/
├── CLAUDE.md
├── outputs/
│   ├── prospect-list.md
│   ├── outreach-drafts/
│   ├── pre-call-briefs/
│   └── pipeline-tracker.md
└── .claude/
    └── skills/
        ├── prospect-researcher/
        │   ├── SKILL.md
        │   └── references/
        │       └── lead-qualification-rubric.md
        ├── email-drafter/
        │   ├── SKILL.md
        │   └── references/
        │       ├── outreach-sequence-template.md
        │       └── personalization-variables.md
        ├── pre-call-brief-builder/
        │   ├── SKILL.md
        │   └── references/
        │       └── pre-call-brief-template.md
        ├── design-partner-advisor/
        │   └── SKILL.md
        └── crm-sync-advisor/
            └── SKILL.md
```

**Agents / Skills:**

`prospect-researcher` — Uses web search to identify individuals and companies that match the ICP. Builds a structured prospect list with firmographic data, contact info (where publicly available), and ICP tier rating. Informs the founder about Apollo and ZoomInfo as tools that would accelerate this step significantly.

`email-drafter` — Produces personalized outreach email drafts for each prospect. Loads the prospect's background from the prospect list, applies brand voice, and generates a draft. Saves to `outreach-drafts/`. Informs the founder about Gmail and Outlook integrations that would allow direct draft injection.

`pre-call-brief-builder` — For any prospect that has agreed to a call, produces a structured pre-call brief: company background, role context, inferred pain points, suggested talking points, questions to ask, and what success looks like for this call (validation, not selling).

`design-partner-advisor` — Specializes in reframing sales conversations as design partnership conversations. Helps the founder articulate what a design partner gets (influence over product direction, early access, founder attention) and helps draft design partner agreements at a conceptual level.

`crm-sync-advisor` — Guides the founder through manually organizing their prospect and deal data in a CRM-compatible format. Produces a structured CSV of contacts and companies that can be imported into HubSpot, Salesforce, or Airtable. Informs about native CRM integrations.

---

### Project 06 — Product Management

**Purpose:** Translate validated market needs into a structured product requirements document. Define epics, prioritize them, and create a roadmap that guides development.

**CLAUDE.md loads:** `icp.md`, `product-overview.md` (bootstrapped here if not yet written), `competitive-landscape.md`

**Outputs to global context:** `product-overview.md`

**Project structure:**
```
06-product-management/
├── CLAUDE.md
├── outputs/
│   ├── product-requirements-document.md   # Goes to global context summary
│   ├── epic-list.md
│   └── roadmap.md
└── .claude/
    └── skills/
        ├── prd-builder/
        │   ├── SKILL.md
        │   └── references/
        │       ├── prd-template.md
        │       └── user-story-guide.md
        ├── epic-definer/
        │   ├── SKILL.md
        │   └── references/
        │       └── epic-template.md
        └── roadmap-builder/
            ├── SKILL.md
            └── references/
                └── roadmap-sequencing-principles.md
```

---

### Project 07 — Product Development & Engineering

**Purpose:** Translate epics into detailed engineering requirements. Guide the founder (or their team or coding agent) through implementation. Run QA and UX review after each epic.

**CLAUDE.md loads:** `product-overview.md`, `brand-identity.md` (for UX/design review)

**Outputs:** All outputs are project-scoped. Epic requirements documents, QA reports, and UX review notes do not propagate to global context.

**Project structure:**
```
07-product-development/
├── CLAUDE.md
├── outputs/
│   ├── epic-requirements/
│   │   ├── epic-01-requirements.md
│   │   ├── epic-02-requirements.md
│   │   └── ...
│   ├── qa-reports/
│   └── ux-review-reports/
└── .claude/
    └── skills/
        ├── epic-requirements-builder/
        │   ├── SKILL.md
        │   └── references/
        │       ├── functional-requirements-template.md
        │       └── non-functional-requirements-guide.md
        ├── qa-reviewer/
        │   ├── SKILL.md
        │   └── references/
        │       └── qa-checklist.md
        └── ux-design-reviewer/
            ├── SKILL.md
            └── references/
                ├── ux-heuristics.md
                └── brand-adherence-checklist.md
```

**Agents / Skills:**

`epic-requirements-builder` — Takes an epic from `epic-list.md` and drills it into a full requirements document: functional requirements, non-functional requirements, acceptance criteria, edge cases, and dependencies. The goal is to minimize degrees of freedom for whoever implements it.

`qa-reviewer` — Reviews implemented code or feature descriptions against the epic requirements. Produces a structured QA report: passed criteria, failed criteria, edge cases to re-test, and a sign-off recommendation.

`ux-design-reviewer` — Evaluates product screens or feature flows against UX heuristics and the brand identity spec from `global/context/brand-identity.md`. Produces a UX review report with specific, actionable feedback.

---

### Project 08 — Beta Testing & User Feedback

**Purpose:** Recruit beta users from the waitlist. Structure the feedback collection process. Synthesize feedback into actionable product inputs.

**CLAUDE.md loads:** `icp.md`, `product-overview.md`, `waitlist-tracker.md` (from Project 04 outputs)

**Outputs:** Beta feedback reports (project-scoped). Validated insights feed into Project 09 and Project 11.

**Project structure:**
```
08-beta-and-user-testing/
├── CLAUDE.md
├── outputs/
│   ├── beta-outreach-drafts/
│   ├── feedback-survey-templates/
│   ├── feedback-synthesis-reports/
│   └── beta-user-tracker.md
└── .claude/
    └── skills/
        ├── beta-recruiter/
        │   └── SKILL.md
        ├── feedback-collector/
        │   ├── SKILL.md
        │   └── references/
        │       └── survey-design-guide.md
        ├── feedback-synthesizer/
        │   ├── SKILL.md
        │   └── references/
        │       └── feedback-tagging-taxonomy.md
        └── cs-engager/
            ├── SKILL.md
            └── references/
                └── check-in-email-templates.md
```

**Agents / Skills:**

`beta-recruiter` — Pulls from `waitlist-tracker.md`, selects the highest-ICP-tier users, and drafts personalized beta invitation emails.

`feedback-collector` — Builds structured feedback survey templates calibrated to what the founder needs to learn at this stage (usability, value perception, willingness to pay signals, missing features).

`feedback-synthesizer` — Ingests raw feedback (the founder pastes it in or loads from a file) and produces a tagged, themed synthesis report. Tags map to product areas and ICP tiers.

`cs-engager` — Drafts structured check-in messages for beta users at defined intervals. Focused on success, not just bug reports. Surfaces engagement signals that indicate retention risk.

---

### Project 09 — Pricing & Packaging

**Purpose:** Develop a pricing and packaging model grounded in beta feedback, competitive research, and the business model requirements.

**CLAUDE.md loads:** `competitive-landscape.md`, `icp.md`, `product-overview.md`

**Outputs to global context:** `pricing-model.md`

**Project structure:**
```
09-pricing-and-packaging/
├── CLAUDE.md
├── outputs/
│   ├── pricing-strategy-options.md
│   ├── packaging-tiers.md
│   └── pricing-model-final.md
└── .claude/
    └── skills/
        ├── pricing-strategist/
        │   ├── SKILL.md
        │   └── references/
        │       ├── pricing-models-overview.md
        │       └── willingness-to-pay-analysis-guide.md
        └── packaging-designer/
            ├── SKILL.md
            └── references/
                └── tier-design-principles.md
```

---

### Project 10 — Legal & Company Formation

**Purpose:** Guide the founder through entity selection, domain acquisition, and basic legal awareness checkpoints throughout the journey.

**CLAUDE.md loads:** `founder-profile.md`, `startup-hypothesis.md`, `pricing-model.md`

**Outputs to global context:** `company-profile.md`

**Important note in CLAUDE.md:** This project does not provide legal advice. It provides frameworks, questions to ask a lawyer, and general information about options. The founder should consult a qualified attorney before making formation decisions.

**Project structure:**
```
10-legal-and-company-formation/
├── CLAUDE.md
├── outputs/
│   ├── entity-options-analysis.md
│   ├── domain-acquisition-plan.md
│   ├── banking-options-overview.md
│   └── early-legal-checklist.md
└── .claude/
    └── skills/
        ├── entity-advisor/
        │   ├── SKILL.md
        │   └── references/
        │       ├── llc-vs-scorp-vs-ccorp.md
        │       └── incorporation-services-overview.md
        ├── domain-strategist/
        │   └── SKILL.md
        ├── banking-advisor/
        │   ├── SKILL.md
        │   └── references/
        │       └── founder-banking-options.md
        └── early-legal-checker/
            ├── SKILL.md
            └── references/
                └── early-stage-legal-checklist.md
```

**Note on sequencing:** An `early-legal-checker` skill should also be available in Project 01, flagging IP assignment risks (if founder is employed elsewhere), NDA considerations for design partners, and data privacy obligations for waitlist collection. This is a cross-cutting concern that surfaces early.

---

### Project 11 — Fundraising Preparation

**Purpose:** Identify funding sources, recruit advisors, develop a pitch deck, and prepare the founder for investor conversations.

**CLAUDE.md loads:** `icp.md`, `competitive-landscape.md`, `product-overview.md`, `pricing-model.md`, `company-profile.md`, `brand-voice.md`

**Outputs:** All project-scoped except investor prospect list which may be referenced in Project 12.

**Project structure:**
```
11-fundraising-prep/
├── CLAUDE.md
├── outputs/
│   ├── funding-landscape-overview.md
│   ├── investor-prospect-list.md
│   ├── advisor-prospect-list.md
│   ├── pitch-deck-outline.md
│   └── pitch-deck-narrative.md
└── .claude/
    └── skills/
        ├── funding-landscape-researcher/
        │   ├── SKILL.md
        │   └── references/
        │       └── funding-stage-guide.md
        ├── investor-prospector/
        │   ├── SKILL.md
        │   └── references/
        │       └── investor-qualification-rubric.md
        ├── advisor-prospector/
        │   └── SKILL.md
        ├── pitch-deck-builder/
        │   ├── SKILL.md
        │   └── references/
        │       ├── pitch-deck-structure.md
        │       ├── tam-sam-som-guide.md
        │       └── social-proof-framing.md
        └── investor-outreach-drafter/
            └── SKILL.md
```

---

### Project 12 — Financial Modeling

**Purpose:** Build a dynamic financial model in markdown/CSV format that the founder can translate into a spreadsheet. Model revenue scenarios, cost structure, unit economics, and runway.

**CLAUDE.md loads:** `pricing-model.md`, `product-overview.md`, `company-profile.md`

**Outputs:** All project-scoped. Financial model files in CSV or structured markdown.

**Project structure:**
```
12-financial-modeling/
├── CLAUDE.md
├── outputs/
│   ├── revenue-model.md
│   ├── cost-structure.md
│   ├── unit-economics.md
│   ├── hiring-roadmap.md
│   ├── runway-scenarios.md
│   └── investor-metrics-summary.md
└── .claude/
    └── skills/
        ├── revenue-modeler/
        │   ├── SKILL.md
        │   └── references/
        │       └── saas-revenue-model-template.md
        ├── unit-economics-builder/
        │   ├── SKILL.md
        │   └── references/
        │       └── ltv-cac-framework.md
        ├── hiring-roadmap-builder/
        │   └── SKILL.md
        └── scenario-planner/
            ├── SKILL.md
            └── references/
                └── scenario-planning-variables.md
```

---

## Cross-Cutting Skills Available in Multiple Projects

Some skills are needed in more than one project. Rather than duplicating, these live in `.claude/skills/` at the root and are available everywhere.

| Skill | Used In |
|---|---|
| `web-researcher` | 01, 02, 05, 11 |
| `context-loader` | All |
| `context-writer` | 01, 02, 03, 06, 09, 10 |
| `document-formatter` | All |
| `third-party-advisor` | 01, 05, 08, 11 |
| `email-drafter` (global variant) | 05, 08 |

Project-specific skills that share a name (e.g., `pricing-strategist` appears in both 02 and 09) are intentionally distinct — the 09 version is more quantitative and builds on the positioning work done in 02.

### Standard Skill-Gap Prompt

Every project's CLAUDE.md will include the following block at the bottom. It points founders to Anthropic's native built-in skill and MCP builder tools rather than anything repo-defined.

```markdown
## Don't See What You Need?

The skills in this project cover the most common tasks for this stage, but they are not exhaustive.
If you need a capability that isn't covered, Claude Code includes two native built-in tools for this:

- **Skill creator** — Claude Code's built-in skill authoring tool. Use it to create a new custom skill
  and save it in this project's `.claude/skills/` directory (project-only) or in the root
  `.claude/skills/` directory (available across all projects).
- **MCP builder** — Claude Code's built-in MCP server builder. Use it if you want to connect
  Claude Code to an external tool or API. This is an advanced option most relevant when you're
  working on outbound sales, beta testing, or fundraising and want to integrate a CRM, email
  platform, or data source directly.

Custom skills and MCP servers you create will live in your private fork and will not affect
the upstream repo. If you build something you think would benefit other founders, see CONTRIBUTING.md
for how to suggest it.
```

---

## Context Accumulation Model

The key design challenge is how context accumulates without bloating any single session. The approach:

1. **Each project's CLAUDE.md explicitly lists** which global context files to load at the start of a session.
2. **The `context-loader` skill** reads only those files, not the entire `global/context/` directory.
3. **After producing a deliverable that updates global context**, the `context-writer` skill appends or rewrites the appropriate file and shows the founder a diff before saving.
4. **Founders can edit global context files directly** between sessions. These are plain markdown — no special tooling required.
5. **Each project's `outputs/` directory** is the memory of what that project has done. Later projects can reference prior outputs explicitly when needed (e.g., Project 08 references Project 04's `waitlist-tracker.md`).

---

## Recommended Additional Projects (Your Suggestions, Incorporated)

### Project 00 — Setup & Onboarding
A short onboarding project that walks the founder through:
- Cloning the repo and setting up Claude Code
- Filling in `global/context/founder-profile.md` interactively
- Writing their first draft of `startup-hypothesis.md`
- Understanding the repo structure and progression
- Committing to their private fork

This ensures all subsequent projects have a baseline global context to work from.

### Founder Personal Brand (within Project 04)
A dedicated `founder-linkedin-builder` skill inside Project 04 that is distinct from the company's content engine. Focuses on the founder's personal thought leadership: LinkedIn post formats for individual voice, how to position the founder as a domain expert, and how personal brand and company brand reinforce each other.

### Advisor Recruitment (Project 11 sub-skill)
The `advisor-prospector` skill in Project 11 handles this. It's distinct from investor prospecting — advisors are recruited earlier, often before institutional fundraising, and the pitch is different.

### Customer Success (Project 08 sub-skill)
The `cs-engager` skill in Project 08 handles structured retention and check-in motions. This expands if the product reaches commercial launch, at which point a Project 13 could be added.

### Operations & Toolstack (within Project 00)
A `toolstack-advisor` skill in Project 00 that recommends a lean founder toolstack by stage, explains how tools connect, and helps the founder avoid overbuilding their stack before they need it.

---

## CLAUDE.md Conventions

**Root CLAUDE.md** contains:
- What this repo is and how to use it
- How to navigate the projects in sequence
- How global context works and where it lives
- Conventions for file naming and output formatting
- How to commit outputs to a private fork
- How to get help if stuck

**Each project's CLAUDE.md** contains:
- What this project does
- Prerequisites (which prior projects should be complete)
- Which global context files to load
- Which skills are available and what they do
- What outputs this project produces and where they go
- What gets written back to global context and when

---

## GitHub Governance

### Repository Model

The public repo (`github.com/[your-handle]/employee-number-two`) is the canonical, read-only source. The `main` branch is protected with the following rules:

- **No direct pushes to `main`** — including by the maintainer. All changes go through PRs.
- **PR review required** — the maintainer is the sole required reviewer.
- **No force pushes** — history on `main` is permanent.

These rules are set in GitHub under **Settings → Branches → Branch protection rules**.

### How Founders Use the Repo

1. Navigate to the repo on GitHub
2. Click **Fork** — this creates their own copy under their GitHub account
3. Clone their fork locally and work from there
4. All their outputs, context files, and custom skills stay in their fork
5. They never push back to the upstream repo unless they are deliberately contributing

### How Community Contributions Work

When a founder builds something they think would benefit others — a new skill, a refined template, a new project — they open a **Pull Request** from their fork to the upstream `main` branch. The PR lands in your GitHub notifications. You review it, request changes if needed, and merge or close it. Nothing reaches `main` without your approval.

`CONTRIBUTING.md` (in the repo root, publicly visible) explains:
- The fork-and-use workflow
- What kinds of contributions are welcome (skills, templates, reference documents, new projects)
- What a good PR includes (description of the skill, what problem it solves, which project it belongs to)
- That contributions become part of the public repo under the same license
- That you review contributions but cannot guarantee a response timeline

### `.gitignore` Entries

```
_dev/
projects/*/outputs/
global/context/
```

The last two entries are important: founders should not accidentally push their personal startup context (ICP, brand voice, financial model) to a public fork. The `.gitignore` prevents outputs and context files from being tracked by default. Founders who want to version-control their own outputs should do so in a **private** fork, not a public one. This will be called out explicitly in `README.md` and Project 00.

---

## Repo Initialization Checklist

When a founder first clones the repo, they:

1. Run through Project 00 (onboarding)
2. Fill in `global/context/founder-profile.md`
3. Write an initial `global/context/startup-hypothesis.md`
4. Create a private fork on GitHub
5. Begin Project 01

From there, each project's CLAUDE.md tells them what to do next.

---

## What This Repo Is Not

- It is not a turnkey SaaS product. It requires Claude Code and a mildly technical user.
- It does not automate posting to social media, sending emails, or executing CRM actions directly.
- It does not provide legal or financial advice.
- It does not require any paid third-party subscriptions, though it will recommend them where relevant.
