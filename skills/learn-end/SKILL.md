---
name: learn-end
description: End and save progress for the current curriculum session. Use when the learner says "learn-end", "/learn-end", "end lesson", "stop learning", "wrap up lesson", "done learning", "save progress", "pause lesson", "that's enough for today", or anything suggesting they want to stop the current session. This handles all session bookkeeping so nothing is lost.
---

# End Curriculum Session

Gracefully close a learning session, capture everything learned, and save all progress so the next session picks up seamlessly.

The learner may end a session at any point: mid-lesson, after the quiz, after an exercise, or at the natural end. Handle all cases.

## Step 1: Load Config

Read `CURRICULUM-CONFIG.md` from the curriculum directory to get file paths and settings.

## Step 2: Session Checkpoint

Determine where the learner is in today's session by reviewing the conversation history:

| Completed Through | Classification |
|-------------------|---------------|
| All blocks (pre-test through mastery check) | **Full session** |
| Pre-test + quiz + lesson, but not practice/exercise | **Partial — lesson done** |
| Pre-test + quiz only | **Partial — quiz done** |
| Pre-test only or mid-lesson | **Partial — early exit** |
| SM-2 quiz partially completed | **Partial — mid-quiz** |

Tell the learner clearly what was completed and what wasn't.

## Step 3: Quick Reflect (2 min)

Ask the learner two questions (keep it fast — they want to stop):

1. **"What's the one thing that clicked today?"** (captures key insight for progress.md)
2. **"Anything confusing or unresolved?"** (captures pending questions for SESSION-STATE.md)

If they say "just save" or seem in a hurry, skip this and use what you observed during the session.

## Step 4: Determine Session Advancement

This is the most important decision:

- **Full session completed** (pre-test + quiz + lesson + practice + exercise + mastery check all done):
  Advance the session counter. Set "Next Session Plan" to the next session.

- **Partially completed** (stopped mid-lesson or skipped practice/exercise/mastery):
  Do NOT advance. Set "Next Session Plan" to resume the same session. Add flag: "Resume Session X from [block name]"

- **Only quiz done**: Do NOT advance. Flag: "Resume Session X from Lesson block."

- **Mastery gate not reached**: Flag: "Resume Session X — mastery check pending. Run remediation before advancing."

This prevents skipping material.

## Step 5: Update SESSION-STATE.md

Read SESSION-STATE.md, then update:

| Field | What to Update |
|-------|---------------|
| **Current Phase/Week** | Only advance if full session completed |
| **Sessions Completed** | Only increment if full session completed |
| **Current Curriculum Day** | Update based on session-to-day mapping |
| **Next Session Plan** | Next session if complete, or "Resume Session X from [block]" if partial |
| **Last Session Date** | Today's date |
| **Session Log (Last 5)** | Add entry: date, session#, duration estimate, topics covered, "FULL" or "PARTIAL" |
| **Terminology Mastery Tracker** | Update SM-2 fields ONLY for terms that were actually tested. Leave untested terms' next_review unchanged. |
| **Confidence Calibration Summary** | Update with this session's data (if quiz happened) |
| **Pre-Test Results** | Update with this session's pre-test scores (if pre-test happened) |
| **Learning Velocity Dashboard** | Update metrics for this session |
| **Community Activity** | Update if community check-in happened |
| **Pending Questions** | Add any unresolved questions raised |
| **Flags for Next Session** | Add resume point if partial; add follow-up items |
| **Build Project** | Update status if project work was done |
| **Outreach Pipeline** | Update counts if outreach happened |

**Critical SM-2 rule**: If the quiz was interrupted mid-way, only update intervals for terms that were actually answered. Do NOT reset or modify terms that weren't tested — their next_review dates remain unchanged.

## Step 6: Update progress.md

Add today's entry:
```
| [date] | Session X | Curriculum Day Y | [topics covered] | [key insight from Step 3] | [questions] |
```

If partial session, note it: "PARTIAL - completed through [block name]"

## Step 7: Save Any Deliverables

If the learner produced any output during the session, save to the correct location:

| Output Type | Save To |
|-------------|---------|
| Portfolio exercise output | `portfolio_dir` from config |
| SWOT assessment | `swot/phase-X-swot.md` |
| Assessment results | `assessments/phase-X-gate.md` |
| Outreach drafts | `outreach/` |
| Community notes | Update `communities_file` from config |

## Step 8: Session Summary

Give the learner a brief, structured summary:

```
SESSION SUMMARY
- Session: [X] of ~[total] ([complete/partial])
- Curriculum Day: [Y]
- Topic: [today's topic]
- Key insight: [from Step 3]
- Pending: [any unresolved items]
- Next session: [what happens next time they say /learn]
- Overall progress: [X]% complete
- SM-2 terms due next session: [count]
- Velocity: [concepts mastered this session] | [avg ease trend]
```

## Step 9: Git Commit & Push

```
git add [curriculum_dir from config]
git commit -m "Curriculum session: Session X [complete/partial] - [topic]"
git push
```

## Key Rules

- **Be fast.** The learner wants to stop, not have a long wrap-up conversation.
- **Never advance on a partial session.** This prevents gaps in learning.
- **Always set Flags for Next Session** so /learn knows exactly where to resume.
- **SM-2 integrity**: Only update intervals for actually-tested terms.
- **Always commit and push.** No progress should be lost.
- **Session numbers, not day numbers.** Use session numbering throughout.
