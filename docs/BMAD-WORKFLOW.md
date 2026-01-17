# BMAD Workflow for YNAB Chat UI

**Complete reference for all 4 phases of BMAD development.**

## Quick Overview

BMAD (Build → Model → Architect → Deploy) is a structured methodology for AI-assisted development that prevents context loss and keeps projects on track.

**Your phases:**
- **Phase 1 (Analysis):** Validate the idea, explore technical risks → 3 days
- **Phase 2 (Planning):** Create detailed PRD with user stories → 1 week
- **Phase 3 (Solutioning):** Design architecture, break into sprints → 1 week
- **Phase 4 (Implementation):** Build in sprints (3–4 weeks)

**Total timeline:** 4–6 weeks to MVP

---

## Phase 1: Analysis (3 Days)

### Day 1: Problem Validation

**Goal:** Confirm the problem is worth solving

**Your task:**
```
1. Define the core problem:
   - Users want to manage YNAB budget via chat ✓ (from MCP)
   - Why? Faster than mobile/web interface
   - For whom? YNAB power users + mobile-first users

2. Validate assumptions:
   - Is chat faster than YNAB mobile? (UX research or user interviews)
   - Will users actually use it? (Early user feedback)
   - Is there demand? (Upvotes on YNAB forum, Discord, etc.)

3. Document findings:
   - Save to docs/PHASE-1-ANALYSIS.md
```

### Day 2: Technical Feasibility

**Goal:** Confirm the solution is feasible

**Your task:**
```
1. Validate MCP integration:
   - Can the YNAB MCP talk to a Next.js backend? ✓ (yes)
   - What's the latency? (test: ~200–500ms per tool call)
   - Error handling? (MCP can timeout, need retry logic)

2. Validate tech stack:
   - Next.js + Node.js + PostgreSQL on Railway? ✓ (tested)
   - Can we deploy in 1 day? ✓ (yes, Railway is fast)
   - Cost? (~$5–20/month on hobby tier)

3. Identify blockers:
   - YNAB API rate limits? (999 calls/hour, plenty)
   - MCP reliability? (Need error handling)
   - Cold starts? (Railway starts fast, <1s)

4. Document findings:
   - Save to docs/PHASE-1-TECHNICAL.md
```

### Day 3: Risk Assessment

**Goal:** Identify top 3 risks + mitigation

**Your task:**
```
1. Risk 1: "MCP tool calls are too slow"
   - Mitigation: Cache results, show loading state, timeout after 5s
   - Impact: High (affects UX)
   - Probability: Medium (depends on YNAB API)
   - Action: Test with real data in Phase 3

2. Risk 2: "User loses session mid-chat"
   - Mitigation: Store chat history in PostgreSQL
   - Impact: High (frustrating)
   - Probability: Low (Railway is reliable)
   - Action: Implement in Phase 4, test error recovery

3. Risk 3: "Can't modify transactions via chat"
   - Mitigation: Start with read-only, add writes in Phase 2
   - Impact: Medium (MVP doesn't need writes)
   - Probability: Low (MCP has tools)
   - Action: Validate MCP tools in Phase 2 PRD

4. Document findings:
   - Save to docs/PHASE-1-RISKS.md
```

### Phase 1 Deliverables

```
docs/
├── PHASE-1-ANALYSIS.md      # Problem validation
├── PHASE-1-TECHNICAL.md     # Tech stack + feasibility
└── PHASE-1-RISKS.md         # Top 3 risks + mitigation
```

**Approval:** "Phase 1 complete. Ready to plan PRD." → Move to Phase 2

---

## Phase 2: Planning (1 Week)

### Day 1: PRD Framework

**Goal:** Clarify all requirements with BMAD Analyst

