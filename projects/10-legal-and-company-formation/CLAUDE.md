# Project 10 — Legal & Company Formation

## Purpose

This is where the company becomes a legal entity. Everything upstream was hypothesis, research, brand, product, and pricing — all held by a person. This project is where the person becomes a company: chooses an entity structure, registers a domain, opens a bank account, and acknowledges the early-stage legal obligations that come with operating a business.

By the end of this project you will have produced a project-scoped entity options analysis, a domain acquisition plan, a banking options overview, and a formation-era legal checklist — plus a distilled summary written to `global/context/company-profile.md` that Projects 11 (fundraising) and 12 (financial modeling) auto-load. The global summary names the legal entity, state of incorporation, domain, banking relationship, and EIN status. Downstream projects rely on it for cap-table work, pitch-deck footer content, and financial-model jurisdiction assumptions.

**This project does not provide legal advice.** Every skill here is framed around surfacing options, frameworks, and questions for your attorney — never "here is what you should do." Formation decisions have long-lived tax and fundraising consequences that depend on specifics only a qualified attorney can evaluate against your situation.

**Jurisdiction scope:** US-only. Skills assume a US-based founder making a US entity choice (LLC, S-Corp, C-Corp) and banking with US institutions. Non-US founders should seek local counsel — the frameworks here will not map cleanly to UK, Canadian, EU, or other jurisdictions.

## Prerequisites

**Project 00** (onboarding — produces `founder-profile.md`). Entity choice depends heavily on founder residency, current employment status, and co-founder situation. Running this project without a founder profile produces generic guidance that will not defensibly apply to your situation.

**Project 09** (pricing — produces `pricing-model.md`) is strongly recommended. Revenue model shapes several downstream decisions: sales-tax nexus risk, choice of state for incorporation, banking feature priorities (ACH vs. international wires vs. card processing). Without it, the skills will still run but will flag that their recommendations are anchored on assumptions rather than evidence.

