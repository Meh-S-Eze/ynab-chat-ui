# Story Breakdown by Sprint

**Timeline:** 4 weeks to MVP  
**Total Stories:** 16  
**Team:** Frontend, Backend, QA (parallel)

---

## Sprint 1: Chat UI (Week 1)

**Goal:** Chat interface works with mock backend

**Stories:** 4  
**Effort:** 4 days (one story per day)

| # | Story | Dev | QA | Status |
|---|-------|-----|----|---------|
| 1.1 | Chat Message Display | 1 day | ✓ | Ready |
| 1.2 | Chat Input & Send | 0.5 days | ✓ | Ready |
| 1.3 | Token Authentication | 1 day | ✓ | Ready |
| 1.4 | API Response Handling | 1.5 days | ✓ | Ready |

**Outcomes:**
- ✅ Chat UI displays messages
- ✅ Users can input messages and send
- ✅ Token authentication working
- ✅ Backend (mocked) responds to chat
- ✅ Deployed to staging

**Dependencies:**
- 1.3 (Token Auth) depends on 2.1 (MCP Client backend setup)
- 1.4 (API Response) depends on 2.2 (Express API endpoint)
- **Work in parallel:** Sprint 1 frontend + Sprint 2 backend

---

## Sprint 2: Backend & MCP Integration (Week 2)

**Goal:** Real MCP integration working, backend complete

**Stories:** 4  
**Effort:** 4 days (one story per day, parallel with Sprint 1)

| # | Story | Dev | QA | Status |
|---|-------|-----|----|---------|
| 2.1 | MCP Client Setup | 1 day | ✓ | Ready |
| 2.2 | Express API Endpoint | 1.5 days | ✓ | Ready |
| 2.3 | Token Validation & Security | 1 day | ✓ | Ready |
| 2.4 | Logging & Debugging | 0.5 days | ✓ | Ready |

**Outcomes:**
- ✅ Backend can call all 30+ MCP tools
- ✅ `/api/chat` endpoint working
- ✅ Token validation secure
- ✅ Logging working (no sensitive data)
- ✅ Chat + MCP integration complete
- ✅ Full end-to-end working

**Dependencies:**
- 2.2 (Express API) depends on 2.1 (MCP Client)
- 2.3 (Security) works with 2.1 and 2.2
- 2.4 (Logging) works with all backend stories

---

## Critical Path

```
Week 1 (Sprint 1):        Frontend UI
  1.1: Chat Display  ────▶ 1.2: Chat Input ────▶ 1.3: Token Auth
                                                      ↓
Week 2 (Sprint 2):        Backend + MCP           1.4: API Response
  2.1: MCP Client ──────▶ 2.2: Express API ─────▶ (connects to frontend)
    (parallel with Sprint 1)                       ↓
  2.3: Security ◀────────────────────────────────▶ 2.4: Logging
```

**Key insight:** Sprint 1 (frontend) and Sprint 2 (backend) work **in parallel**.
- Frontend can use mock backend during Sprint 1
- Backend connects to MCP during Sprint 2
- Both merge at Story 1.4 / 2.2 junction

---

## Next Steps

**Phase 2 Complete** ✅
- PRD done
- Stories written
- Breakdown by sprint

**Phase 3 Ready** 👈
- Design system architecture
- Write Architecture Decision Records (ADRs)
- Create deployment plan
- Final story refinement

**Ready to start coding on Monday! 🚀**
