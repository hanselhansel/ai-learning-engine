# Mastery Gates, Streaks & Milestones

## Mastery Gate Logic

### When Gates Trigger
- End of every Standard and Deep session (Step 10S / after Step 14D)
- NOT triggered in Micro, Quick, or Synthesis modes

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