**Your task:**
```
1. Use Analyst Agent:
   - Prompt: "You are a BMAD Analyst for the YNAB Chat UI.
     My context: [paste Phase 1 findings]
     Ask me 7 clarifying questions to build a PRD."

2. Answer questions about:
   - User stories (what users do in chat)
   - Acceptance criteria (how we measure success)
   - MVP scope (what's essential, what's Phase 2)
   - Non-functional requirements (speed, reliability)
   - Constraints (budget, timeline)
   - Integrations (YNAB MCP, database, auth)

3. Save responses to docs/PRD-DRAFT.md
```

### Days 2–3: Expand PRD

**Goal:** Create detailed, clear PRD

**Your task:**
```
1. Ask Analyst to expand PRD:
   - Project summary (1 sentence what, why, success metrics)
   - Phase 1 user stories (5–10 specific stories)
   - Phase 2–4 outlines (brief descriptions)
   - Non-functional requirements (response time <2s, 99.5% uptime)
   - Constraints (4-week timeline, Railway budget)
   - Assumptions & dependencies
   - Validation checklist

2. Review and clarify:
   - Is Story 1.1 clear enough to code?
   - What does "success" look like for Story 1.3?
   - Are acceptance criteria testable?

3. Iterate until PRD is solid

4. Save to docs/PRD.md
```

### Day 4: Story Breakdown

**Goal:** Break PRD into sprint-sized stories

**Your task:**
```
1. Ask Scrum Master Agent:
   - Prompt: "Break this PRD into 4 sprints of stories.
     Each story: 1 day max. Include acceptance criteria."

2. Create story files:
   docs/stories/
   ├── sprint-1/
   │   ├── story-1.1-chat-display.md
   │   ├── story-1.2-chat-input.md
   │   ├── story-1.3-mock-backend.md
   │   └── story-1.4-responsive.md
   ├── sprint-2/
   │   ├── story-2.1-express-api.md
   │   ├── story-2.2-mcp-client.md
   │   ├── story-2.3-error-handling.md
   │   └── story-2.4-logging.md
   ├── sprint-3/
   └── sprint-4/

3. For each story, include:
   - Description (1 paragraph)
   - Acceptance criteria (5–8 specific, testable items)
   - Edge cases (what if user X happens?)
   - Dev notes (tech specifics)
   - QA notes (how to test)
   - Blockers (dependencies on other stories)
```

### Day 5: Review & Approval

**Goal:** Approve PRD + stories

**Your task:**
```
1. Review PRD for clarity:
   - Is every story testable?
   - Are acceptance criteria specific?
   - Are edge cases covered?

2. Validate story order:
   - Sprint 1 stories don't depend on Sprint 2? ✓
   - Risks from Phase 1 addressed? ✓

3. Approve: "PRD and stories ready for architecture"

4. Commit to Git:
   git add docs/PRD.md docs/stories/
   git commit -m "Phase 2: PRD and story breakdown complete"
   git push
```

### Phase 2 Deliverables

```
docs/
├── PRD.md                   # Complete PRD
└── stories/
    ├── sprint-1/
    │   └── [4 story files]
    ├── sprint-2/
    ├── sprint-3/
    └── sprint-4/
```

**Success Metrics:**
- ✅ PRD approved
- ✅ 30+ stories ready
- ✅ Sprint 1 assigned to developers

---

## Phase 3: Solutioning (1 Week)

### Days 1–2: Architecture Design

**Goal:** Design system architecture

**Your task:**
```
1. Ask Architect Agent:
   - Prompt: "Design the architecture for this YNAB chat app.
     PRD: [paste PRD]
     Provide:
     - System components (frontend, backend, database, MCP)
     - Data flow diagrams (text-based)
     - Integration points
     - 3 Architecture Decision Records (ADRs)
     - Tech stack summary
     - Security considerations"

2. Review architecture:
   - Is it simple? (3–4 components max)
   - Does it match the PRD?
   - Are integration points clear?

3. Flag unclear decisions:
   - "Why in-memory state for MVP?"
   - "How do we handle MCP timeouts?"

4. Iterate with Architect

5. Save to docs/ARCHITECTURE.md + docs/ADRs/
```

