# Source Credibility Guide

This is an internal reference for the `news-analyst` skill. It defines how to weigh publications when synthesizing news coverage and how to distinguish reporting from sponsored content. **Do not show this document to the founder.** Use it to rate sources before including them in the report.

---

## Credibility Tiers

### Tier 1 — Primary sources
- SEC filings (10-K, 10-Q, S-1, 8-K)
- Company's own press releases and blog posts (treat as promotional but factually accurate about the company's own actions)
- Court documents, regulatory filings
- Official industry reports (FTC, CFPB, EU Commission, etc.)
- Conference talks and earnings calls (transcripts count)

Treat these as authoritative about the facts they report on, while remaining skeptical about framing.

### Tier 2 — Established trade press
Domain-specific publications with editorial standards. These are often the best source for early-market signal because reporters cover their beat in depth and pick up on moves before mainstream press does.

**B2B tech examples:**
- The Information (paywall, high-quality)
- Stratechery (opinion but well-researched)
- Protocol (now defunct, but archives useful)
- TechCrunch (broad coverage, variable depth)
- Ars Technica (technical depth)

**Sales / GTM examples:**
- Sales Hacker
- G2 Research
- Tomasz Tunguz blog
- SaaStr

**Developer tools:**
- DevOps.com
- The New Stack
- InfoQ

**Finance / fintech:**
- Finextra
- American Banker
- PYMNTS (watch for sponsored content)

Trade press quality varies enormously publication to publication. When in doubt, check if the piece has a byline with a real reporter and whether the publication has a clear separation between editorial and sponsored content.

### Tier 3 — Mainstream business press
- Wall Street Journal, New York Times (business section), Financial Times, Bloomberg, Reuters, The Economist

High editorial standards but often less depth on specific categories. Useful for confirming major events (funding rounds, acquisitions, regulatory actions) and for signal that a topic has crossed into mainstream awareness.

### Tier 4 — Analyst and research reports
- Gartner, Forrester, IDC
- CB Insights, Pitchbook, Crunchbase
- McKinsey, BCG reports

Often paywalled. Treat as informed opinion, not fact. Analyst projections are inputs to thinking, not conclusions. Market sizing numbers from analyst reports should always be cited with attribution and treated as rough estimates, not precise figures.

### Tier 5 — Community and aggregation
- Hacker News discussions
- LinkedIn posts from industry practitioners
- Twitter/X threads from named reporters or practitioners
- Industry Slack community summaries

Useful for sentiment and for tips that direct you to more credible sources. Individual posts are anecdotes. Look for patterns across multiple posts before treating something as a signal.

### Tier 6 — Do not cite
- SEO content farms (obvious when the site has "ultimate guide" listicles on dozens of unrelated topics)
- AI-generated roundup articles (often wrong, and trending upward in volume)
- Press release aggregators (PRNewswire, Business Wire) without a reporting layer on top
- Blogs with no byline, no About page, or no contact info
- Any source that contradicts multiple Tier 1–3 sources without a clear reason

---

## Distinguishing Reporting from Sponsored Content

Sponsored content is increasingly hard to distinguish from journalism. Red flags:

- **"Sponsored by" or "Paid partnership" labels** (required by law in many jurisdictions but often tiny)
- **Piece reads like vendor talking points** — heavy on product benefits, light on independent analysis
- **Single-source articles** where the only expert quoted works for the vendor
- **No critical perspective** — every sentence aligns with what the vendor would want said
- **Published in a "marketing content" section** — many publications have these, with names like "partner content," "brand voice," "insights"
- **Reporter byline links to an agency or freelance marketing firm, not a staff reporter**

When in doubt, treat a suspicious piece as a primary source from the vendor (Tier 1) and attribute accordingly. Do not cite it as independent reporting.

---

## Weighting for This Specific Analysis

For the News Analyst skill, when the question is **market momentum**, weigh:

- Funding round reporting from **multiple sources** higher than a single source
- **Analyst reports from Tier 4** above **company blog posts from Tier 1** (analysts are at least attempting to be independent)
- **Trade press with a named reporter** above **mainstream press without deep domain knowledge**
- Recent coverage (last 6 months) above older coverage for any claim about where the market "is" today

For the question of **sentiment**, weigh:

- Direct quotes from practitioners (Tier 2 or Tier 5) above analyst characterizations (Tier 4)
- Critical or skeptical pieces above promotional pieces (promotional pieces tell you what a vendor wants to be true, not what is true)
- Coverage from outside the founder's existing echo chamber — if the founder is already reading TechCrunch, findings from TechCrunch add less than findings from a publication they had not seen

---

## Red Flags to Always Mention in the Report

If you notice any of these during research, surface them explicitly in the "Gaps" section of the report — do not let them pass silently:

- A claim from the founder's hypothesis ("why now" is especially common) has **no supporting coverage** from any Tier 1–3 source
- Coverage is **dominated by a single publication** — the story may be reflecting that publication's house view rather than the market
- The funding narrative is **disproportionate to product evidence** — lots of raises in the category but no press about actual customers or results
- A major player is **conspicuously absent** from coverage — either they are losing ground or your search is missing something

These are honest signals, and the founder benefits more from hearing them than from a clean-looking report that papered over them.
