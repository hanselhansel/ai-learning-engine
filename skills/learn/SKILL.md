---
name: learn
description: Resume and run the current curriculum session. Adaptive learning engine with SM-2 spaced repetition, Socratic method, pre-testing, confidence calibration, and mastery-based progression. Triggers on "let's learn", "learn", "next lesson", "continue learning", "resume lesson", "start lesson", "today's lesson", "spatial AI lesson", or anything suggesting the learner wants to continue their curriculum. Also triggers on "/learn".
---

# Adaptive Learning Engine

Evidence-based session runner. Reads a curriculum config, loads state, and guides the learner through an optimized session flow.

## Step 1: Load Curriculum Config (MANDATORY FIRST STEP)

Read `CURRICULUM-CONFIG.md` from the curriculum directory specified in CLAUDE.md.

Extract:
- **File paths**: curriculum_file, state_file, progress_file, portfolio_dir, communities_file, research_reference
- **Learner bridges**: existing knowledge to connect new concepts to
- **Exercise types**: portfolio artifact formats
- **Mastery thresholds**: per-phase pass/fail scores
- **Tone**: communication style

## Step 2: Load Session State

Read the `state_file` (SESSION-STATE.md). This is the **single source of truth**.

Extract:
- **Next Session Plan**: exactly what to teach today
- **Sessions Completed**: progress counter
- **Current Curriculum Day**: maps to CURRICULUM.md day numbering
- **Terminology Mastery Tracker**: SM-2 fields (interval, next_review, ease, confidence, status)
- **Pending Questions**: unresolved from previous sessions
- **Flags for Next Session**: items to surface at start
- **Learning Velocity Dashboard**: trend data
- **Community Activity**, **Build Project**, **Assessment Scores**

If "Sessions Completed" shows 0, this is the first session.

## Step 3: Load Today's Lesson

Read the `curriculum_file` (CURRICULUM.md). Find the section matching "Next Session Plan."

If the curriculum day has more than 7 new concepts, plan to cover only 7 this session. The remaining concepts carry to the next session (multi-session day).

## Step 4: Open Session

Greet the learner briefly:
- Session number and approximate total (e.g., "Session 5 of ~65")
- Today's topic title
- Any flags from last session (corrections, weak terms, pending deliverables)
- If pending questions exist, surface them

## Step 5: Pre-Test on NEW Material (5 min)

**Before teaching ANY new concept**, generate 3-5 questions about today's upcoming material from the curriculum.

These questions test concepts the learner has NOT been taught yet. The learner will get most wrong — **that's the point**. The pretesting effect (errors before learning create stronger memory traces than reading before learning).

For each question:
1. Pose the question, connecting to learner bridges where possible
2. Let the learner attempt an answer
3. Do NOT reveal the correct answer yet — say "We'll come back to this during the lesson"
4. Record: question, learner's attempt, correct answer

Use these pre-test results during the Socratic Lesson (Step 7) to highlight what the learner got right and wrong.

## Step 6: Spaced Repetition Quiz (10 min)

Use the SM-2 algorithm to select terms for review.

### Term Selection
1. From the Terminology Mastery Tracker, find all terms where `next_review <= today`
2. If more than 10 terms are due: prioritize by (a) most days overdue first, (b) then lowest ease factor
3. Cap at 10 terms per session. Overflow rolls to next session automatically.

### Quiz Flow (for each term)
1. Give the term
2. Learner explains it
3. **Before revealing if correct**: ask learner to rate confidence (1-5)
4. Score: correct or incorrect
5. Reveal correct answer, noting what was right/wrong

### SM-2 Update (for each term after scoring)
```
If correct:
  ease_factor = max(1.3, ease_factor + 0.1)
  interval = max(1, round(previous_interval * ease_factor))
  next_review = today + interval days

If wrong:
  ease_factor = max(1.3, ease_factor - 0.2)
  interval = 1
  next_review = tomorrow
```

### Confidence Calibration
- confidence >= 4 AND wrong → log "overconfident" (dangerous blind spot — flag for extra review)
- confidence <= 2 AND correct → log "underconfident" (learner knows more than they think)
- otherwise → log "calibrated"

### Phase Gate Days
If this is a **Phase Gate session** (end of a phase, per curriculum), run the full gate assessment instead of the regular quiz. See CURRICULUM.md for gate-specific instructions.

## Step 7: Socratic Lesson (25-30 min)

**CRITICAL RULE: NEVER explain a concept before the learner has attempted to reason about it.**

For EACH new concept (max 7 per session):

1. **Bridge question**: Pose a question connecting the concept to the learner's existing knowledge (from learner_bridges in config).
   - Example: "How would your 16 Claude agents 'see' a physical room? What information would they need?"

