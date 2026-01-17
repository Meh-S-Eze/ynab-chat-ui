# BMAD Quick-Start: YNAB Chat UI

**Status:** Ready to begin Phase 2
**Today:** Saturday afternoon
**Start:** Monday 9 AM

---

## 📋 Pre-Launch Checklist (Do This Today)

- [ ] Read `docs/BMAD-WORKFLOW.md` (overview)
- [ ] Read `docs/PHASE-2-KICKOFF.md` (what to do Monday)
- [ ] ✅ Decide: Can you dedicate 1–2 hours daily for 4 weeks?
- [ ] ✅ Bookmark BMAD docs and GitHub repo
- [ ] ✅ Confirm GitHub repo is ready

---

## 🚀 Monday 9 AM: START HERE

### Phase 2: Planning & PRD Creation (1 Week)

**What:** Create a detailed PRD with 16+ user stories

**Why:** Clear requirements = faster coding, fewer reworks

**How:**

1. Open Claude / ChatGPT / your AI tool

2. Copy prompt from `docs/PHASE-2-KICKOFF.md` ("Monday Morning" section)

3. Spend 1–2 hours answering Claude's questions

4. Save responses to `docs/PRD-ANALYSIS.md`

**Expected outcome:** PRD draft + clarifying questions answered

---

## 📊 Timeline at a Glance

```
Week 1 (Mon–Fri):   Phase 2 (Planning)      → PRD complete
Week 2 (Mon–Fri):   Phase 3 (Architecture)  → System design complete
Week 3 (Mon–Fri):   Phase 4 Sprint 1        → Chat UI working
Week 4 (Mon–Fri):   Phase 4 Sprint 2        → MCP integration working
```

**Total:** 4 weeks to working MVP

---

## 📁 Repository Structure (After Phase 2)

```
ynab-chat-ui/
├── README.md                    # Project overview
├── docs/
│   ├── BMAD-WORKFLOW.md         # Full BMAD methodology
│   ├── PHASE-2-KICKOFF.md       # Week 1 instructions
│   ├── QUICK-START.md           # This file
│   ├── PRD.md                   # Product requirements document
│   ├── PRD-ANALYSIS.md          # Analysis notes
│   └── stories/                 # User stories by sprint
│       ├── sprint-1/
│       │   ├── story-1.1-chat-display.md
│       │   ├── story-1.2-chat-input.md
│       │   ├── story-1.3-mock-backend.md
│       │   └── story-1.4-responsive.md
│       ├── sprint-2/
│       ├── sprint-3/
│       └── sprint-4/
├── frontend/                    # Next.js app (Phase 4)
├── backend/                     # Node.js API (Phase 4)
└── database/                    # PostgreSQL schema (Phase 4)
```

---

## 🎯 Weekly Success Metrics

**Week 1 (Phase 2):**
- ✅ PRD written and approved
- ✅ 16+ stories broken down by sprint
- ✅ Everyone agrees on MVP scope

**Week 2 (Phase 3):**
- ✅ System architecture designed
- ✅ Architecture Decision Records (ADRs) written
- ✅ Sprint 1 ready to code

**Week 3 (Phase 4 Sprint 1):**
- ✅ Chat UI working with mock backend
- ✅ All 4 stories passing QA
- ✅ Deployed to staging

**Week 4 (Phase 4 Sprint 2):**
- ✅ Real MCP integration working
- ✅ User can chat about budget
- ✅ Error handling complete
- ✅ Ready for Phase 2 (add database)

---

## 💡 Key Principles

**1. One phase at a time**
- Don't start coding until Phase 3 (Architecture) is done
- Don't design architecture until Phase 2 (PRD) is done
- This prevents rework and wasted effort

**2. Stories are gospel**
- Developers code to stories (not to vague ideas)
- QA tests against acceptance criteria (in stories)
- Bugs are tracked against stories
- This keeps everyone aligned

**3. Stories drive everything**
- Architecture = service stories
- Code review = check story acceptance criteria
- Testing = follow story acceptance criteria
- Deployment = one story at a time

**4. Iterate, don't restart**
- Story unclear? Ask Claude to clarify it
- Don't rewrite whole PRD
- Make minimal edits, move forward

---

## ⚠️ Common Stumbles

### "I want to start coding now"
**Fix:** Phase 2 takes 1 week but saves 2 weeks later. Do it.

### "Story 1.2 is vague"
**Fix:** Ask Claude: "Rewrite Story 1.2 with an example user flow."

### "We're behind schedule"
**Fix:** Reduce scope. Move non-essential stories to Phase 2.

### "Architecture is unclear"
**Fix:** Ask Architect Agent to write Architecture Decision Records (ADRs).

### "Developer doesn't understand story"
**Fix:** Link to story file in PR, ask Claude to clarify specific part.

---

## 🛠️ Tools You'll Use

**Claude / ChatGPT / AI Chat Tool:**
- BMAD Analyst (Phase 2: clarify requirements)
- BMAD Architect (Phase 3: design system)
- Developer/Kilocode (Phase 4: write code)
- QA/Claude (Phase 4: test features)

**GitHub:**
- Store PRD, stories, documentation
- Track code changes
- Deploy to Railway

**Railway:**
- Hosting for Next.js frontend
- Hosting for Node.js backend
- PostgreSQL database (Phase 2+)

**Git:**
- `main` branch = working code
- `develop` branch = development
- PRs for code review

---

## 📞 Need Help?

**Story is unclear?**
→ Ask Claude (in story context): "Rewrite Story X as an example flow"

**Architecture question?**
→ Ask Claude (as Architect): "Why did we choose X instead of Y?"

**Bug with a story?**
→ Update story file, note lesson learned for Phase 2

**Want expert input?**
→ Join [BMAD Discord](https://discord.gg/gk8jAdXWmj)

---

## 🏁 You've Got This

- **Week 1:** Plan everything (1–2 hours/day)
- **Week 2:** Design architecture (1–2 hours/day)
- **Week 3:** Build chat UI (1–2 hours/day)
- **Week 4:** Integrate MCP (1–2 hours/day)

**By end of Week 4:** Production-ready chat app.

**Start Monday. 🚀**