### Days 3–4: Sprint Planning

**Goal:** Create sprint breakdown with stories

**Your task:**
```
1. Ask Scrum Master:
   - Prompt: "For each story, create:
     - Story description
     - Acceptance criteria (5–8)
     - Edge cases
     - Testing approach
     - Dev notes
     - QA notes"

2. Create story detail files:
   docs/stories/
   ├── sprint-1/
   │   ├── story-1.1-chat-display.md
   │   ├── story-1.2-chat-input.md
   │   ├── story-1.3-mock-backend.md
   │   └── story-1.4-responsive.md
   ...

3. Review each story:
   - Can developer code this in 1 day? ✓
   - Are acceptance criteria testable? ✓
   - Are edge cases covered? ✓
```

### Day 5: Review & Approval

**Goal:** Approve architecture + stories

**Your task:**
```
1. Review architecture + stories for clarity

2. Approve: "Architecture and stories ready for dev"

3. Commit to Git:
   git add docs/ARCHITECTURE.md docs/ADRs/ docs/stories/
   git commit -m "Phase 3: Architecture and story breakdown"
   git push

4. Schedule Phase 4 (dev) kickoff for Monday
```

### Phase 3 Deliverables

```
docs/
├── ARCHITECTURE.md          # System design
├── ADRs/
│   ├── 001-use-railway.md
│   ├── 002-mcp-integration.md
│   └── 003-database-schema.md
└── stories/                 # Detailed stories with acceptance criteria
    ├── sprint-1/
    ├── sprint-2/
    ├── sprint-3/
    └── sprint-4/
```

**Success Metrics:**
- ✅ Architecture approved
- ✅ 30+ detailed stories
- ✅ Sprint 1 ready to code

---

## Phase 4: Implementation (3–4 Weeks)

### Sprint 1: Chat UI (Week 1)

**Goal:** Chat display works with mock backend

**Stories:** 1.1–1.4 (4 stories, ~4 days)

**Your daily workflow:**
```
9:00 AM  - Review next story + clarify with Kilocode
9:30 AM  - Kilocode generates code
1:00 PM  - Code review + approve
2:00 PM  - Merge to main, Railway auto-deploys
3:00 PM  - Claude validates QA checklist
4:00 PM  - Unblock issues + prep next story
```

**Friday:** Demo working chat UI on staging

### Sprint 2: MCP Integration (Week 2)

**Goal:** Real MCP integration + API working

**Stories:** 2.1–2.4 (4 stories, ~4 days)

**Friday:** Demo full chat → MCP → response flow

### Sprint 3: Persistence (Week 3)

**Goal:** Database storage working

**Stories:** 3.1–3.4

**Friday:** Demo chat history, user profiles

### Sprint 4: Polish (Week 4)

**Goal:** Production-ready

**Stories:** 4.1–4.4 (error handling, monitoring, docs)

**Friday:** Ready for public launch

### Phase 4 Workflow

**Each story follows this pattern:**

```
1. Story assignment
   - Kilocode: "Implement story 1.1"
   - Kilocode: "Generate PR"

2. Code review (your 1 hour)
   - Review against acceptance criteria
   - Check for edge cases from story file
   - Approve or request changes

3. Merge & deploy (automatic)
   - Git push → Railway auto-deploys to staging
   - New URL: staging.ynab-chat.railway.app

4. QA validation
   - Claude: "Run QA checklist from story file"
   - Claude: "Test on staging: [list of steps]"
   - Claude: "All pass? Mark story done."

5. Move to next story
   - Kilocode: "Ready for story 1.2"
```

### Phase 4 Deliverables

