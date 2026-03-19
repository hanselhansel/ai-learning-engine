# SM-2 Spaced Repetition Algorithm

## Term Selection
1. Find all terms where `next_review <= current_session`
2. If >10 due: prioritize by (a) most overdue first, (b) lowest ease factor
3. Cap at 10 per session (overflow rolls to next session)
4. Micro mode: cap at 3

## Quiz Flow (per term)
1. Present term
2. Learner explains
3. Ask confidence rating (1-5) BEFORE revealing answer
4. Score correct/incorrect
5. Reveal answer with what was right/wrong

## SM-2 Update Rules

### Correct Answer
```
ease = max(1.3, ease + 0.1)
interval = max(1, round(previous_interval * ease))
next_review = current_session + interval
correct_count += 1
```

### Incorrect Answer
```
ease = max(1.3, ease - 0.2)
interval = 1
next_review = current_session + 1
```

### New Term Initialization
```
ease = 2.5
interval = 0
next_review = current_session (due immediately)
correct_count = 0
confidence = -
status = New
```

## Confidence Calibration
- confidence >= 4 AND wrong → "overconfident" (blind spot — flag for extra review)
- confidence <= 2 AND correct → "underconfident" (knows more than they think)
- otherwise → "calibrated"

## Sanity Checks (run after every update)
- ease: MUST be 1.3 ≤ ease ≤ 3.0. If out of range → reset to 2.5
- interval: MUST be > 0. If zero/negative → reset to 1
- next_review: MUST be valid session number. If invalid → reset to current_session + 1
- correct_count: MUST be >= 0

## Worked Example
Term: "World Model", ease=2.5, interval=3, correct_count=2
- Learner answers correctly, confidence=4
- New ease: max(1.3, 2.5 + 0.1) = 2.6
- New interval: max(1, round(3 * 2.6)) = 8
- next_review: current_session + 8
- Status: if correct_count >= 3 AND ease > 2.3 → "Known", else "Learning"

## Status Definitions
- **Known**: correct_count >= 3 AND ease > 2.3
- **Learning**: 1+ correct OR ease <= 2.3
- **New**: never quizzed
