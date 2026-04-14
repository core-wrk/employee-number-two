# Stack Selection Tradeoffs

Internal reference for `tech-stack-advisor`. For every load-bearing stack decision, this file names the tradeoff plainly so the founder understands what they are giving up. Never present a decision as free.

---

## Managed vs. Self-Hosted (generally)

**Managed wins at pre-PMF.** You are trading money for time. At early stage, founder time is the scarcest resource and cash is usually more available than hours. A solo founder operating their own Postgres, their own Redis, and their own object storage is a solo founder who is not talking to users.

**Self-hosted wins when:** the founder has operational expertise *and* has a specific named reason the managed option fails (egress cost at scale, compliance, a feature the managed version doesn't have). "It's cheaper at scale" is not a reason at pre-PMF.

---

## Monolith vs. Serverless Functions vs. Microservices

- **Monolith** (single deployable app): default. One repo, one deploy, one database. Fastest to iterate.
- **Serverless functions** (Vercel/Netlify edge functions, AWS Lambda): great for stateless request-response; bad for long-running tasks, background jobs, or anything requiring a persistent connection.
- **Microservices**: wrong answer at pre-PMF in nearly all cases. The operational overhead destroys founder velocity.

**Tradeoff naming:** Monolith means scaling is coarse (whole app scales or nothing). Serverless means cold starts and stateless constraints. Microservices means you own a distributed system.

---

## SQL vs. Document Database

- **Postgres (SQL):** default. Handles relational data, JSONB for flexible schemas, full-text search, vector search via pgvector, time-series via TimescaleDB extension. One database handles 90% of early-stage products.
- **Firestore / DynamoDB / MongoDB (document):** pick only if access patterns are overwhelmingly key-value, the data shape is genuinely schemaless, or the managed story for a specific product fits (Firebase for mobile).

**Tradeoff naming:** Postgres is the most transferable skill and the least surprising default. Document databases win on specific access patterns and lose on ad-hoc querying and joins.

---

## Auth: Managed Provider vs. Roll Your Own

- **Managed (Clerk, Supabase Auth, Auth.js, Firebase Auth):** default. Ship in a day.
- **Roll your own:** wrong answer unless there is a specific compliance or integration requirement. Auth bugs are security bugs. Managed providers have already found and fixed the common ones.

**Tradeoff naming:** Managed means vendor lock-in (migrating users between auth providers is real work). Roll-your-own means you own every CVE.

---

## Hosting: Platform vs. Cloud

- **Platform (Vercel, Netlify, Fly.io, Railway):** default. Git-push to deploy, zero infra operations.
- **Direct cloud (AWS, GCP, Azure):** pick only if the founder has existing cloud expertise and the product requires something the platforms don't offer (specific regions, specific compliance, GPUs).

**Tradeoff naming:** Platforms are more expensive per unit of compute but dramatically cheaper per hour of founder time. At scale the math inverts; at pre-PMF the math never inverts.

---

## AI Providers: Single vs. Multi

- **Single provider (Anthropic or OpenAI):** default. Pick one, build the product, do not spend time on provider abstraction layers until there is a concrete reason (cost, capability gap, reliability).
- **Multi-provider:** justified when a specific feature lives on one provider and a different specific feature lives on another, or when reliability/fallback is a hard product requirement.

**Tradeoff naming:** Single-provider means you ship faster and are exposed to one vendor's pricing and outages. Multi-provider means you build an abstraction layer that you will also have to maintain.

---

## Observability: Build From Day One vs. Defer

- **Errors (Sentry):** install from day one. It takes 20 minutes and will save you weeks later.
- **Product analytics (PostHog):** install before you have users. Retroactive analytics is impossible.
- **LLM traces (LangSmith, Langfuse):** install from day one if the product uses LLMs. LLM bugs without traces are nearly un-debuggable.
- **APM / infra monitoring (Datadog, New Relic):** defer until you have real traffic.

**Tradeoff naming:** The cost of installing observability late is much higher than the cost of installing it early. This is one of the few layers where defer is almost always wrong.

---

## Feature Flags: Ship With or Without

- **Without:** default at pre-PMF. You do not have users to segment. Deploy or don't deploy.
- **With (LaunchDarkly, Statsig, PostHog feature flags):** justified once you have at least two user cohorts and an A/B test you actually want to run. PostHog's feature flags are included in its analytics tier and are a reasonable place to start.

**Tradeoff naming:** Feature flags add complexity and a failure mode (flag stale, code path dead). Don't add them prematurely.

---

## Type Safety: Strict or Loose

- **Strict TypeScript / strict Python type checking:** default. Catches a class of bugs at compile time that would otherwise ship to users.
- **Loose:** faster prototyping but the cost compounds. The time saved on day 1 is paid back with interest on day 30.

**Tradeoff naming:** Strict types slow the first day slightly and speed up every day after. Loose types do the reverse. At pre-PMF, velocity on day 30 matters more than velocity on day 1.

---

## The Meta-Tradeoff: Novel vs. Boring

At pre-PMF, boring wins. "Boring" means: well-trodden, mature frameworks with answers to every common question already on Stack Overflow or in the framework docs. Novel stacks (whatever is trending this quarter) have the opposite property — every question is a new question.

The founder is not being judged by other engineers for their stack choice. The founder is being judged by users for their product. Boring stack, interesting product is always the right shape at this stage.

Exceptions:
- The founder genuinely has deep expertise in a novel stack (then it is not novel to them — it is their boring)
- The product's core value proposition requires a specific novel capability

Otherwise: boring.
