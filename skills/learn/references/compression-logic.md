# Content Compression & Velocity-Based Pacing

## Content Compression Rules (A2)

### Quiz Compression
IF term.ease > 2.5 AND term.correct_count >= 3 → Skip in quiz (already "Known")
Exception: randomly include 1 Known term per quiz as a check (prevents decay)

### Lesson Compression
IF pre_test_score >= 80% on a concept → Compress (summarize in 2-3 sentences, don't full Socratic)
IF pre_test_score >= 60% → Light Socratic (1 bridge question + reveal, skip follow-up)
IF pre_test_score < 60% → Full Socratic (bridge question + reveal + deeper follow-up)

### Session Compression
IF all pre_test scores >= 80% → Reduce lesson time by 30%, add extra practice
IF velocity > 1.5x average → Offer: "You're ahead of pace. Want to cover extra concepts or go deeper?"

## Velocity Calculation

### Per-Session Velocity
velocity = concepts_mastered_this_session / expected_concepts_for_mode

Expected by mode:
- Micro: 0 (review only)
- Quick: 0 (review only)
- Standard: 5-7
- Deep: 5-7 (same new concepts, more depth)
- Synthesis: 0 (integration, not new)

### Rolling Velocity (last 5 sessions with new concepts)
rolling_velocity = avg(last_5_session_velocities)

### Velocity-Based Pacing (A4)
IF rolling_velocity > 1.3 → "Fast learner" — offer to cover 1-2 extra concepts
IF rolling_velocity 0.7-1.3 → "On pace" — standard flow
IF rolling_velocity < 0.7 → "Needs support" — reduce to 4-5 concepts, add remediation
IF rolling_velocity < 0.5 → "Struggling" — reduce to 3-4 concepts, flag for review

## Difficulty Scaling (A3)
Based on pre-test score + velocity:
- High performer (pre-test >= 70%, velocity >= 1.0): harder interleaved questions, application-level
- Average (pre-test 40-69%, velocity 0.7-1.0): standard mix
- Needs support (pre-test < 40% OR velocity < 0.7): easier questions, more scaffolding

## Spaced Exercise Repetition (A5)
Exercises (not just terms) enter a spaced queue:
- After completing a portfolio exercise, add to queue with interval=5 sessions
- When due: include as 1 interleaved practice question
- If answered well: interval *= 1.5
- If struggled: interval = 2
