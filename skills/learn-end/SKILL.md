---
name: learn-end
description: End and save progress for the current curriculum session. Use when the learner says "learn-end", "/learn-end", "end lesson", "stop learning", "wrap up lesson", "done learning", "save progress", "pause lesson", "that's enough for today", or anything suggesting they want to stop and save progress. Handles all 5 flex modes (Micro/Quick/Standard/Deep/Synthesis) and preserves partial progress.
---

# End Learning Session (v3)

Gracefully close a session at any point. Captures progress, saves state, ensures seamless resume.

## Step 1: Load Config

Read `CURRICULUM-CONFIG.md` from the curriculum directory specified in CLAUDE.md.
Extract file paths: state_file, progress_file, summaries_dir, analytics_dashboard, concept_map.

## Step 2: Determine Session State

Review conversation history to determine:
- **Active mode**: Which flex mode was in progress? (Micro/Quick/Standard/Deep/Synthesis)
- **Last completed block**: Which was the last block fully completed?
- **Current block**: What was in progress when the learner stopped?

### Completion Check by Mode

Read `references/flex-session-blocks.md` (from the learn skill directory) for block composition.

**Micro** — complete if: SM-2 drill + interleaved Q + velocity check all done
**Quick** — complete if: SM-2 quiz + interleaved practice + velocity check all done
**Standard** — complete if: Pre-test + SM-2 + Socratic + interleaved + portfolio + reflect all done
**Deep** — complete if: All Standard blocks + teach-back + concept linking + community + extended practice all done
**Synthesis** — complete if: SM-2 expanded + integration challenge + teach-back + growth reflection all done

## Step 3: Quick Reflect (2 min max)

Ask two questions (keep it fast — the learner wants to stop):

1. **"What's the one thing that clicked today?"** — captures key insight
2. **"Anything confusing or unresolved?"** — captures pending questions

If learner says "just save" or seems rushed — skip this, use observations from the session.

## Step 4: Determine Day Advancement

**CRITICAL DECISION:**

- **Full session completed** (all required blocks for the active mode done):
  - Advance day counter
  - Set "Next Session Plan" to next day
  - Increment sessions_completed

- **Partial session** (stopped before all blocks done):
  - Do NOT advance
  - Set "Next Session Plan" to: "Resume Day X from [last incomplete block] ([Mode] mode)"
  - Add flag: "Partial [Mode] session — completed through [block]. Resume from [next block]."

- **Only opened session** (no blocks completed):
  - Do NOT advance
  - Add flag: "Session opened but no blocks completed. Resume Day X."

## Step 5: Update SESSION-STATE.md

Read current state_file, then update:

| Field | What to Update |
|-------|---------------|
| Current Phase/Week/Day | Only advance if full session completed |
| Sessions Completed | Only increment if full session completed |
| Last Session Date | Today's date |
| Last Session Mode | The mode that was active |
| Next Session Plan | Next day if complete, or resume instruction if partial |
| Streak Count | Increment if full session. Keep current if partial (still counts as activity). |
| Session Log | Add entry with: date, session#, mode, day, duration, topics, "FULL" or "PARTIAL ([last block])" |
| Terminology Tracker | Update with any SM-2 quiz results from this session |
| Confidence Calibration | Update if quiz was completed |
| Pre-Test Results | Update if pre-test was completed |
| Velocity Dashboard | Update if enough data from this session |
| Concept Links | Update if concept linking block was reached |
| Spaced Exercise Queue | Update if exercises were completed |
| Pending Questions | Add any unresolved questions raised |
| Flags for Next Session | Add resume point if partial + any follow-up items |

## Step 6: Generate Partial Summary Card

Read `templates/session-summary-card.md` (from the learn skill directory).
Generate a summary card even for partial sessions. Mark as "PARTIAL" in the card.
Save to `sessions/summaries/session-XX.md` (use sessions_completed + 1 if partial, since counter didn't advance).

For partial sessions, show:
- Blocks completed vs total for the mode
- Any quiz/pre-test scores captured
- Partial progress notation

## Step 7: Update Progress + Analytics

- Add entry to progress.md: "PARTIAL - completed through [block name]" if partial
- Update analytics dashboard if quiz data was collected
- Update concept map if concept linking was reached

## Step 8: Save Deliverables

If any written output was produced during the session (exercise, analysis, SWOT, etc.), ensure it's saved:

| Output Type | Save To |
|-------------|---------|
| Portfolio exercise | portfolio/ |
| SWOT assessment | swot/phase-X-swot.md |
| Assessment results | assessments/phase-X-gate.md |

## Step 9: Session Summary

Display brief summary to the learner:

```
SESSION SAVED
- Day: [X] of [TOTAL] ([complete/partial])
- Mode: [mode] ([blocks completed]/[total blocks])
- Topic: [today's topic]
- Key insight: [from Step 3 or session observation]
- Next: [what happens when they type /learn next]
- Progress: [X]% complete
```

## Step 10: Git Commit + Push

```
git add [curriculum_dir from config]
git commit -m "Curriculum progress: Day X [complete/partial] ([Mode]) - [topic]"
git push
```

## Key Rules

- **Be fast.** The learner wants to stop, not have a long conversation.
- **Never advance on partial.** This prevents gaps in learning.
- **Partial still counts for streak.** Opening a session and doing some work maintains the streak.
- **Always set resume flags.** The learn skill must know exactly where to pick up.
- **Always commit.** No progress should be lost.
- **Mode-aware.** A "partial" Micro (2/3 blocks done) is different from a "partial" Deep (5/14 blocks done). Be specific about what was completed.
