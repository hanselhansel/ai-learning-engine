# Adaptive Refinement

## How to Use This File
The engine reads this file during Step 6 (Close Session) to analyze session responses and determine if the learner's persona or difficulty level should be adjusted.

## Detection Signals

### Vocabulary Signal
| Indicator | Level Suggestion |
|-----------|-----------------|
| Simple language, avoids technical terms even when available | Elementary / Adult Beginner |
| Uses some jargon correctly, mixes with simpler terms | Teen / Adult Beginner |
| Consistent jargon usage, professional communication | Professional |
| Uses precise technical terms, references specific research/papers | Expert |

### Answer Depth Signal
| Indicator | Level Suggestion |
|-----------|-----------------|
| One-sentence answers, surface-level | Elementary / Beginner |
| 2-3 sentences, some reasoning | Teen / Adult Beginner |
| Multi-paragraph with nuance, considers trade-offs | Professional |
| Deep analysis, cites evidence, identifies edge cases | Expert |

### Confidence Calibration Signal
| Pattern | Interpretation |
|---------|---------------|
| Consistently overconfident (high confidence, wrong answers) | Material may be too advanced — or blind spots need addressing |
| Consistently underconfident (low confidence, correct answers) | Material may be too easy — or learner needs encouragement |
| Well-calibrated | Persona is well-matched |

### Pre-Test Performance Signal
| Score Range | Interpretation |
|-------------|---------------|
| >80% consistently | Material may be too easy. Consider persona upgrade or content compression. |
| 50-80% | Well-matched difficulty |
| <30% consistently | Material may be too hard. Consider persona downgrade or more scaffolding. |

### Engagement Signal
| Pattern | Interpretation |
|---------|---------------|
| Very quick answers (< 10 seconds) | Might be too easy, or not engaging deeply |
| Very long pauses, asks for help often | Might be too hard |
| Asks follow-up questions, explores tangents | Well-engaged, possibly ready for more depth |
| Short, disengaged answers | Possible fatigue, boredom, or overwhelm |

## Adjustment Rules

### Within-Session (Silent, Automatic)
These adjustments happen DURING the session without changing the config:

1. **If 2+ consecutive answers exceed persona level**: Increase question difficulty for remaining session. Use harder Socratic questions, reduce hints.
2. **If 2+ consecutive answers fall below persona level**: Decrease difficulty for remaining session. Add more scaffolding, give hints sooner.
3. **Log**: Record observations in SESSION-STATE.md under "Profile Refinement Log"

### Between-Session (Flagged, Requires Confirmation)
These adjustments are flagged at session close and surfaced at next session open:

1. **If 3+ sessions show consistent above-level performance**:
   - Flag: "Your responses suggest you might be ready for [HIGHER PERSONA]. Want to adjust?"
   - If confirmed: Update CURRICULUM-CONFIG.md persona field
   - If declined: Keep current persona, stop suggesting for 5 sessions

2. **If 3+ sessions show consistent below-level performance**:
   - Flag: "I notice you might benefit from more scaffolding. Want to adjust the teaching style?"
   - Frame positively — never say "downgrade." Say "adjust the teaching style to match your learning pace."
   - If confirmed: Update CURRICULUM-CONFIG.md persona field
   - If declined: Keep current persona, add extra scaffolding silently

3. **Objective Refinement**: If learner's answers consistently reflect a different goal than configured:
   - Flag: "Your questions lean toward [DIFFERENT OBJECTIVE]. Want to adjust your learning goal?"
   - If confirmed: Update CURRICULUM-CONFIG.md learning_objective

### Never Auto-Change Without Confirmation
- Persona changes always require learner confirmation via explicit question
- Within-session difficulty adjustments are silent and temporary
- Between-session flags are suggestions, not mandates

## Profile Refinement Log Format

Add to SESSION-STATE.md after each session:

```
### Profile Refinement Log

| Session | Signal | Observation | Action |
|---------|--------|-------------|--------|
| 5 | Vocabulary | Used "embodiment gap," "sim-to-real transfer" naturally | No change — matches Professional |
| 6 | Answer Depth | Multi-paragraph analysis with trade-offs | Confirm Professional fit |
| 7 | Pre-Test | 85% on pre-test (3 sessions above 80%) | FLAG: Consider content compression |
```

## Mid-Curriculum Objective Change
If the learner updates their objectives between sessions:
1. SKILL.md Step 4 (Open Session) detects config change by comparing current config to last session's logged objective
2. Acknowledge: "I see you've updated your learning goal. I'll adjust my questions and exercises accordingly."
3. Recalibrate perspective lenses for remaining sessions
4. Log the change in Profile Refinement Log

## Cross-Reference
- **learner-personas.md**: Defines the persona levels being detected/adjusted
- **compression-logic.md**: Pre-test performance affects content compression
- **objective-threading.md**: Objective changes affect threading
