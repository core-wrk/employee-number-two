# Stack Archetypes

Internal reference for `tech-stack-advisor`. Used to match a product's shape to a stack shape quickly, without reinventing the decision space for every founder.

Pick the archetype that matches closest. If no archetype matches cleanly, pick the closest and document the divergence in the founder's `tech-stack.md`.

---

## 1. Web SaaS (B2B or B2C)

**Shape:** Multi-tenant web app, users sign in, data persisted, billing per seat or per workspace.

**Typical stack:**
- Frontend: Next.js or Remix (TypeScript)
- Backend: Next.js API routes or a separate TS server; Python/FastAPI if heavy data/ML work
- Database: Postgres (Supabase, Neon, RDS)
- Auth: Clerk or Supabase Auth
- Hosting: Vercel (if Next.js) or Fly.io / Railway
- Email: Resend
- Observability: Sentry + PostHog
- Payments: Stripe

**Why this shape:** Every layer has a proven managed option. A solo founder can ship a real product on this stack in weeks, not months.

**Watch for:** Founders who want to self-host Postgres because "AWS is cheaper at scale." They are not at scale yet. Defer.

---

## 2. Mobile-First

**Shape:** The primary surface is a mobile app. Web may exist as a marketing site or admin panel only.

**Typical stack:**
- Mobile framework: Expo (React Native) unless the founder has specific iOS/Android native expertise
- Backend: Managed backend (Supabase, Firebase, Convex) to avoid running servers
- Database: Comes with the managed backend
- Auth: Comes with the managed backend, or Clerk
- Hosting: Managed backend handles it; marketing site on Vercel
- Push notifications: Expo's notification service or OneSignal
- Observability: Sentry (works for React Native)

**Why this shape:** Running a mobile app and a backend simultaneously as a solo founder is the fastest way to burn weeks. Managed backends collapse the complexity.

**Watch for:** Founders who want to ship native iOS + native Android simultaneously. Default to Expo unless there is a specific performance or platform-API requirement.

---

## 3. AI-Agent Product

**Shape:** An LLM or agent is the core product value. Users talk to an agent, hand off tasks to an agent, or consume agent-produced outputs.

**Typical stack:**
- Frontend: Next.js with streaming UI (AI SDK, assistant-ui, or custom)
- Backend: Next.js API routes or a Python/FastAPI server depending on how much orchestration logic lives server-side
- LLM provider: Anthropic (Claude) or OpenAI — pick one primary, note the fallback
- Orchestration: Direct SDK calls for simple agents; LangGraph or a custom graph for multi-step; MCP for tool integrations
- Vector database: Only if retrieval is a core feature. Otherwise defer.
- Database: Postgres (pgvector extension handles most retrieval needs at early stage)
- Auth: Clerk or Supabase Auth
- Hosting: Vercel if stateless; Fly.io if long-running server logic
- Observability: LangSmith or Langfuse for LLM traces; Sentry for errors; PostHog for product analytics

**Why this shape:** LLM products fail most often on (1) prompt quality, (2) cost visibility, (3) latency. The stack should surface all three early. A trace-capable observability layer is not optional here.

**Watch for:** Founders who want to self-host open-weights models before they have product-market fit. Managed APIs almost always win at pre-PMF stage on cost-of-iteration.

---

## 4. Data-Heavy Analytics

**Shape:** The product's value is in computing or visualizing something on a large or complex dataset. Think BI tools, ops dashboards, reporting products.

**Typical stack:**
- Frontend: Next.js or Remix; heavy chart library (Visx, Recharts, D3)
- Backend: Python (FastAPI) or TS with a dedicated analytics layer
- Primary database: Postgres
- Analytics warehouse: DuckDB (local) or ClickHouse / BigQuery / Snowflake (managed) depending on data volume. At early stage, DuckDB or Postgres is usually enough.
- ETL/ingestion: Dagster, Airbyte, or direct SQL depending on sophistication
- Auth: Clerk or Supabase Auth
- Hosting: Vercel for frontend; the warehouse vendor handles analytics workload
- Observability: Sentry + PostHog

**Why this shape:** Data products have a bimodal stack — a web application layer and a data layer that must not couple too tightly. Keep them separable.

**Watch for:** Founders who want to ship Snowflake or BigQuery on day one. Start with Postgres; graduate only when query performance forces it.

---

## 5. Marketplace

**Shape:** Two-sided or multi-sided — suppliers and buyers, or hosts and guests. Matching, payments, and trust/reviews are load-bearing.

**Typical stack:**
- Frontend: Next.js
- Backend: Next.js API routes or dedicated backend
- Database: Postgres
- Auth: Clerk or Supabase Auth; consider role-based access control carefully
- Payments: Stripe Connect (for marketplace payment flows specifically — not vanilla Stripe)
- Messaging between users: Postgres-backed first; upgrade to a hosted realtime service (Ably, Pusher, Supabase Realtime) if needed
- Search: Postgres full-text to start; Algolia or Meilisearch if search becomes a core UX surface
- Email: Resend
- Observability: Sentry + PostHog

**Why this shape:** Marketplaces have specific flows (Stripe Connect for split payments, messaging, reviews) that other archetypes don't. Name them explicitly in the tech stack.

**Watch for:** Founders trying to ship both sides of the marketplace at once. Usually one side should be curated or manually onboarded while the other self-serves.

---

## 6. Internal Tool Shipped as a Product

**Shape:** The founder built an internal tool for themselves or a small team and is now productizing it. Usually has unusual integration requirements (a specific CRM, a specific data source).

**Typical stack:**
- Whatever the internal tool was already built in, if it works. Rewriting to "productize" is almost always a mistake unless the internal version is genuinely unshippable.
- Add: multi-tenancy (workspace/org scoping), real auth, billing, onboarding flow.

**Why this shape:** The stack is already chosen. The work is productization, not rebuild.

**Watch for:** Founders who want to rewrite their internal tool in a "real" framework. The rewrite almost always stalls. Ship the existing stack with the productization layer bolted on.

---

## 7. Other / Doesn't Fit

If the product doesn't match any archetype above, walk the founder through the question: "What is the one most load-bearing technical requirement?" Then build the stack outward from that single requirement. Document explicitly that no standard archetype applied.

Examples where this happens:
- Hardware-integrated products
- High-frequency trading or low-latency products
- Products with regulatory requirements (HIPAA, PCI, SOC 2 from day one)
- Products with strong offline or on-device requirements
- Browser extensions where the extension itself is the product