2. **Learner generates**: Let them attempt an answer. Don't interrupt.

3. **Reveal**: Explain the concept, highlighting:
   - What they got right
   - What they missed
   - Connect to their pre-test answer if they attempted this concept in Step 5

4. **Deeper follow-up**: Ask ONE follow-up question that goes one level deeper.

Use web search for the latest data, funding rounds, and product launches during the lesson.

## Step 8: Interleaved Practice (10 min)

Pose 3 problems that mix today's concepts with concepts from at least 2 previous sessions.

**Important**: Reference CURRICULUM.md for concept CONTENT (not just term definitions from the tracker). Terms are shallow; concepts have depth.

Example: "Company X uses [Session 3 concept: imitation learning] to train robots for [today's concept: warehouse manipulation]. What's the business case using [Session 2 concept: the convergence thesis]?"

This forces CONNECTION and TRANSFER, not just recall.

## Step 9: Portfolio Exercise (10-15 min)

Use `exercise_types` from the config to frame the drill as a REAL artifact.

NOT: "Write a 1-page comparison of VLA approaches"
YES: "Draft a LinkedIn post explaining why VLAs are the transformer moment for robotics"

Every output should be something the learner could actually use — for networking, job applications, portfolio, or content creation.

Save output to the `portfolio_dir` specified in config.

## Step 10: Community Check-in (5 min)

- Phase 1-2: "What did you notice lurking? Interesting threads? People? Topics?"
- Phase 3+: Review engagement plan. Posts? Replies? Connections?
- Log activity in the `communities_file` from config

## Step 11: Reflect + Mastery Check (5 min)

### a) Founder Summary
Ask the learner for an "explain it to a founder" summary (2-3 sentences they could use at a networking event). This is a generation exercise — they produce it from memory, not from notes.

### b) Mastery Gate
Score today's new concepts (quick verbal check on each):
- Use the threshold from config (`mastery_thresholds`)
- **Below threshold**: Run 10-min targeted remediation on weak concepts only. Then re-test.
- **Fail twice**: ADVANCE anyway. Flag weak concepts as "needs extra spaced repetition" in the tracker. Do NOT block progression indefinitely.
- **Above threshold**: Advance to next session.

### c) Flags
- Flag items for next session (corrections, weak terms, pending deliverables)
- Suggest 2-3 high-value follow-up questions aligned to learner profile

## Step 12: Weekly Synthesis Challenge (every 5th session)

On sessions 5, 10, 15, 20, 25... **replace** Interleaved Practice (Step 8) and Portfolio Exercise (Step 9) with a 20-minute Synthesis Challenge:

1. Pose a question requiring integration of ALL concepts from the current week
2. The question should require application and transfer, not just recall
3. Output = a real networking/portfolio artifact (saved to portfolio_dir)

Example: "A VC asks you: What's the single biggest technical risk in spatial AI and why should I invest anyway? Answer using concepts from all 5 sessions this week."

## Step 13: Update State + Commit (MANDATORY)

### Update SESSION-STATE.md:
- Advance session counter (only if mastery gate passed or escape valve triggered)
- Set "Current Curriculum Day" based on session-to-day mapping
- Set "Next Session Plan" to next session's content
- Update "Last Session Date"
- Add entry to "Session Log (Last 5)"
- Update Terminology Mastery Tracker with SM-2 fields for all quizzed terms
- Add new terms from today's lesson (set: interval=1, next_review=tomorrow, ease=2.5, status=New)
- Update Confidence Calibration Summary
- Update Pre-Test Results table
- Update Learning Velocity Dashboard
- Update Community Activity, Pending Questions, Flags

### Update progress.md:
Add today's entry with: date, session#, curriculum day, topics covered, key insight, pre-test score, questions.

### Phase Gate days also update:
- assessments/ folder with scored results
- swot/ folder (if applicable)
- Assessment Scores table in SESSION-STATE.md

### Git Commit & Push:
```
git add [curriculum_dir from config]
git commit -m "Curriculum session: Session X - [brief topic]"
git push
```

## Key Rules

- **Socratic first**: Never explain before the learner attempts. Ask, then reveal.
- **Concept cap**: Max 7 new concepts per session. Split multi-concept days across sessions. Depth over breadth.
- **Zero hallucination**: Say "unsure" if unsure. Use web search for current data.
- **Quantify everything**: Market sizes, funding, growth rates, multiples.
- **Portfolio output**: Every exercise produces a real, usable artifact.
- **SM-2 discipline**: Always update the tracker. Bounds: ease >= 1.3, interval >= 1.
- **Session numbering**: Use session numbers, not day numbers. Learner can do multiple sessions per sitting.
