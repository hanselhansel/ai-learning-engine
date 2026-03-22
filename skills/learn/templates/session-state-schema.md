# SESSION-STATE.md v3 Schema

Defines all sections and fields for the v3 learning engine state file.

## Required Sections

### 1. Auto-Resume Protocol (header)
Instructions for Claude to read this file first. Reference CURRICULUM-CONFIG.md for paths.

### 2. Current Position
| Field | Type | Description |
|-------|------|-------------|
| Current Phase | string | e.g., "Phase 1: Foundations" |
| Current Week | string | e.g., "Week 1" |
| Current Day | integer | Curriculum day number |
| Sessions Completed | string | "X / ~Y" format |
| Last Session Date | date | YYYY-MM-DD |
| Last Session Mode | string | Micro/Quick/Standard/Deep/Synthesis |
| Next Session Plan | string | Description of next session content |
| Streak Count | integer | Consecutive days with sessions (resets after 3 days gap) |
| Milestones Shown | list | Which milestone messages have been displayed |

### 3. Assessment Scores
Phase gate results table. Updated only on gate days.

### 4. SWOT Evolution
SWOT snapshots per phase. Updated on growth reflection sessions.

### 5. Pending Questions
| Field | Type | Description |
|-------|------|-------------|
| # | integer | Sequential ID |
| Question | string | The question text |
| Raised On | string | Day/session when raised |
| Resolved? | string | Open/Discussed/Resolved |
| Answer | string | Resolution summary |

### 6. Terminology Mastery Tracker (SM-2)
Grouped by session/day of introduction.

| Field | Type | Description |
|-------|------|-------------|
| Term | string | The term name |
| Session Introduced | integer | When first taught |
| Correct Count | integer | Times answered correctly |
| Interval | integer | Sessions until next review |
| Next Review | integer | Session number for next quiz |
| Ease | float | SM-2 ease factor (1.3-3.0) |
| Confidence | string | Last calibration result |
| Status | string | Known/Learning/New |
| Notes | string | Corrections, common errors |

### 7. Confidence Calibration Summary
Per-session breakdown of calibrated/overconfident/underconfident counts.

### 8. Pre-Test Results
| Field | Type | Description |
|-------|------|-------------|
| Session | integer | Session number |
| Curriculum Day | integer | Day in curriculum |
| Questions | integer | Number of pre-test questions |
| Correct Before | integer | Right answers before lesson |
| Correct After | integer | Right answers after lesson |

**Archive rule:** Keep last 5 entries. Older → `sessions/archive/state-history.md`

### 9. Learning Velocity Dashboard
Per-session velocity metrics.

| Field | Type | Description |
|-------|------|-------------|
| Session | integer | Session number |
| Mode | string | Session mode used |
| Concepts Taught | integer | New concepts this session |
| Concepts Mastered | integer | Passed mastery gate |
| Velocity | float | mastered/expected ratio |
| Avg Ease Trend | float | Average ease across all terms |
| Calibration % | float | % calibrated responses |
| Pre-Test Delta | string | "+X" improvement |
| Est. Sessions Remaining | integer | Based on velocity |

### 10. Concept Links
Relationship graph between concepts.

| Field | Type | Description |
|-------|------|-------------|
| Concept A | string | Source concept |
| Relationship | string | enables/analogous/part-of/contrasts/builds-on/requires |
| Concept B | string | Target concept |
| Session Added | integer | When link was identified |

### 11. Spaced Exercise Queue
Portfolio exercises due for review.

| Field | Type | Description |
|-------|------|-------------|
| Exercise | string | Brief description |
| Session Created | integer | When originally done |
| Next Review | integer | Session to resurface |
| Interval | integer | Sessions between reviews |

### 12. Community Activity Summary
Per-community engagement tracking.

### 13. Build Project
Project status tracker.

### 14. Outreach Pipeline
Outreach metrics.

### 15. Session Log (Last 10)
| Field | Type | Description |
|-------|------|-------------|
| Date | date | Session date |
| Session | integer | Session number |
| Mode | string | Flex mode used |
| Curriculum Day | integer | Day in curriculum |
| Duration | string | Approximate time |
| Key Topics | string | Topics covered |
| Notes | string | Performance notes |

**Archive rule:** Keep last 10 entries. Older → `sessions/archive/state-history.md`

### 16. Day Mastery Status Table

Single source of truth for mastery-based progression.

| Column | Type | Description |
|--------|------|-------------|
| Day | integer | Curriculum day number |
| Phase | integer | Which phase this day belongs to (for threshold lookup) |
| Content Delivered | date | When lesson content was generated/delivered |
| SR Quiz Score | string | Score from SR Quiz (or "N/A" for first day, "—" if not yet quizzed) |
| Mastery Verified | YES/NO | Whether the learner demonstrated mastery in a live session |
| Weak Flag | YES/NO | If true, learner failed gate twice and was advanced via escape valve |
| Verified Date | date | When mastery was verified (or "—" if not yet) |

### Derived Fields (NOT stored — computed at read time)
- **Pending Verification**: Days where Content Delivered is set but Mastery Verified = NO
- **Current Verified Day**: Highest Day where Mastery Verified = YES

### 17. Flags for Next Session
Checklist of items to surface at next session open.

## Archive Rules

### When to Archive
- Session log exceeds 10 entries
- Pre-test results exceed 5 entries

### Archive Process
1. Read `sessions/archive/state-history.md` (create if not exists)
2. Append overflow entries with date header
3. Remove archived entries from SESSION-STATE.md
4. Keep newest entries in SESSION-STATE.md

### Archive Format
```markdown
## Archived [DATE]

### Session Log (archived from SESSION-STATE.md)
[table of archived entries]

### Pre-Test Results (archived from SESSION-STATE.md)
[table of archived entries]
```

## Warm-Start Migration Rules (v1 → v3)

### Preserve
- Current position (phase, week, day)
- All terminology entries with correct counts
- Pending questions
- Session log
- Flags
- Community activity, build project, outreach

### Calculate SM-2 from v1 correct counts
| v1 Correct Count | v3 Ease | v3 Interval | v3 Status |
|-------------------|---------|-------------|-----------|
| 0 | 2.5 | 0 (due now) | New |
| 1 | 2.5 | 1 | Learning |
| 2 | 2.6 | 3 | Learning |
| 3+ | 2.8 | 6 | Known |

### Initialize blank
- Confidence Calibration Summary
- Pre-Test Results
- Concept Links
- Spaced Exercise Queue
- Streak: 0
- Milestones Shown: []
- Last Session Mode: "Standard" (default)

### Calculate from history
- Learning Velocity Dashboard: reconstruct from session log entries
