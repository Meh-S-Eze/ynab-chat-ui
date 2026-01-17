# Phase 2 Kickoff: Planning & PRD Creation

**Timeline:** Monday morning – Friday end of day
**Outcome:** Complete PRD + 30+ user stories ready for architecture

---

## Monday Morning: 9 AM – 12 PM

### Goal: Draft PRD Framework with BMAD Analyst

**What to do:**

1. Open Claude, ChatGPT, or your favorite AI chat tool
2. Copy this prompt exactly:

```
You are a BMAD Analyst Agent for the YNAB Chat UI Project.

My context:
- I have a YNAB MCP (Model Context Protocol) server with 30+ budget tools
- I want to build a Next.js + Node.js chat application
- Users chat with an AI to manage their budget (check balances, add transactions, review categories)
- Timeline: 4 weeks to MVP (chat working) + database persistence later
- Deployment: Railway (serverless)
- Budget: ~$10–20/month

Your job: Ask me 7 clarifying questions to build a PRD.

Focus on:
1. MVP scope (what features in the first 2 weeks?)
2. User types (who uses this? power users? mobile-first?)
3. Priorities (is speed more important than features?)
4. Success metrics (how do we know it's working?)
5. Constraints (any regulatory, compliance issues with YNAB data?)
6. Integration (which YNAB MCP tools are essential?)
7. Non-functional requirements (response time? offline mode?)

Start with your questions, then we'll build the PRD together.
```

3. Paste your context and answer Claude's questions (takes ~1 hour)

4. Save Claude's analysis to `docs/PRD-ANALYSIS.md`

**Example Clarifying Questions Claude Might Ask:**

```
1. "What's the ONE most important action a user should do in chat?
   Example: Check their checking account balance?"

2. "Should users be able to MODIFY data (add transaction) or just READ?"

3. "What's your target response time? 
   < 1 second? < 2 seconds? < 5 seconds?"

4. "Do you need user accounts/authentication from day 1?
   Or test with demo account first?"

5. "Which 3 YNAB MCP tools are ESSENTIAL for MVP?
   (e.g., get_budget, get_transactions, get_accounts)"

6. "What's failure? 
   If chat times out, what should happen? Retry? Show error?"

7. "Mobile or desktop first?"
```

**Your answers should be specific:**
```
❌ "Make it fast"
✅ "Response time < 2 seconds, or show loading state + timeout after 5s"

❌ "Support all YNAB features"
✅ "MVP: read-only. Essential tools: get_budget, get_accounts, get_transactions. 
    Phase 2: add add_transaction"

❌ "Authenticate users"
✅ "Start with demo account (no auth). Add auth in Phase 2."
```

**Time:** 1–1.5 hours

---

## Tuesday – Wednesday: 2 PM – 4 PM Each Day

### Goal: Expand PRD Framework

**Day: Tuesday**

1. Read Claude's analysis from Monday

2. Ask Claude (as Analyst):
```
You're a BMAD Analyst. Based on my answers to your 7 questions, 
write a PRD outline:

1. Project Summary (1 paragraph: what, why, success metrics)
2. MVP User Stories (5–8 specific stories with acceptance criteria)
3. Phase 2 Outline (brief description of next features)
4. Non-Functional Requirements (response time, uptime, error handling)
5. Constraints (timeline, budget, tech stack)
6. Assumptions & Dependencies
7. Validation Checklist (how do we know MVP is done?)

Format each story as:
## Story X: [Title]
- **As a:** [user type]
- **I want to:** [action]
- **So that:** [outcome]
- **Acceptance Criteria:**
  1. [specific, testable criterion]
  2. [another criterion]
  ...
```

