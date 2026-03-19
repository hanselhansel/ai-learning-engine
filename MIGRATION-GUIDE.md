# Migration Guide

## v1 → v3

v1 was a basic lecture-then-quiz engine with fixed ~130 min sessions. v3 adds flex sessions, SM-2 spaced repetition, content compression, teach-back, and 21 additional features.

### Breaking Changes

- SESSION-STATE.md format completely changed (new sections, SM-2 fields on terminology tracker)
- SKILL.md rewritten (hub-and-spoke architecture replaces monolithic)
- New file: CURRICULUM-CONFIG.md required (engine reads config at session start)

### Migration Steps

1. **Create CURRICULUM-CONFIG.md**
   Copy `CURRICULUM-CONFIG-TEMPLATE.md` and fill in your details.

2. **Migrate SESSION-STATE.md**
   Your existing terminology entries need SM-2 fields. Calculate from correct counts:

   | Existing Correct Count | New Ease | New Interval | New Status |
   |------------------------|----------|-------------|-----------|
   | 0 correct | 2.5 | 0 (due now) | New |
   | 1 correct | 2.5 | 1 | Learning |
   | 2 correct | 2.6 | 3 | Learning |
   | 3+ correct | 2.8 | 6 | Known |

   Add new sections (initialized blank):
   - Confidence Calibration Summary
   - Pre-Test Results
   - Learning Velocity Dashboard
   - Concept Links
   - Spaced Exercise Queue
   - Streak Count: 0
   - Milestones Shown: []
   - Last Session Mode: "Standard"

3. **Deploy new skill files**
   Replace your `.claude/skills/learn/SKILL.md` with the new hub-and-spoke version.
   Copy the `references/` and `templates/` directories alongside it.

4. **Update CLAUDE.md triggers**
   Update your learn trigger to reference CURRICULUM-CONFIG.md and the v3 session flow.

### What's Preserved

- Current position (phase, week, day)
- All terminology entries (with calculated SM-2 fields)
- Pending questions
- Session log
- Flags
- Community activity, build project, outreach

### What's New

- Flex sessions (choose your time at session start)
- SM-2 spaced repetition with ease factors
- Content compression (skip mastered material)
- Teach-back with peer simulation
- Concept linking + Mermaid maps
- Session summary cards + analytics dashboard
- Streak tracking + milestone celebrations
- Mid-session checkpoints (survive /compact)
- Auto-generated session files with web research

---

## v2 → v3

v2 added SM-2, Socratic method, and config-driven architecture but used fixed ~80 min sessions. v3 adds flex sessions as the organizing principle.

### Breaking Changes

- SKILL.md rewritten from monolithic to hub-and-spoke
- SESSION-STATE.md adds: Concept Links, Spaced Exercise Queue, Streak, Milestones, Last Session Mode
- New files: references/ directory (6 files), templates/ directory (3 files)

### Migration Steps

1. **Keep your CURRICULUM-CONFIG.md** — add new sections:
   - Flex Session Defaults
   - Compression Settings
   - Session Variety (C4)

2. **Update SESSION-STATE.md** — add new sections:
   - Concept Links (empty table)
   - Spaced Exercise Queue (empty table)
   - Streak Count: 0
   - Milestones Shown: []
   - Last Session Mode: "Standard"
   - Expand Session Log from "Last 5" to "Last 10"

3. **Deploy new skill files**
   Replace `.claude/skills/learn/SKILL.md` with hub-and-spoke version.
   Add `references/` and `templates/` directories.

4. **Existing SM-2 data preserved** — no recalculation needed.

### What's New in v3 (beyond v2)

- Flex sessions (5 modes replacing fixed 80-min)
- Content compression + difficulty scaling
- Teach-back with peer simulation
- Concept linking + Mermaid concept maps
- Session summary cards + analytics dashboard
- Streak tracking + milestones
- Mid-session checkpoints
- Auto-generated sessions with web research
- Curriculum generator skill
- Curriculum gallery (4 examples)
