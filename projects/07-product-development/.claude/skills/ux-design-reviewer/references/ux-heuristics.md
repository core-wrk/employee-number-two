# UX Heuristics

Internal reference for `ux-design-reviewer`. Nielsen's 10 plus mobile/responsive and accessibility extensions. Walk through these in order for every review.

---

## Nielsen's 10 Usability Heuristics

### 1. Visibility of System Status

The system should always keep users informed about what is going on, through appropriate feedback within reasonable time.

- Loading states for any operation >200ms
- Progress indicators for long operations
- Confirmation of successful actions
- Current location/step in multi-step flows

**Common violations:** silent submissions, no loading spinner on slow network, no confirmation after a successful save.

### 2. Match Between System and the Real World

Speak the users' language. Use words, phrases, and concepts familiar to the user, not system-oriented terms.

- Button labels use the user's vocabulary, not the developer's
- Error messages describe what the user did and what to do next, not stack traces or error codes
- Dates and times in the user's format and timezone

**Common violations:** "400 Bad Request" shown to a user, jargon like "entity" or "object" in UI copy.

### 3. User Control and Freedom

Users often choose functions by mistake. Provide a clearly marked "emergency exit" to leave the unwanted state.

- Every modal has a visible close affordance
- Every destructive action has an undo or a confirmation
- Users can navigate back out of a flow without losing their place
- Long forms don't discard data on navigation

**Common violations:** modal with no close button, destructive delete with no confirmation, form that clears on browser back.

### 4. Consistency and Standards

Users should not have to wonder whether different words, situations, or actions mean the same thing. Follow platform and product conventions.

- Same verb for the same action across screens ("Save" everywhere, not "Save" in one place and "Submit" in another)
- Same icon for the same concept
- Standard form patterns (primary button on the right in web; iOS conventions on iOS)

**Common violations:** three different words for the same action, inconsistent placement of primary actions.

### 5. Error Prevention

Even better than good error messages is a careful design that prevents a problem from occurring in the first place.

- Disable actions that cannot succeed (submit button disabled until form is valid)
- Confirm destructive actions
- Provide format hints for inputs that have format requirements (date, phone, currency)
- Validate inline as the user types where appropriate

**Common violations:** allowing a form submission that will definitely fail, requiring the user to guess the required format.

### 6. Recognition Rather Than Recall

Minimize the user's memory load by making objects, actions, and options visible.

- Show the user's prior input alongside the next step
- Autocomplete or suggest rather than require typing
- Label form fields (labels stay visible, don't rely solely on placeholders)

**Common violations:** multi-step wizard that hides prior answers, placeholder-only labels that disappear on focus.

### 7. Flexibility and Efficiency of Use

Accelerators — unseen by the novice user — may often speed up the interaction for the expert user.

- Keyboard shortcuts for common actions
- Bulk actions on lists
- Saved filters or views for repeat tasks
- "Remember me" on login

**Common violations:** no keyboard nav anywhere; every action requires the mouse.

### 8. Aesthetic and Minimalist Design

Dialogues should not contain information that is irrelevant or rarely needed.

- Every element on screen earns its place
- Secondary actions are visually subordinate to primary actions
- Whitespace is used; screens are not cluttered

**Common violations:** screen with three equally-prominent primary buttons, information-dense dashboard with no visual hierarchy.

### 9. Help Users Recognize, Diagnose, and Recover From Errors

Error messages should be expressed in plain language, precisely indicate the problem, and constructively suggest a solution.

- Error messages name the specific field or input that is wrong
- Error messages suggest the specific fix
- Errors are visually distinct (color, icon, position)
- Error messages use color alone only when accompanied by text or icon (color-blind users)

**Common violations:** "Invalid input" with no indication of which field, red border on a field with no message.

### 10. Help and Documentation

Even though it is better if the system can be used without documentation, it may be necessary to provide help.

- Contextual help near complex fields
- Empty states that explain how to populate them
- First-run tours for genuinely novel interactions (use sparingly)

**Common violations:** empty dashboard with no indication of what to do first.

---

## Accessibility Extensions

### A1. Color Contrast (WCAG AA)

Text contrast ratio against its background must be at least 4.5:1 for normal text and 3:1 for large text.

**Common violations:** light gray placeholder text, low-contrast secondary buttons, error text on a tinted background.

### A2. Keyboard Navigation

Every interactive element must be reachable and operable with a keyboard alone.

**Common violations:** custom dropdowns that cannot be opened without a mouse, modals that don't trap focus.

### A3. Screen Reader Labels

Every interactive element must have an accessible name that a screen reader can announce.

**Common violations:** icon-only buttons without aria-label, form fields without associated labels.

### A4. Focus Indication

The currently focused element must be visually distinguishable.

**Common violations:** `outline: none` in CSS with no replacement focus style.

### A5. Color-Independent Information

Information conveyed by color must also be conveyed by at least one other means (text, icon, pattern).

**Common violations:** "required" fields indicated only by red asterisks, error states indicated only by red borders.

---

## Mobile / Responsive Extensions

### M1. Touch Target Size

Interactive elements on touch devices should be at least 44×44 CSS pixels.

**Common violations:** densely packed buttons, close icons too small to tap accurately.

### M2. Responsive Layout

The layout must remain usable at every breakpoint the product targets (phone, tablet, desktop).

**Common violations:** content that overflows horizontally on mobile, modals that exceed the viewport.

### M3. Input Types

Use the correct `inputmode` and `type` for each input so mobile keyboards match the expected input.

**Common violations:** email fields with default keyboard instead of email keyboard, phone fields without `inputmode="tel"`.

### M4. Safe Area

On mobile, the UI should respect the device's safe area (notch, home indicator).

**Common violations:** bottom navigation that sits under the iPhone home indicator.

---

## When To Skip a Heuristic

Skip only when the UI surface genuinely doesn't expose the heuristic (e.g., a purely textual error screen with no input doesn't need to be evaluated against M3). Note the skip explicitly rather than silently omitting the heuristic.
