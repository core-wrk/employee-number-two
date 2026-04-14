# Functional Requirements — Template and Examples

Internal reference for `epic-requirements-builder`. Use this to structure functional requirements consistently and to recognize when an FR is too broad, too vague, or actually two FRs pretending to be one.

---

## The Canonical Form

Every functional requirement follows this shape:

> **FR-NN:** [User role] can [single action] in order to [outcome]. [One sentence of clarifying detail about what the system does in response.]

- **User role** — specific: "signed-in admin," "free-tier user," "anonymous visitor," not "user"
- **Single action** — one verb per FR. If the sentence has "and" between two verbs, split into two FRs.
- **Outcome** — the user's goal, not a system behavior. "To download their data for backup" is an outcome. "To call the /export endpoint" is not.
- **Clarifying detail** — what the system does. Names the persistence, the response, the visible change.

---

## Good Examples

- **FR-01:** A signed-in user can request an export of their records in order to keep a local backup. The system queues a background job and sends the user an email with a signed download link when the export is complete.
- **FR-02:** An admin can deactivate another user's account in order to revoke their access. The target user's active sessions are invalidated within 60 seconds and they cannot sign in again until reactivated.
- **FR-03:** A free-tier user can view the first 50 rows of a dataset in order to evaluate whether the data fits their needs before upgrading. Beyond row 50, the table shows a paywall overlay with an upgrade CTA.

---

## Common Failure Patterns

### Too broad

> Bad: **FR-01:** A user can manage their account.

"Manage" contains a dozen actions. Split into specific FRs: update profile, change password, delete account, change plan.

### Multiple verbs in one FR

> Bad: **FR-02:** A user can create and edit and delete projects.

Split into FR-02 (create), FR-03 (edit), FR-04 (delete). Each has different edge cases, permissions, and acceptance criteria.

### Implementation dressed as requirement

> Bad: **FR-03:** The system calls POST /api/exports with a JSON payload.

That is an implementation detail, not a requirement. The requirement is what the user can do; the API shape is the implementer's choice within the constraints.

### No outcome

> Bad: **FR-04:** A user can click the export button.

Why? What happens next? The "in order to" clause forces clarity about the user's goal.

### Vague role

> Bad: **FR-05:** A user can access advanced features.

Which user? What makes them eligible? "A user on the Pro plan" or "A workspace admin" — the role determines permissions and acceptance criteria.

---

## When to Split an FR

Split when any of the following are true:

- Two different user roles can perform the action with different behavior
- The action has distinct success and error outcomes that need separate AC coverage
- The action is scoped to different states of the product (logged in vs. not, paid vs. free)
- The word "and" appears between verbs in the action clause

---

## When to Merge FRs

Merge when two "FRs" are actually the same action with different phrasing or cosmetically different detail. If the acceptance criteria for both would be identical, they are one FR.

---

## Role Taxonomy

Use consistent role names across FRs in the same epic. Common roles:

- **Anonymous visitor** — not signed in, no account
- **Signed-in user** — authenticated, default role
- **Free-tier user** — authenticated, no paid subscription
- **Paid user** — authenticated, on any paid plan. Subdivide by plan tier if relevant (Pro, Team, Enterprise).
- **Workspace member** — belongs to a workspace, not an admin
- **Workspace admin** — elevated permissions within a workspace
- **System admin / superuser** — operator role, typically internal

If the epic introduces a new role not in this list, define it explicitly at the top of the epic's functional requirements section.
