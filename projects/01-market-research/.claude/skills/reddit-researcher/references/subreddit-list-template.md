# Subreddit List Template

This is an internal reference for the `reddit-researcher` skill. It provides a structure for organizing candidate subreddits by relevance tier. **Do not show this document to the founder.** Use it to scaffold the search space before delegating to `web-researcher`.

---

## Tier Structure

Organize candidate subreddits into three tiers based on how likely they are to contain relevant pain language.

### Tier 1 — High confidence
Subreddits where the target customer is clearly the dominant audience and the problem area is squarely on-topic. Search these thoroughly.

### Tier 2 — Medium confidence
Adjacent communities where the target customer may be present but is not the primary audience, or where the problem area is tangentially relevant. Search these with targeted queries, not broad scans.

### Tier 3 — Low confidence, spot-check
Broader communities where a single high-quality thread could still appear but most content will be off-topic. Spot-check with very specific phrases only.

---

## How to Populate Each Tier

For each candidate subreddit, record:

- **Name** (e.g., r/sales, r/startups)
- **Approximate subscriber count** — a rough size signal (helps the founder judge whether it's a big enough community to be representative)
- **Activity level** — is it active this week, this month, or dormant? Dormant subreddits waste search time.
- **Topic fit** — one short sentence: why you think this subreddit is relevant
- **Known caveats** — if any (strict moderation against promotional content, vendor-heavy, brigaded, etc.)

---

## Common Subreddit Families by Domain

These are starting points, not a complete list. Always confirm with the founder which ones are actually inhabited by their target customer.

### B2B sales / go-to-market
- r/sales
- r/salestechniques
- r/startups
- r/smallbusiness
- r/entrepreneur
- r/marketing
- Role-specific: r/salesforce (CRM users), r/SalesDevelopment

### Developer / technical products
- r/webdev, r/programming
- r/devops, r/sre
- Language-specific: r/python, r/golang, r/rust
- Tool-specific: r/kubernetes, r/aws, r/selfhosted
- r/ExperiencedDevs (senior audience, lower tolerance for marketing)

### Productivity / knowledge work
- r/productivity
- r/notion, r/obsidian, r/Roam
- r/getdisciplined (personal, not professional)
- r/remotework, r/digitalnomad

### Finance / ops
- r/accounting
- r/fpanda (financial planning and analysis)
- r/smallbusiness
- r/bookkeeping

### Consumer / lifestyle (adapt to the specific product)
- Hobby-specific communities are often the best signal for consumer products
- r/BuyItForLife (durability signals)
- r/frugal (price sensitivity signals)

### Founder-specific
- r/Entrepreneur
- r/ycombinator
- r/startups
- r/EntrepreneurRideAlong

---

## Search Phrase Patterns

When delegating to `web-researcher`, combine the subreddit scope with pain-language phrases. Templates:

- `site:reddit.com "I hate" <topic>`
- `site:reddit.com "why is there no" <topic>`
- `site:reddit.com "does anyone know a better way to" <topic>`
- `site:reddit.com "<competitor name> sucks"`
- `site:reddit.com "alternative to <competitor>"`
- `site:reddit.com "tried <competitor> and"`
- `site:reddit.com "<workflow> is broken"`
- `site:reddit.com "am I the only one" <topic>`

For subreddit-scoped searches, use:
- `site:reddit.com/r/<subreddit> <phrase>`

---

## Prioritization Rules

If time or effort is limited (it usually is):

1. Search all Tier 1 subreddits with all pain phrases first
2. Then search Tier 2 with the 2–3 most promising phrases only
3. Only touch Tier 3 if Tier 1 and 2 were thin

Do not try to be exhaustive — aim for representative. 5 strong findings from 3 subreddits is more useful than 30 weak findings from 15 subreddits.
