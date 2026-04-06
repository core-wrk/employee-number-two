# Context Backfill Guide

Internal reference for the `journey-assessor` skill. When a founder skips projects, this guide describes what needs to go into each global context file and how to help the founder fill it in.

---

## founder-profile.md

**Always required.** Every project reads this file.

**What it contains:**
- Founder's name and background
- Relevant domain expertise
- Technical vs. non-technical orientation
- Goals for using this repo
- Working style preferences
- Team composition (solo founder, co-founders, early employees)

**How to backfill:** Use the `profile-builder` skill. This is a conversational skill that will guide the founder through creating their profile. Even founders who skip ahead should complete this.

**Estimated time:** 10-15 minutes

---

## startup-hypothesis.md

**Always required.** Most projects read this file for core context about what the startup is building and why.

**What it contains:**
- Problem statement (specific, with a named audience)
- Proposed solution (concrete, with a mechanism)
- Key assumptions (at least 3, testable)
- Target customer description
- Current alternatives and why they fall short
- Why now — what has changed

**How to backfill:** Use the `hypothesis-builder` skill. Even founders with a live product benefit from articulating their hypothesis clearly — it sharpens fundraising narratives and product positioning.

**Estimated time:** 20-30 minutes

---

## competitive-landscape.md

**Required if skipping Project 01 (Market Research).**

**What it contains:**
- Direct competitors (companies solving the same problem for the same customer)
- Indirect competitors (different approach to the same problem, or same approach to an adjacent problem)
- For each competitor: what they do well, where they fall short, pricing, target market
- Capability gaps — what no competitor does well
- The founder's differentiation thesis

**How to backfill:** Ask the founder to describe their competitive landscape. Prompt for:
1. "Who are your top 3-5 competitors?"
2. For each: "What do they do well? Where do they fall short?"
3. "What does no one in this space do well?"
4. "How will you be different?"

If the founder's knowledge is thin, suggest they do Project 01 instead of backfilling — the market research agents will produce a much more thorough analysis.

**Estimated time:** 15-20 minutes (backfill) vs. 2-4 sessions (full project)

---

## icp.md

**Required if skipping Project 01 (Market Research).**

**What it contains:**
- Ideal customer profile: company type, size, industry, geography
- Key persona: role, title, responsibilities, pain points
- Buying behavior: how they find solutions, how they evaluate, who decides
- Disqualification criteria: who is NOT the target customer

**How to backfill:** Ask the founder:
1. "Describe your ideal customer — the company and the person within it"
2. "What is their title? What are they responsible for?"
3. "How do they find and buy tools like yours?"
4. "Who should you NOT sell to?"

**Estimated time:** 10-15 minutes

---

## brand-voice.md

**Recommended if skipping Project 02 (Brand and Marketing). Not strictly required but improves output quality for content-producing projects.**

**What it contains:**
- Brand personality (3-5 adjectives)
- Voice attributes (how the brand sounds)
- Tone variations (how tone shifts by context — marketing vs. support vs. sales)
- Messaging pillars (3-4 key themes)
- Do's and don'ts

**How to backfill:** Ask the founder:
1. "If your brand were a person, how would you describe their personality?"
2. "What are 3-4 words that describe how your brand should sound?"
3. "What should your brand NEVER sound like?"
4. "What are the key messages you want every piece of content to reinforce?"

If the founder has existing marketing copy, offer to analyze it and extract voice attributes.

**Estimated time:** 10-15 minutes

---

## brand-identity.md

**Optional. Only needed if the founder has visual brand guidelines they want to carry forward.**

**What it contains:**
- Primary and secondary colors (hex codes)
- Typography choices
- Logo description or direction
- Design principles
- Visual tone (minimal, bold, playful, etc.)

**How to backfill:** Only backfill if the founder has an existing visual identity. Ask them to share their brand guidelines or describe their visual direction. If they do not have one, skip this file — Project 03 will create it when they are ready.

**Estimated time:** 5-10 minutes (if they have guidelines)

---

## product-overview.md

**Required if skipping Project 06 (Product Management).**

**What it contains:**
- Product name and one-line description
- Value proposition
- Core features (what exists today)
- Target user and use case
- Key workflows or user journeys
- Technical stack (high level)
- Current status (concept, prototype, beta, live)

**How to backfill:** Ask the founder:
1. "Describe your product in one sentence"
2. "What are the 3-5 core features?"
3. "Walk me through the main user workflow"
4. "What is your tech stack?"
5. "What is the current status — concept, prototype, beta, or live?"

**Estimated time:** 15-20 minutes

---

## pricing-model.md

**Required if skipping Project 09 (Pricing and Packaging).**

**What it contains:**
- Pricing model type (subscription, usage-based, one-time, freemium)
- Pricing tiers and what is included in each
- Target price points
- Competitive pricing context
- Free tier or trial strategy

**How to backfill:** Ask the founder:
1. "How do you charge (or plan to charge) for your product?"
2. "What are your pricing tiers?"
3. "How does your pricing compare to competitors?"
4. "Do you have a free tier or trial?"

If the founder has not thought about pricing yet, suggest they do Project 09 when they are ready rather than guessing.

**Estimated time:** 10-15 minutes

---

## company-profile.md

**Required if skipping Project 10 (Legal and Company Formation).**

**What it contains:**
- Legal entity name and type (LLC, C-Corp, etc.)
- State of incorporation
- Domain name
- Banking setup
- Key legal milestones (incorporation date, EIN, etc.)

**How to backfill:** Only backfill if the company is already incorporated. Ask for the basic facts. If not yet incorporated, skip — Project 10 will guide them through it.

**Estimated time:** 5 minutes (if incorporated)

---

## Backfill Priority Order

When a founder is skipping multiple projects, backfill context files in this order:

1. `founder-profile.md` — always first
2. `startup-hypothesis.md` — always second
3. `icp.md` — needed by most projects
4. `competitive-landscape.md` — needed by most projects
5. `product-overview.md` — needed if they have a product
6. `brand-voice.md` — nice to have
7. `pricing-model.md` — only if relevant
8. `brand-identity.md` — only if they have one
9. `company-profile.md` — only if incorporated
