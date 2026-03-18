# Skill: Curriculum Session Exit

## Metadata
- **Name:** learn-end
- **Description:** End a curriculum session gracefully. Saves progress, prevents skipping material on partial sessions, commits to git.
- **Triggers:** "learn-end", "end lesson", "stop learning", "done learning", "save progress", "wrap up lesson", "pause lesson", "that's enough for today"

## Purpose

Use ONLY for mid-session exits (learner needs to leave before the lesson finishes naturally). If the full session protocol completed normally, the `/learn` skill handles closing automatically.

## Execution Protocol

### Step 1: Determine Completion Level

Check what session blocks were completed:

| Completion Level | Criteria | Day Advances? |
|-----------------|----------|---------------|
| **Full** | Quiz + Lesson + Drill + Reflect all done | YES |
| **Partial (lesson done)** | Quiz + Lesson done, drill/reflect skipped | NO |
| **Partial (quiz only)** | Only quiz completed | NO |
| **Partial (mid-lesson)** | Stopped during lesson | NO |

**Critical rule:** NEVER advance the day counter on partial sessions. This prevents skipping material.

### Step 2: Quick Reflect (2 min)

Ask two fast questions:
1. "What's the one thing that clicked today?"
2. "Anything confusing or unresolved?"

If the learner is in a rush, skip and use your own observations from the session.

### Step 3: Update SESSION-STATE.md

Update ALL fields:

- **Current Phase/Week/Day:** Only advance if FULL completion
- **Next Session Plan:**
  - Full: set to next day's topic
  - Partial: set to "Resume Day X from [block name]"
- **Days Completed:** Only increment if FULL
- **Last Session Date:** Today's date
- **Session Log:** Add entry with "FULL" or "PARTIAL ([block reached])" indicator
- **Terminology Mastery Tracker:** Update with any quiz results from this session
- **Community Activity Summary:** Log any community activity
- **Pending Questions:** Add new ones raised during session
- **Flags for Next Session:**
  - If partial: add flag with exact resume point (e.g., "Resume from Drill exercise")
  - Add any corrections or follow-ups noted during session
- **Build Project:** Update if any project work was done
- **Outreach Pipeline:** Update if any outreach was discussed

### Step 4: Update progress.md

Add entry:
- Date, phase/day, topics covered, key insight, questions
- Note: "PARTIAL - completed through [block name]" if not full

### Step 5: Save Deliverables

If any exercises, analyses, or written work was produced during the session:
- Exercise output: `build-project/` or inline in progress.md
- SWOT: `swot/phase-X-swot.md`
- Assessments: `assessments/phase-X-gate.md`
- Outreach drafts: `outreach/`
- Community notes: update COMMUNITIES.md

### Step 6: Session Summary

Give the learner a brief structured summary:

```
SESSION SUMMARY
- Day: [X] of [TOTAL] ([complete/partial])
- Topic: [today's topic]
- Key insight: [from reflection or observation]
- Pending: [unresolved items]
- Next session: [what happens when they type "let's learn" next]
- Overall progress: [X]% complete ([days done] / [total] days)
```

### Step 7: Git Commit & Push (if applicable)

```bash
git add [curriculum-folder]/
git commit -m "Curriculum progress: Phase X, Day Y [complete/partial] - [topic]"
git push
```

## Key Rules

1. **Be fast.** The learner wants to stop. Don't make closing take 10 minutes.
2. **Never advance on partial sessions.** This is the most important rule.
3. **Always set flags.** Next session must know exactly where to resume.
4. **Always save state.** SESSION-STATE.md gets updated even on 5-minute sessions.
5. **Always commit.** No progress should be lost.
