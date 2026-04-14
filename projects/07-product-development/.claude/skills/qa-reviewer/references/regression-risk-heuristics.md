# Regression Risk Heuristics

Internal reference for `qa-reviewer`. Use these heuristics to identify areas where the implementation for this epic might have broken something outside the epic's scope. Name each risk explicitly in the QA report with a specific check the founder should perform.

---

## High-risk change types

These change types have a disproportionate likelihood of introducing regressions. Flag them always.

### Shared module changes

If the implementation modified a module used by other parts of the product (utility functions, shared hooks, shared components, shared types), the risk is that consumers outside this epic now behave differently.

**Check:** grep for imports of the changed module. Confirm every caller still works. For a coding agent: ask it to list every import site and describe whether the call-site assumptions still hold.

### Database schema changes

Migrations, new columns, changed constraints, dropped columns, renamed tables — every one of these can break code that queries the old shape.

**Check:** enumerate every place in the codebase that queries the affected table or column. For a coding agent: ask it to list every ORM model, raw query, or migration that references the changed schema element.

### Auth or authorization changes

Any change to middleware, role checks, permission predicates, or session handling is high-risk. Auth regressions are security incidents.

**Check:** enumerate every route and list the auth requirement for each. Compare to pre-change state. Particularly: anonymous-access routes that might have inadvertently become gated, and admin-only routes that might have inadvertently become public.

### API contract changes

Renaming endpoints, changing request/response shapes, changing status codes, changing error formats — breaks every client that depends on the old contract.

**Check:** if there are published API contracts (OpenAPI spec, typed client SDK, frontend code that calls the backend), diff them against the implementation. Flag any breaking change.

### Dependency upgrades

A major or minor version bump of a framework, ORM, or critical library can change behavior in ways the implementer didn't notice.

**Check:** read the changelog of the upgraded dependency between the old and new versions. Flag any breaking changes or deprecations relevant to how the product uses the dependency.

---

## Medium-risk change types

### Background job changes

New jobs, changed job signatures, changed retry logic — can cause silent failures that only surface when the job runs in production.

**Check:** verify the job is registered, the queue is configured, the retry policy matches the NFR. Particularly: jobs with exponential backoff that could pile up during an outage.

### Third-party service integrations

A new Stripe webhook, a new email provider, a new analytics event — each introduces a surface that can fail silently in production.

**Check:** verify the integration has error handling. Verify it emits observable events. Verify there is a fallback or at least a logged failure path.

### Caching changes

Adding, changing, or invalidating caches can mask bugs or introduce staleness. Cache-related bugs are notoriously hard to reproduce.

**Check:** identify every cache layer (browser, CDN, application, database query cache). Verify invalidation triggers match data mutations.

### Configuration or environment variable changes

New env vars, changed defaults, changed configuration schemas — breaks deploys in environments that haven't been updated.

**Check:** confirm the new config is documented. Confirm staging and production will receive the update before deploy. Confirm there is a sensible default for local development.

---

## Low-risk change types (but still worth a glance)

- UI-only changes to a self-contained component
- New additive endpoints with no shared code
- Pure additions to types or interfaces
- Documentation-only changes

These rarely regress, but it is still worth confirming that is what they actually are and not something with hidden coupling.

---

## The "did it touch it?" shortcut

For any epic, the fastest regression risk scan is:

1. List the files the implementation touched
2. For each file, answer: does anything outside this epic import, extend, or depend on this file?
3. For each "yes," flag a regression risk with a specific check

In agent mode, you can ask the coding agent to enumerate this directly. In human mode, you may need the founder to forward the question to the engineer.

---

## Recording regression risks in the report

Every regression risk in the QA report should be written as:

- **Risk:** [one-sentence description of what could break]
- **Location:** [file, function, or migration where the risk lives]
- **Recommended check:** [specific action — run a specific test, manually check a specific page, query the database for a specific condition]

Vague risks ("there could be regressions elsewhere") are not useful. Specific risks ("the `getUser` helper at `src/lib/users.ts:42` is called by 14 other places; any behavior change affects all of them") are actionable.