3. Review Claude's output:
   - Is each story testable? (Can QA verify it works?)
   - Are acceptance criteria specific? (Not vague "should work")
   - Is scope clear? (What's MVP vs Phase 2?)

4. Flag unclear items:
   ```
   "Story 1.2 is unclear. What exactly should the chat display?
   Show me an example conversation flow."
   ```

5. Save to `docs/PRD-DRAFT.md`

**Day: Wednesday**

1. Iterate with Claude on unclear stories:
   ```
   "Claude, rewrite Story 1.3 using this example:
   
   User: 'What's my checking account balance?'
   AI: 'Your checking account has $1,234.56'
   
   Make the acceptance criteria match this flow."
   ```

2. Ask Claude for non-functional requirements:
   ```
   "Claude, for non-functional requirements, clarify:
   - Response time: < 2 seconds for chat messages?
   - MCP tool calls: < 5 seconds each (with timeout)?
   - Error handling: Show error message to user?
   - Database: In-memory for MVP, PostgreSQL later?"
   ```

3. Review constraints:
   - Timeline: 4 weeks to MVP ✓
   - Budget: $10–20/month on Railway ✓
   - Tech stack: Next.js + Node.js + PostgreSQL ✓
   - Team: You + AI agents (Kilocode, Claude) ✓

4. Save final PRD to `docs/PRD.md`

**Time:** 1–1.5 hours each day

---

## Thursday: 9 AM – 12 PM

### Goal: Validation Checklist + Approval

**Your task:**

1. Ask Claude to run PRD validation:
   ```
   "Claude, validate this PRD against BMAD standards:
   
   - Is every story testable? (Can QA verify with yes/no?)
   - Are acceptance criteria specific? (Not vague?)
   - Is scope clear? (MVP vs Phase 2?)
   - Are risks addressed? (Edge cases covered?)
   - Are constraints realistic? (4 weeks feasible?)
   - Are dependencies clear? (Story 1.2 needs 1.1?)
   
   Report any issues."
   ```

2. Fix any issues Claude flags:
   ```
   Issue: "Story 1.3 doesn't handle 'No data' case"
   Fix: Add acceptance criterion: "If budget empty, show message: 
        'No budget data. Add a budget in YNAB first.'"
   ```

3. Get final approval from Claude:
   ```
   "Claude, is this PRD ready for Phase 3 (Architecture)?"
   ```

4. Commit to Git:
   ```bash
   git add docs/PRD.md docs/PRD-*.md
   git commit -m "Phase 2: PRD complete and approved"
   git push origin main
   ```

**Time:** 1–2 hours

---

## Thursday: 2 PM – 5 PM

### Goal: Break PRD into Stories by Sprint

**Your task:**

1. Ask Claude (as Scrum Master):
   ```
   "You're a BMAD Scrum Master. Break this PRD into 4 sprints:
   
   - Sprint 1 (Week 1): Chat UI, mock backend [3–4 stories]
   - Sprint 2 (Week 2): Real MCP integration [3–4 stories]
   - Sprint 3 (Week 3): Database + persistence [3–4 stories]
   - Sprint 4 (Week 4): Polish + production [3–4 stories]
   
   For each sprint, list stories as:
   
   ## Sprint 1
   ### Story 1.1: Chat Message Display
   - **Acceptance Criteria:**
     1. Messages display in scrollable list
     2. Each message shows sender, time, text
     ...
   
   ### Story 1.2: Chat Input Form
   - **Acceptance Criteria:**
     1. User can type message
     2. Send button submits
     ...
   
   (Continue for all sprints)
   
   Make sure each story:
   - Takes 1 day max to code
   - Is testable (QA can verify)
   - Doesn't depend on stories outside sprint
   - Builds on previous sprint"
   ```

2. Create story directory structure:
   ```bash
   mkdir -p docs/stories/sprint-{1,2,3,4}
   ```

3. Create individual story files from Claude's output:
   ```
   docs/stories/sprint-1/story-1.1-chat-display.md
   docs/stories/sprint-1/story-1.2-chat-input.md
   docs/stories/sprint-1/story-1.3-mock-backend.md
   docs/stories/sprint-1/story-1.4-responsive.md
   ...
   ```

4. Save all story files to Git (you'll add in Friday commit)

**Time:** 1–2 hours

---

## Friday: 9 AM – 10 AM

### Goal: Review + Approval

**Your task:**

1. Review PRD one more time (fresh eyes):
   - Are acceptance criteria testable?
   - Is MVP scope clear?
   - Are edge cases covered?

2. Review sprint structure:
   - Sprint 1 self-contained? (No dependencies on Sprint 2)
   - Stories take 1 day each?
   - 4 sprints = 4 weeks? ✓

3. Spot-check one story (e.g., Story 1.1):
   - Can a developer code this in 1 day?
   - Can QA test it in 1 hour?
   - All acceptance criteria testable?

4. Final commit:
   ```bash
   git add docs/stories/
   git commit -m "Phase 2: Story breakdown by sprint"
   git push origin main
   ```

5. Approve:
   ```
   ✅ PRD complete
   ✅ 16+ stories ready
   ✅ Sprint 1 assigned
   ✅ Ready for Phase 3
   ```

**Time:** 30 minutes

---

## Friday: 10 AM – 11 AM

### Goal: Schedule Phase 3 Kickoff

**Your task:**

1. Mark your calendar: **Monday 9 AM = Phase 3 Kickoff**

2. Read Phase 3 intro from BMAD-WORKFLOW.md
   - What will you do Monday?
   - Who's the Architect Agent?

3. Prepare for Phase 3:
   - You'll design system architecture
   - Break stories into more detail
   - Create deployment plan

**Time:** 15 minutes

---

## Phase 2 Checklist

**By Friday EOD, you should have:**

- [ ] PRD document (docs/PRD.md) with:
  - [ ] Project summary (1 paragraph)
  - [ ] 5–8 MVP user stories
  - [ ] Acceptance criteria for each
  - [ ] Non-functional requirements
  - [ ] Constraints & timeline
  - [ ] Success metrics

- [ ] Story breakdown (docs/stories/) with:
  - [ ] 4 sprint folders (sprint-1 through sprint-4)
  - [ ] 3–4 story files per sprint
  - [ ] 16+ total stories
  - [ ] Each story has acceptance criteria

- [ ] Analysis docs (docs/PRD-*.md) with:
  - [ ] Claude's clarifying questions & your answers
  - [ ] PRD analysis & validation

- [ ] Git commits:
  - [ ] Phase 2 PRD commit
  - [ ] Phase 2 story breakdown commit
  - [ ] Both pushed to `main` branch

---

## Common Mistakes to Avoid

❌ **"I'll just start coding"**
- Phase 2 takes 5 days but saves 2 weeks of rework
- Do this right, your code will be 10x faster

❌ **"This story is clear enough"**
- If you wouldn't code it in 1 day, it's not clear
- Ask Claude to make it more specific

❌ **"We'll figure out edge cases later"**
- Write acceptance criteria that cover edge cases
- "What if user X happens?" → New acceptance criterion

❌ **"Let's skip non-functional requirements"**
- "Response time < 2s" is the difference between viable/broken
- Think about: speed, reliability, error handling

❌ **"Acceptance criteria can be vague"**
- ❌ "Chat should work"
- ✅ "User can type message, hit Enter, message appears in list within 2 seconds"

---

## Time Investment

```
Monday:    1.5 hours
Tuesday:   1.5 hours
Wednesday: 1.5 hours
Thursday:  2.5 hours (validation + story breakdown)
Friday:    1 hour (review + approval)
─────────────────────
TOTAL:     8 hours (spread across 5 days)
```

**Return on investment:** 8 hours now = save 2 weeks of coding later

---

## Next: Phase 3 (Architecture)

**Monday Morning (1 week from now):**
- Design system architecture
- Write Architecture Decision Records (ADRs)
- Break stories into more detail
- Create deployment plan

**Expected outcome:** Architecture approved, Sprint 1 ready to code

---

**You're ready. Start Monday. 🚀**
