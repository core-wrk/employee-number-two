# Non-Functional Requirements — Category Guide

Internal reference for `epic-requirements-builder`. For each epic, walk through these categories and ask whether a measurable NFR is warranted. Not every epic needs an NFR in every category. Skip the ones that don't apply — but be able to justify the skip.

---

## Canonical NFR Form

> **NFR-NN:** [Category]: [specific, measurable requirement with a number]

If an NFR doesn't contain a number or a named threshold, it isn't a requirement — it is a wish.

---

## Performance

Ask:
- What is the user-perceived latency target for the primary action?
- Is there a throughput requirement (requests per second, concurrent users)?
- Are there background jobs with their own latency targets?

**Examples:**
- **NFR-01:** Performance: p95 latency for the export request submission is under 500ms; export completion for up to 10,000 rows is under 30 seconds.
- **NFR-02:** Performance: dashboard first-contentful-paint under 1.5 seconds on a 3G connection.

---

## Scalability

Ask:
- What load does this epic need to support on day one?
- What load does it need to support in three months?
- Are there known hot spots (a single-workspace limit, a single-user limit)?

**Examples:**
- **NFR-01:** Scalability: supports 1,000 concurrent exports across the system without queue backlog exceeding 5 minutes.
- **NFR-02:** Scalability: a single workspace can hold up to 1,000,000 records without degraded search latency.

---

## Security and Privacy

Ask:
- Does this epic touch PII, credentials, or payment data?
- What authorization checks are required?
- Are there data retention or deletion requirements?
- Does the epic introduce any new attack surface (file upload, user-generated URLs, iframe embeds)?

**Examples:**
- **NFR-01:** Security: export files contain only data the requesting user has read permission to; cross-tenant data leakage is a blocker bug, not a P2.
- **NFR-02:** Privacy: generated export files are deleted from storage 7 days after generation; download links expire after 24 hours.

---

## Accessibility

Ask:
- Is this a user-facing UI surface?
- What WCAG level applies (AA is the typical target)?
- Does the interaction rely on color, hover, or drag alone (all of which fail accessibility)?

**Examples:**
- **NFR-01:** Accessibility: meets WCAG 2.1 AA. All interactive elements are keyboard-navigable; color contrast ratios meet AA; all images have alt text; error states are announced to screen readers.
- **NFR-02:** Accessibility: the export table supports keyboard navigation (arrow keys for rows, enter to select, escape to close).

---

## Reliability

Ask:
- What is the uptime target?
- What happens on failure — retry, user-visible error, silent degradation?
- Are there idempotency requirements (a duplicate request should not duplicate effects)?

**Examples:**
- **NFR-01:** Reliability: export jobs retry up to 3 times on transient failures with exponential backoff; after 3 failures, the user receives an email with a support link.
- **NFR-02:** Reliability: the /submit endpoint is idempotent — the same idempotency key submitted twice within 24 hours returns the original result without re-executing.

---

## Observability

Ask:
- What events should be logged for debugging?
- What metrics should be emitted for monitoring?
- What errors should trigger alerts vs. fail silently?

**Examples:**
- **NFR-01:** Observability: every export job emits `export.requested`, `export.started`, `export.completed`, and `export.failed` events with the user ID, row count, and duration.
- **NFR-02:** Observability: export failure rate over 5% in a 15-minute window triggers a Sentry alert.

---

## Compatibility

Ask:
- Which browsers must be supported (modern evergreens only, or IE11)?
- Which mobile platforms and OS versions?
- What API versions must be compatible?

**Examples:**
- **NFR-01:** Compatibility: supported on the latest two versions of Chrome, Firefox, Safari, and Edge. No IE support.
- **NFR-02:** Compatibility: the mobile app targets iOS 15+ and Android API 29+.

---

## Cost

Ask (especially for AI-heavy epics):
- What is the per-request cost target?
- Are there caching opportunities that reduce cost?
- Are there hard caps on LLM token spend per user or per workspace?

**Examples:**
- **NFR-01:** Cost: p95 per-chat-session cost is under $0.05 via prompt caching and model tiering (Haiku for routing, Sonnet for generation).
- **NFR-02:** Cost: free-tier users are capped at 100 LLM requests per day, enforced server-side.

---

## When to Skip a Category

Skip a category when the epic genuinely has no meaningful requirement in it. A backend-only epic with no UI can skip Accessibility. A purely internal admin epic may not need Compatibility. A synchronous, simple epic may not need Reliability beyond the framework default.

But: **never skip Security/Privacy without explicit justification.** Every user-facing epic has a security surface even if it is small. Name the requirement explicitly, even if it is "no new attack surface introduced."