```
Source code:
├── frontend/                # Next.js app
│   ├── app/chat/page.tsx
│   ├── components/
│   ├── hooks/
│   └── styles/
├── backend/                 # Node.js + Express
│   ├── src/api/
│   ├── src/mcp-client/
│   ├── src/database/
│   └── src/index.ts
└── database/                # PostgreSQL schema
    └── schema.sql

Deployment:
├── Dockerfile
├── docker-compose.yml
├── railway.json
└── .env.example

Documentation:
├── README.md                # Setup instructions
├── DEPLOYMENT.md            # Railway deployment
├── API.md                   # Backend API spec
└── DEVELOPMENT.md           # Dev environment setup
```

---

## Common Patterns

### Using BMAD Agents

You'll use Claude in 3 roles:

**BMAD Analyst** (Phase 2):
- Ask clarifying questions about requirements
- Validate assumptions
- Break PRD into stories

**BMAD Architect** (Phase 3):
- Design system architecture
- Write Architecture Decision Records (ADRs)
- Review technical decisions

**BMAD Scrum Master** (Phase 4):
- Assign stories to developers
- Validate acceptance criteria
- Run daily standups

**Developer (Kilocode)** (Phase 4):
- Implement stories
- Generate PRs
- Fix bugs

**QA (Claude)** (Phase 4):
- Run QA checklists
- Validate acceptance criteria
- Report bugs

### Story File Template

Every story gets a file with this structure:

```markdown
# Story 1.1: Chat Message Display

## Description
Users can see a list of chat messages in chronological order, with sender, timestamp, and message text.

## Acceptance Criteria
1. Messages display in a scrollable list
2. Each message shows: sender name, timestamp (HH:MM), text
3. Messages are ordered newest-first
4. Oldest message is at bottom
5. List scrolls to bottom when new message arrives
6. Works on desktop (Chrome, Safari, Firefox)

## Edge Cases
- Empty message list (show "No messages yet")
- Very long message (wrap text, don't break layout)
- Same sender multiple messages (group or separate?)
- Timestamps across multiple days (show date separator?)

## Dev Notes
- Use React hooks: useState, useEffect
- CSS Grid or Flexbox for layout
- Timestamp formatting: use `new Date().toLocaleTimeString()`
- No backend needed yet (mock data in component state)

## QA Notes
- Add 5 test messages manually
- Scroll to bottom, verify newest is visible
- Resize browser, verify text wraps
- Clear messages, verify "No messages yet" shows

## Blockers
- None (self-contained component)
```

---

## Metrics & Success

### Phase 1: Analysis
**Success = Confidence to proceed**
- ✅ Problem validated (users want it)
- ✅ Tech stack feasible (team knows it)
- ✅ Risks identified (know what to watch)

### Phase 2: Planning
**Success = Clear requirements**
- ✅ PRD approved (stakeholders agree)
- ✅ Stories written (developers understand)
- ✅ Scope bounded (MVP defined)

### Phase 3: Solutioning
**Success = Clear architecture**
- ✅ Architecture approved (team aligned)
- ✅ Risks addressed (ADRs written)
- ✅ Sprint 1 ready (first 4 stories detailed)

### Phase 4: Implementation
**Success = Working product**
- ✅ Sprint 1 done (chat UI works)
- ✅ Sprint 2 done (MCP integration works)
- ✅ Sprint 3 done (data persists)
- ✅ Sprint 4 done (production-ready)

---

## When Things Go Wrong

### "This story is too vague"
**Fix:** Ask Analyst to rewrite with example flows

### "We're behind schedule"
**Fix:** Reduce scope (move non-essential stories to Phase 2)

### "Kilocode generated code that doesn't match architecture"
**Fix:** Reference ADRs in story file, ask Kilocode to rewrite

### "User feedback contradicts PRD"
**Fix:** Update PRD with new learnings, adjust upcoming stories

---

## Next Steps

1. **Now:** Review Phase 1 findings
2. **Monday:** Start Phase 2 (Planning)
3. **Next week:** Phase 3 (Solutioning)
4. **Week 3-4:** Phase 4 (Implementation)

**You've got this. Let's build. 🚀**
