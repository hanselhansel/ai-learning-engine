# Mastery Gates, Streaks & Milestones

## Pre-Session Mastery Gate

### Purpose
Verifies that the PREVIOUS day's content was actually learned before advancing to new content. This is separate from the end-of-session gate (which checks the CURRENT day's concepts).

### When Pre-Session Gate Triggers
- Standard, Deep, and Synthesis modes: Full gate (10 questions from SR Quiz)
- Quick mode: Abbreviated gate (5 questions)
- Micro mode: NEVER triggers (review-only, no advancement)

### Gate Check
1. Read Day Mastery Status table from SESSION-STATE.md
2. Derive Pending Verification: days where Content Delivered is set but Mastery Verified = NO
3. If no pending days → skip gate, load new content
4. If 1 pending day → quiz that day's terms from SM-2 tracker
5. If 2+ pending days → run Auto-Recovery flow (see below)

### Threshold Selection
Use the threshold for the PENDING DAY's phase, not the current phase. Example: if Day 5 (Phase 1, 70%) is pending but learner is now in Phase 2 (80%), quiz Day 5 at 70%.

Read threshold from CURRICULUM-CONFIG.md `Mastery Thresholds` table.

### Gate Outcomes (same escape valve as end-of-session gate)

**PASS (score ≥ phase threshold):**
- Mark day as Mastery Verified = YES in table
- Set Verified Date
- Log: "Pre-session gate: PASSED Day X [score]"

**FAIL (attempt 1):**
- Run 10-min remediation drill on failed terms
- Re-quiz those terms only
- If pass → mark verified

**FAIL twice (escape valve):**
- Mark Weak Flag = YES, Mastery Verified = YES
- Set SM-2 interval to 1 for failed terms
- Log: "Pre-session gate: ESCAPED Day X [score] — [terms] flagged weak"
- ADVANCE anyway — never block indefinitely

### Auto-Recovery (2+ pending days)
1. List all pending days with topics
2. Show: "You have N unverified days. Here's a catch-up plan."
3. Run combined SR Quiz (2 questions per pending day from SM-2 tracker)
4. Score EACH DAY INDIVIDUALLY (not aggregate):
   - Day passes if its questions score ≥ that day's phase threshold
   - Day fails if below threshold
5. For each passing day: mark Mastery Verified = YES
6. For each failing day:
   - Run remediation on that day's weak terms
   - Re-quiz that day only
   - If still fails: mark Weak Flag = YES, advance (escape valve)
7. After recovery: continue to new content

### No SM-2 Terms Fallback
If a pending day has no terms in the SM-2 tracker (e.g., async session didn't populate):
- Auto-mark as verified with note: "No terms to quiz — auto-verified"
- Log the gap for review

## Mastery Gate Logic

### When Gates Trigger
- End of every Standard and Deep session (Step 10S / after Step 14D)
- NOT triggered in Micro mode
- Quick mode: abbreviated end-of-session gate (verbal check on 3 concepts instead of all)

### Gate Check
Quick verbal check on each new concept taught this session:
1. Ask learner to explain concept in one sentence
2. Score: pass (>= threshold) or fail

### Threshold (from CURRICULUM-CONFIG.md)
Default: 70% of concepts must pass (e.g., 5/7 concepts)
Phase gates (end of phase): 80% on terminology quiz + 4/5 verbal explain

### Gate Outcomes

**PASS (>= threshold):**
- Advance to next session
- Log: "Mastery gate: PASSED [X/Y]"

**FAIL (< threshold), attempt 1:**
- Run 10-min targeted remediation on failed concepts ONLY
- Re-test failed concepts
- If pass on re-test → advance

**FAIL twice (escape valve):**
- ADVANCE anyway
- Flag failed concepts as "needs_extra_review" in tracker
- Set their SM-2 interval to 1 (review next session)
- Log: "Mastery gate: ESCAPED [X/Y] — [failed concepts] flagged"
- NEVER block progression indefinitely

## Streak Tracking (E8)

### Rules
- streak_count increments by 1 after each completed session (any mode counts)
- streak resets to 0 if >3 calendar days since last session
- Streak display at session open: "Session X | Y-day streak"

### Stale Session Detection
At session open:
- Calculate days_since_last = today - last_session_date
- If days_since_last > 3: reset streak to 0, display "Welcome back! Starting a fresh streak."
- If days_since_last > 7: also suggest starting with Quick mode to warm up

## Milestone Celebrations (E8)

| Milestone | Trigger | Message |
|-----------|---------|---------|
| First session | session_count == 1 | "First session complete! The hardest part is starting." |
| 5-day streak | streak == 5 | "5-day streak! You're building a habit." |
| 10-day streak | streak == 10 | "10 days straight. This is becoming part of who you are." |
| 25% complete | progress >= 25% | "Quarter of the way there. Look how far you've come." |
| 50% complete | progress >= 50% | "Halfway! You know more than most people in this space." |
| 75% complete | progress >= 75% | "Three quarters done. You're in the home stretch." |
| 100% complete | progress >= 100% | "Curriculum complete! Time to put this knowledge to work." |
| 10 terms Known | known_count >= 10 | "10 terms mastered. Your vocabulary is taking shape." |
| 25 terms Known | known_count >= 25 | "25 terms mastered. You can hold your own in conversations." |
| 50 terms Known | known_count >= 50 | "50 terms mastered. You speak the language fluently." |

Display milestone message at session open if triggered since last session.
Only show each milestone ONCE (track in SESSION-STATE.md milestones_shown list).

## Growth Reflection (B4)
- Triggers: every 10th Standard/Deep session, and every Synthesis session
- Flow: "Let's look at where you started. On Day 1, you [quote from session 1 log]. Now you [current capability]. What's changed in how you think about this space?"
- Update SWOT if applicable
