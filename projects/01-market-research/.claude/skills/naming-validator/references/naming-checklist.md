# Naming Checklist

This is an internal reference for the `naming-validator` skill. It defines the axes to check for every candidate name, the TLDs to cover, USPTO search tactics, and heuristics for spotting obvious conflicts. **Do not show this document to the founder.** Use it to run a consistent check across all candidates.

---

## TLDs to Check

For every name, check availability on these TLDs at minimum:

| TLD | Why it matters |
|---|---|
| `.com` | Default, most valuable, still matters even if alternatives have become acceptable |
| `.io` | Strong for developer and technical products |
| `.co` | Common backup when `.com` is taken |
| `.ai` | Expected for AI-adjacent products |
| `.app` | Useful for consumer apps |

Check these if the founder's market is specific:
- `.dev` — developer tools
- `.co.uk` / `.de` / `.fr` / `.jp` — if the founder plans to operate in a specific country
- `.tech` / `.xyz` — low-cost alternatives, weaker brand signal

**How to check:** A registrar's WHOIS tool, ICANN Lookup, or any registrar's search page. For each TLD, categorize as:

- **Available** — unregistered, buyable at registration cost
- **Registered — parked** — registered but not in active use (may be on an aftermarket for a premium price)
- **Registered — active** — registered and hosting an active site. Note what is on it.

Parked domains are often purchasable for hundreds to tens of thousands of dollars. Report the status and let the founder decide whether to pursue an aftermarket purchase.

---

## USPTO Trademark Search Tactics

The USPTO trademark database is searchable at the public trademark search tool (successor to TESS). For each candidate:

### Search variations
- Exact name
- Name with common prefixes/suffixes removed (e.g., check "Lumen" if the candidate is "LumenAI")
- Phonetic variants ("Fonix" → also check "Phoenix," "Fonex")
- Common misspellings of the candidate

### What to report for each match
- Exact mark text
- Status (LIVE / DEAD — only LIVE marks matter for conflict analysis)
- Filing date
- Registration number
- Goods and services description
- Nice Classification number(s)
- Owner / registrant

### Nice Classes that matter for most startups in this repo
- **Class 009** — downloadable software, mobile apps, SaaS delivered as software
- **Class 035** — business services, advertising, marketing
- **Class 036** — financial services
- **Class 038** — telecommunications, including SaaS delivered as a service
- **Class 041** — education, training
- **Class 042** — SaaS, PaaS, cloud computing, software-as-a-service
- **Class 044** — medical services
- **Class 045** — legal services

Most software startups file in **Class 009 and Class 042** together. A conflict in either of these for a similar product is a serious flag.

### How to interpret matches
- **Exact match, live, same class, related goods/services:** Strong blocker. Flag as "Not recommended."
- **Exact match, live, unrelated class (e.g., Class 025 for clothing):** Often not a blocker for a software product, but note it so an attorney can evaluate.
- **Phonetic match, live, same class:** Flag for attorney review. Phonetic similarity is a common basis for trademark disputes.
- **Dead mark:** Generally not a concern, but still report it — the prior owner may still claim common-law rights in some jurisdictions.

Do not try to interpret what is and is not a "likelihood of confusion" — that is the legal standard and it is a lawyer's judgment call. Just report the facts.

---

## Social Handle Check

Check these platforms for every candidate:

- **Twitter / X** — @<name>
- **LinkedIn** — company page, not personal profile
- **Instagram** — @<name>
- **GitHub** — for developer-facing products, a taken GitHub org name is a real obstacle
- **TikTok** — for consumer products
- **YouTube** — channel name availability

Categorize handles as:
- **Available**
- **Taken — inactive** (account exists but no posts, or last post >1 year ago)
- **Taken — active** (account posts regularly)

A broadly-taken handle on an inactive account can sometimes be recovered (platforms have reclamation processes for trademark holders) but do not assume this. Report it as taken.

---

## Search Engine Collision Check

Google the exact name. Also try "<name> app," "<name> software," "<name> <industry>." What comes up?

### Red flags
- **Existing product in the same or adjacent space** with the same or a very similar name — even if not trademarked, a brand already owning the search results is a real obstacle to being found
- **Cultural collision** — the name is also a well-known movie, band, book, political figure, drug name, or profanity in any major language
- **Negative associations** — the name or a homophone is a controversial brand, a failed company, or a term with negative connotation

### Not a red flag on its own
- Generic dictionary word results (e.g., "Apple" the fruit) — context matters more
- A very small business with the same name in an unrelated industry
- Results for the name as a common first name (unless the common name dominates results)

---

## Heuristics for Quick Triage

Before doing the full check, do a 30-second pre-check to eliminate obviously bad candidates:

- **`.com` owned by a Fortune 500 company or major tech brand** — almost always not worth pursuing
- **Exact product name already exists in the founder's category** — immediate red flag
- **Name is a generic category term** ("Project Manager," "Email Tool") — impossible to trademark, bad for search
- **Name is hard to spell or pronounce** — will hurt word-of-mouth growth
- **Name means something unfortunate in a major market language** — easy to miss, hard to fix later

Pre-triage saves time. If a name fails pre-check, tell the founder briefly and move on rather than running the full checklist.

---

## Summary Report Structure

For each candidate, the final report should capture (condensed format):

```
### <Name>
- Domains: [.com: <status>] [.io: <status>] [.co: <status>] [.ai: <status>]
- USPTO: <0 matches / N matches in Class XXX / details>
- Handles: [Twitter: <status>] [LinkedIn: <status>] [Instagram: <status>] [GitHub: <status>]
- Search collision: <clean / notes>
- Overall tier: Recommended | Flagged | Not recommended
- Blocker (if not recommended): <one sentence>
```

Keep the report scannable. The founder will compare candidates side-by-side and needs to see at a glance which ones are live options.