**Project 01** (market research — produces `startup-hypothesis.md`) is recommended. The product domain surfaces regulated-industry flags (healthcare, fintech, children's data, education data) that affect both entity choice and early legal obligations.

## Global Context Files

**Loads:** `founder-profile.md`, `startup-hypothesis.md`, `pricing-model.md` (optional — soft-degrade if pre-pricing)

**Writes:** `company-profile.md` — the distilled record of legal identity. `entity-advisor` writes the initial version (entity type, state, formation status); subsequent skills append fields as decisions are made (domain registered, bank account opened, EIN obtained). All writes go through the `context-writer` skill with preview and approval.

## How This Project Works

Skills fall into four areas that map to distinct formation decisions:

1. **Entity selection** — `entity-advisor` surveys LLC, S-Corp, and C-Corp options against the founder's situation and revenue model, then produces a 2–3 option comparison with tradeoffs and questions for a lawyer. The founder selects a direction; the skill seeds `company-profile.md` once the entity is formed.
2. **Domain acquisition** — `domain-strategist` guides the path from desired domain to registered domain: primary targets, TLD strategy, acquisition mechanics (direct vs. aftermarket vs. broker), and squatter-outreach playbook when the .com is held.
3. **Banking** — `banking-advisor` compares founder-friendly business banking providers (Mercury, Brex, Chase Business, local credit unions) across founder-friendliness, fundraising compatibility, international support, and integrations. Runs after entity formation because account opening typically requires an EIN.
4. **Formation-era legal checkpoints** — `early-legal-checker` surfaces the legal items that typically matter at or after formation: trademark filing timing, 83(b) election deadlines for founder equity, co-founder invention-assignment and vesting agreements, TOS/privacy-policy requirements at launch, and state-specific compliance (franchise tax, statement of information filings).

This is a different scope from the Project 01 `early-legal-checker`, which focuses on pre-research flags (IP assignment risk from current employment, NDA considerations for design partners, data-privacy basics for waitlist collection). Run the Project 01 version first and the Project 10 version at or after formation. The two are complementary.

All skills are conversational. Each opens with the "not legal advice" disclaimer, reads the relevant context files, asks grounding questions before proposing options, and shows a preview of any output before writing. The founder names every selection explicitly — no skill picks an entity structure, domain, banking provider, or legal action on the founder's behalf.

## Skills

| Skill | Description |
|---|---|
| `entity-advisor` | Survey LLC, S-Corp, and C-Corp options against founder profile and revenue model; produce a 2–3 option tradeoff table with questions for a lawyer; capture selected entity and seed `company-profile.md` |
| `domain-strategist` | Guide primary + fallback domain selection, TLD strategy, and acquisition path; produce a plan with concrete next steps and price anchors |
| `banking-advisor` | Compare founder-friendly US business banking providers on dimensions that matter for early-stage startups; produce a comparison with a recommended direction |
| `early-legal-checker` | Surface formation-era legal checkpoints (trademark, 83(b), co-founder agreements, TOS/privacy policies, state compliance); produce a checklist of questions for an attorney |

## Recommended Flow

**In order (approximate — several skills can run in parallel):**

1. **`early-legal-checker`** — run first, ideally before entity formation. Expect 30–45 minutes. Surfaces the items that need to be handled at or immediately after formation (83(b) deadlines are particularly time-sensitive — 30 days from equity issuance, no extensions). Output: `outputs/early-legal-checklist.md`.
2. **`entity-advisor`** — second. Expect 60–90 minutes. Produces the options analysis and captures the founder's selected entity. Once the entity is actually formed (via Stripe Atlas, Clerky, Firstbase, or direct-to-state), re-run to have the skill invoke `context-writer` and seed `company-profile.md` with legal name, entity type, state, and formation date. Output: `outputs/entity-options-analysis.md`.
3. **`domain-strategist`** — can run in parallel with entity selection. Expect 30–60 minutes (plus wait time if pursuing aftermarket acquisition). Produces the plan; once a domain is acquired, re-run briefly to append the registered domain to `company-profile.md`. Output: `outputs/domain-acquisition-plan.md`.
4. **`banking-advisor`** — run after entity formation and EIN receipt. Expect 45 minutes. Once an account is opened, re-run to append the banking relationship to `company-profile.md`. Output: `outputs/banking-options-overview.md`.

**On re-run:** If `company-profile.md` already exists, skills that write to it read the existing content first, append rather than overwrite, and show the diff through `context-writer`. A second pass through `entity-advisor` (e.g., after raising a priced round that requires LLC-to-C-Corp conversion) explicitly surfaces what is changing and why.

**If you are pre-pricing:** Run `entity-advisor` only if you have a clear read on your fundraising path (VC vs. bootstrapped), since that is the dominant variable in LLC-vs-C-Corp choice. If you do not, defer until Project 09 is complete.

## Outputs

All saved in `projects/10-legal-and-company-formation/outputs/`:

- `entity-options-analysis.md` — 2–3 viable entity structures, tradeoff table, tax/fundraising/compliance implications, questions for a lawyer, selected direction (from `entity-advisor`)
- `domain-acquisition-plan.md` — primary target, fallback domains, TLD strategy, acquisition path, price anchors, timeline, squatter-outreach draft if applicable (from `domain-strategist`)
- `banking-options-overview.md` — comparison of 3–5 providers across founder-friendliness, fundraising compatibility, integrations, card programs, treasury yield; recommended direction (from `banking-advisor`)
- `early-legal-checklist.md` — formation-era legal checkpoints organized by trigger (at formation, within 30 days, at launch, at first hire), with questions for an attorney (from `early-legal-checker`)

**Writes to `global/context/`:** `company-profile.md` — distilled record of legal identity. Written by `entity-advisor` initially and appended by `domain-strategist`, `banking-advisor` (for EIN and banking), and the founder manually as formation steps complete. All writes go through `context-writer`.

## Validation

This project is in a workable state when:

- `entity-options-analysis.md` exists with at least 2 entity structures compared and a **Selected Direction** naming the chosen entity with rationale.
- `domain-acquisition-plan.md` exists with a primary target and at least 2 fallback options, and a named acquisition path for the primary.
- `banking-options-overview.md` exists with 3+ providers compared and a recommended direction.
- `early-legal-checklist.md` exists with at least one item in each trigger category (at formation, within 30 days, at launch).
- `global/context/company-profile.md` exists and contains at minimum: legal name, entity type, state of incorporation, formation date or status, and a `last_reviewed` date. Domain and banking fields can be populated over time as those steps complete.

A good Project 10 outcome is one where the founder can hand the entity decision to an attorney with the specific questions and rationale they need to advise efficiently — not one where the founder walks in cold and pays the attorney to start from first principles. The project saves money by making the founder a better-informed buyer of legal services, not by replacing them.

**Note on scope:** This project does not file trademarks (USPTO registration is a lawyer or self-service task), does not open bank accounts (providers require the founder directly), does not draft operating agreements or shareholder agreements (these need an attorney), and does not handle cap-table mechanics beyond flagging 83(b) timing (Project 11 covers equity issuance in depth). Keep this project focused on the structural decisions and the checklist of questions to ask professionals.

---

## Don't See What You Need?

The skills in this project cover the most common tasks for this stage, but they are not exhaustive.
If you need a capability that isn't covered, Claude Code includes two native built-in tools for this:

- **Skill creator** — Claude Code's built-in skill authoring tool. Use it to create a new custom skill
  and save it in this project's `.claude/skills/` directory (project-only) or in the root
  `.claude/skills/` directory (available across all projects).
- **MCP builder** — Claude Code's built-in MCP server builder. Use it if you want to connect
  Claude Code to an external tool or API. Most relevant here when connecting to a registrar API
  (Namecheap, Cloudflare Registrar), a trademark-search service, or a tax/compliance platform.

Custom skills and MCP servers you create will live in your private fork and will not affect
the upstream repo. If you build something you think would benefit other founders, see CONTRIBUTING.md
for how to suggest it.
