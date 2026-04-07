# Competitive Analysis Framework

This is an internal reference for the `competitor-mapper` skill. It defines the matrix structure, how to categorize competitors, and tactics for finding hard-to-get information like pricing. **Do not show this document to the founder.** Use it to guide the research and make the matrix consistent across competitors.

---

## Competitor Categorization

Every competitor fits into one of three buckets. Getting the bucket right matters for how the founder thinks about positioning.

### Direct competitors
- Solve the same problem
- For roughly the same customer type
- Explicitly compete for the same budget line item

These are the competitors founders name first. They are usually important but rarely the most dangerous — direct competitors are visible and can be planned around.

### Indirect competitors
- Solve a slice of the same problem (e.g., covers 40% of what your product would cover)
- Or solve the same problem for an adjacent customer type that could expand into yours
- Or solve a related problem that consumes the same budget

Indirect competitors are often acquirers or expansion threats. A company serving enterprise might expand down-market. A point tool might broaden its scope. Track these closely.

### Workarounds
- Spreadsheets, documents, internal tools built by engineering teams, manual processes
- Consultants or agencies performing the work as a service
- "Doing nothing" — living with the problem

Workarounds are the most commonly missed category and often the most important. If 80% of your target customers are using a spreadsheet, your real competitor is the spreadsheet — not the other SaaS vendor with 3 customers. The spreadsheet has zero switching cost, infinite flexibility, and a deeply entrenched user base.

---

## Dimensions to Capture Per Competitor

Every competitor entry in the matrix should attempt to fill all of these fields. If a field is unavailable, write "Not found — <what you tried>" rather than leaving it blank.

| Dimension | What to capture | Typical source |
|---|---|---|
| **Name and URL** | Company name and primary website | Trivial |
| **What they do** | 1–2 sentence functional description, not marketing copy | Company homepage, Crunchbase |
| **Stated ICP** | Who they say they serve (role, company size, industry) | Company "for X" pages, customer case studies |
| **Actual ICP** | Who actually uses them, based on reviews | G2 reviewer profiles, Reddit threads, LinkedIn |
| **Core capabilities** | 3–5 specific things the product does | Product pages, documentation |
| **Pricing model** | Per-seat, per-usage, flat, tiered, custom | See pricing discovery section below |
| **Pricing numbers** | Actual dollar figures or ranges | See pricing discovery section below |
| **Funding / stage** | Last round, total raised, notable investors | Crunchbase, Pitchbook, press releases |
| **Founded** | Year founded | LinkedIn company page, Crunchbase |
| **Team size** | Rough employee count | LinkedIn |
| **Notable customers** | Logos the company publicly claims | Customer page, press releases |
| **User strengths** | What users actually praise (quoted) | G2, Capterra, Reddit, Hacker News |
| **User gaps** | What users actually complain about (quoted) | G2, Capterra, Reddit, Hacker News |
| **Recent moves** | Product launches, funding, hires, pivots in last 6 months | Press, LinkedIn, company blog |

---

## Pricing Discovery Tactics

Pricing is the most valuable and hardest-to-find field. When a company does not publish pricing:

### Tactics that usually work

1. **Wayback Machine / Internet Archive.** Many companies hide pricing now but had it public 2–3 years ago. `web.archive.org/web/*/<company>.com/pricing` will often show historical pricing pages.
2. **G2 and Capterra review text.** Reviewers frequently mention what they pay. Search review bodies, not just star ratings.
3. **Reddit threads about sales calls.** "I just got quoted $X for [Company Y]" posts are common in practitioner subreddits.
4. **Product comparison articles.** Third-party comparison sites sometimes publish pricing they got from sales calls.
5. **SEC filings (for public companies or their customers).** If a customer files public financials, they may disclose what they pay.
6. **Job postings from the company.** Sometimes indicate target deal size ("experience closing $50K–$200K ARR deals").
7. **LinkedIn posts from practitioners.** People sometimes complain about pricing publicly.

### Tactics to avoid
- Guessing based on competitor pricing ("probably around $X because their competitor is $Y")
- Quoting a "starting at" number from sales collateral without caveats
- Using analyst report pricing without citing the specific report

### When pricing is genuinely unavailable
Write: "Not public — checked company website, Wayback Machine archive (<year>), G2 reviews, and a search of r/<relevant subreddit>. No pricing information found. The founder could request pricing directly through sales." This gives the founder a clear action item.

---

## Patterns That Indicate Real Capability Gaps

The most valuable output of this skill is the gap analysis, not the matrix itself. Look for:

- **Cross-competitor complaints.** The same issue raised in reviews of 3+ competitors = a category-level gap, not a product weakness. These are the highest-value gaps to surface.
- **Feature exists but is poorly executed.** Users complain about a feature that competitors technically have ("they say they do X but it doesn't work for Y"). This is a gap hiding inside a checklist item.
- **Workflow breakage at integration points.** "Works great until I try to export it to Salesforce" or "Great product but doesn't play nice with our existing stack." Integration gaps are expensive for incumbents to fix and are often the best wedge.
- **Pricing forces bad product choices.** "We had to buy the enterprise tier just to get <feature> but we only use 10% of it." Bad pricing design is a gap you can attack with better packaging.
- **Unserved segments.** "None of these work for companies under 50 people" or "Everything is built for US markets and ignores compliance in <region>." Segment gaps are often the cleanest positioning.

Patterns that are NOT gaps:
- "Their UI is ugly" — subjective, hard to attack defensibly
- "They are too expensive" — price is a segmentation choice, not a gap (unless it forces bad product choices as above)
- "Their sales team is pushy" — GTM issues, not product gaps

---

## How to Handle Indirect and Workaround Competitors

For indirect competitors, apply the same framework but add:
- **Expansion path:** Could they plausibly expand into the founder's exact space? What would they have to build?
- **Defense:** What is preventing them from doing so today (focus, ICP, feature depth)?

For workarounds, modify the framework:
- **User / creator:** Who builds and maintains the spreadsheet, process, or internal tool?
- **Cost of switching:** Why is the spreadsheet sticky? (Familiarity, customization, no approval process needed, zero cost)
- **Pain of ownership:** What goes wrong with the workaround? (This is usually where the real pain lives)
- **Trigger:** What would have to happen for someone to actively look for a product to replace this?

Workarounds rarely have pricing, funding, or reviews — but they are real competitors and deserve a full entry in the matrix.

---

## Minimum Matrix Coverage

A useful matrix has at least:
- 3 direct competitors
- 2 indirect competitors
- 1 workaround

Fewer than this and the founder has not actually mapped the landscape — they have named the incumbents. Push for more, especially in the indirect and workaround categories.

Maximum: 10–12 entries. Beyond that the matrix becomes unusable and the gap analysis gets diluted. If more than 12 candidates emerge, prioritize by relevance to the founder's specific target customer.
