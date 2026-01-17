# Story Template

Use this template for every story. Copy and fill in.

---

# Story X.Y: [Title]

## Description

[1–2 sentences describing what the user can do after this story is complete]

Example: "Users can see a list of chat messages in chronological order, with sender, timestamp, and message text displayed."

## User Story

- **As a:** [user type, e.g., "YNAB power user", "mobile-first user"]
- **I want to:** [action, e.g., "see my budget balance in chat"]
- **So that:** [outcome, e.g., "I can quickly check my budget without opening the app"]

## Acceptance Criteria

[List 5–8 specific, testable criteria. Each should be verifiable with "yes" or "no".]

1. [Specific criterion - be measurable, not vague]
2. [Another criterion]
3. [Another criterion]
4. [Another criterion]
5. [Another criterion]

**Example:**
1. Messages display in a scrollable list
2. Each message shows: sender name, timestamp (HH:MM format), and message text
3. Messages are ordered with newest first
4. The list automatically scrolls to show the newest message
5. On desktop browsers (Chrome, Safari, Firefox), text wraps and layout doesn't break
6. On mobile (iOS Safari, Chrome), layout remains readable

## Edge Cases

[Describe situations that could break this story. For each, note how it should behave.]

- **Empty state:** If no messages exist, display "No messages yet"
- **Long message:** Message longer than 500 characters wraps to multiple lines
- **Same sender consecutive messages:** [Decision: show sender once? Each message?]
- **Timestamps across days:** [Decision: show date separator? Show full date?]

## Dev Notes

[Technical hints for the developer]

- Use React hooks: `useState`, `useEffect`
- CSS: Flexbox or Grid for layout
- No backend needed (use mock data in component state)
- Timestamp formatting: `new Date().toLocaleTimeString('en-US', { hour: '2-digit', minute: '2-digit' })`
- Styling: Follow design system in `styles/globals.css`

## QA Notes

[Testing instructions for QA. Be specific and reproducible.]

1. Add 5 test messages manually to component
2. Verify list shows all 5 messages
3. Scroll to top, verify oldest message is visible
4. Scroll to bottom, verify newest message is visible
5. Resize browser to 320px wide (mobile), verify text wraps
6. Resize browser to 1440px wide (desktop), verify layout works
7. Clear all messages, verify "No messages yet" displays

## Testing Checklist

- [ ] Acceptance criteria #1: _______ ✓ / ✗
- [ ] Acceptance criteria #2: _______ ✓ / ✗
- [ ] Acceptance criteria #3: _______ ✓ / ✗
- [ ] Acceptance criteria #4: _______ ✓ / ✗
- [ ] Acceptance criteria #5: _______ ✓ / ✗
- [ ] Acceptance criteria #6: _______ ✓ / ✗
- [ ] Edge case: Empty state ✓ / ✗
- [ ] Edge case: Long message ✓ / ✗
- [ ] Performance: Loads in < 100ms ✓ / ✗
- [ ] Accessibility: Keyboard navigation works ✓ / ✗

## Definition of Done

- [ ] Code written and peer reviewed
- [ ] All acceptance criteria verified (QA checklist complete)
- [ ] Unit tests written (if applicable)
- [ ] Integration tests pass
- [ ] No console errors or warnings
- [ ] Deployed to staging
- [ ] Works in Chrome, Safari, Firefox
- [ ] Mobile responsive (320px to 1440px)
- [ ] Documentation updated (if needed)

## Story Dependencies

[List other stories this story depends on. If none, say "None (self-contained)"]

Example:
- Depends on Story 1.1 (Chat display must exist before we can input messages)
- Does NOT depend on Story 2.1 (backend can be mocked)

## Story Points / Time Estimate

**Estimated effort:** 1 day (6–8 hours)

**Breakdown:**
- Design: 0.5 hours
- Code: 4–5 hours
- Testing: 1 hour
- Code review & fixes: 1 hour

## Notes

[Any additional context, decisions, or learnings]

- Decided to order newest-first (not oldest-first) based on chat UX patterns
- Timestamp format (HH:MM) chosen for brevity; can add date later
- No avatars in MVP; can add in Phase 2

---

## How to Use This Template

1. Copy this file
2. Rename to `story-X.Y-[title].md`
3. Fill in each section
4. Save to `docs/stories/sprint-N/`
5. Commit to Git

**Example filename:** `story-1.1-chat-display.md`
