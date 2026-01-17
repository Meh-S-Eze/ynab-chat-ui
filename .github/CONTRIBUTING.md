# Contributing

This project uses BMAD (Build → Model → Architect → Deploy) methodology.

## Phases

1. **Phase 1:** Analysis (Validate problem)
2. **Phase 2:** Planning (Write PRD + stories)
3. **Phase 3:** Solutioning (Design architecture)
4. **Phase 4:** Implementation (Code in sprints)

## Working on Stories

Each story has an acceptance criteria checklist in `docs/stories/sprint-N/story-X.Y-*.md`.

**Before you code:**
1. Read the story file completely
2. Understand all acceptance criteria
3. Note edge cases

**When coding:**
1. Code to the story (not beyond scope)
2. Write tests for acceptance criteria
3. Test edge cases from the story file

**When submitting PR:**
1. Link to the story file
2. Reference acceptance criteria
3. Include QA checklist results

## Code Review

Reviews check:
1. ✅ All acceptance criteria met
2. ✅ No console errors
3. ✅ Tests passing
4. ✅ Works on mobile + desktop
5. ✅ No regressions

## Deployment

Code is deployed to staging automatically on merge to `main`.

Staging URL: `https://staging.ynab-chat.railway.app`

## Questions?

See `docs/BMAD-WORKFLOW.md` for full methodology.
