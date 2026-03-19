---
name: learn
description: Resume and run the current curriculum session. Adaptive learning engine with SM-2 spaced repetition, Socratic method, flex sessions (Micro/Quick/Standard/Deep/Synthesis), pre-testing, confidence calibration, teach-back, concept linking, and mastery-based progression. Triggers on "let's learn", "learn", "next lesson", "continue learning", "resume lesson", "start lesson", "today's lesson", or "/learn".
---

# Adaptive Learning Engine v3

Evidence-based session runner with flex sessions and hub-and-spoke architecture. Process only — all rules live in references/.

## Step 1: Load Config

Read `CURRICULUM-CONFIG.md` from the curriculum directory specified in CLAUDE.md.
Extract: file paths, learner bridges, exercise types, mastery thresholds, flex defaults, compression settings, tone.

## Step 2: Load & Validate State

Read the `state_file` (SESSION-STATE.md). This is the **single source of truth**.

**Validate:**
- Required sections exist (position, terminology tracker, session log, flags)
- SM-2 values in range: ease 1.3-3.0, interval >= 0. Read `references/sm2-algorithm.md` for sanity check rules.
- If corrupted: warn learner, offer reconstruction from progress.md + git history
- If position mismatch with CURRICULUM.md: warn learner, offer to recalibrate

**CHECKPOINT**: After validation, write a checkpoint note to progress.md ("Session started, state valid").

## Step 3: Load Curriculum

Read `curriculum_file` (CURRICULUM.md). Find the section matching "Next Session Plan."
If the day has >7 new concepts, plan to cover only 7 (multi-session day).

## Step 4: Open Session

Display session header:
```
Session [X] | [Y]-day streak | [Z]/[N] concepts mastered ([W]%)
```

**Streak check**: Read `references/mastery-gates.md` for streak rules.
- If >3 days since last session: reset streak, display "Welcome back! Starting a fresh streak."
- If >7 days: suggest starting with Quick mode to warm up.

**Milestone check**: Check milestones_shown list. Display any new milestone message.

**Concept of the Day (E4)**: Pick 1 random "Known" term from tracker. Ask: "Quick check -- what's [TERM]?" Accept brief answer, confirm, move on. (Skip if no Known terms yet.)

**Surface flags** from previous session.

**ASK**: "How much time do you have?" Map answer to mode:
- ~5 min: Micro
- ~15-20 min: Quick
- ~60 min: Standard (default)
- ~90+ min: Deep Dive
- Every 5th session: Synthesis (override other choices, but learner can defer)

Read `references/flex-session-blocks.md` for the block composition of the chosen mode.

## Step 5: Run Mode Blocks

### MICRO MODE (5 min)
1. **SM-2 Quick Drill** (3 min): Read `references/sm2-algorithm.md`. Quiz 3 due terms. Confidence rating per term.
2. **One interleaved question** (1 min): Mix concept from current + previous session.
3. **Velocity check + close** (1 min).
CHECKPOINT to progress.md

### QUICK MODE (15-20 min)
1. **SM-2 Quiz** (10 min): Read `references/sm2-algorithm.md`. Up to 10 terms. Confidence calibration. Difficulty scaling per `references/compression-logic.md`.
2. **Interleaved Practice** (5-8 min): 3 problems mixing current + previous concepts. Include 1 spaced exercise from queue.
3. **Velocity Check + Close** (2 min).
CHECKPOINT to progress.md after quiz

### STANDARD MODE (50-65 min)
1. **Pre-Test** (5 min): 3-5 questions on today's NEW concepts BEFORE teaching. Don't reveal answers. If learner gets one right, say "Interesting -- let's verify during the lesson."
CHECKPOINT
2. **SM-2 Quiz** (8-10 min): Read `references/sm2-algorithm.md`. Read `references/compression-logic.md` for content compression (skip Known terms, keep 1 random check).
CHECKPOINT
3. **Socratic Lesson** (20-25 min): Max 7 concepts (fewer if compression active). For EACH concept: bridge question, learner attempts, reveal + connect to pre-test answer. Mid-lesson retrieval checks every 2-3 concepts. **Escape hatch**: if learner says "I have no idea," give a hint first. If still stuck after hint, explain directly. Read `references/compression-logic.md` for difficulty scaling and velocity pacing.
CHECKPOINT
4. **Interleaved Practice** (8-10 min): 5 problems mixing concepts. Include 1 spaced exercise from queue. Reference CURRICULUM.md for concept CONTENT, not just term definitions.
5. **Portfolio Exercise** (8-12 min): Use exercise_types from config. Every 3rd Standard session: swap for teach-back (read `references/teach-back-protocol.md`).
6. **Reflect + Mastery Check** (5 min): Read `references/mastery-gates.md`. Ask founder summary. Run mastery gate. Every 10th session: growth reflection. Flag items for next session.
CHECKPOINT

### DEEP DIVE MODE (90-120+ min)
All Standard steps PLUS:
7. **Teach-Back with Peer Simulation** (15-20 min): Read `references/teach-back-protocol.md`. Claude plays skeptical colleague.
CHECKPOINT
8. **Concept Linking** (10-15 min): Read `references/concept-linking.md`. Surface 3-5 connections, update concept links table, generate/update Mermaid map.
9. **Community Check-in** (5-10 min): Phase-appropriate engagement.
10. **Extended Practice** (10-15 min): Session variety -- occasionally swap for debate/case study/reverse quiz per config.

### SYNTHESIS MODE (every 5th session, 60-75 min)
1. **SM-2 Quiz expanded** (15 min): All terms from the week.
2. **Integration Challenge** (30 min): Cross-topic exercise requiring all week's concepts.
3. **Teach-Back** (15 min): 2-min pitch of the week's big idea. Read `references/teach-back-protocol.md`.
4. **Growth Reflection** (10 min): Velocity comparison, SWOT update.

## Step 6: Close Session (ALL MODES)

### Update State
- Update SESSION-STATE.md with all session data (SM-2 updates, new terms, session log, flags)
- Read `templates/session-state-schema.md` for archive rules: trim session log to last 10, pre-tests to last 5
- Archive overflow to `sessions/archive/state-history.md`

### Generate Outputs
1. **Session Summary Card**: Read `templates/session-summary-card.md`. Generate and save to `sessions/summaries/session-XX.md`
2. **Analytics Dashboard**: Read `templates/analytics-dashboard.html`. Update with current data. Save to `portfolio/analytics-dashboard.html`
3. **Concept Map** (if Deep/Synthesis): Read `references/concept-linking.md`. Generate Mermaid map. Save to `portfolio/concept-map.md`

### Update Progress
- Update progress.md with session entry

### Auto-Generate Next Session
- Use web search to research latest news, papers, announcements relevant to next session's topic
- Generate next session file at `sessions/day-XX-session.md`
- If web search fails: generate from CURRICULUM.md only, note "Research pending"

### Git Commit + Push
```
git add [curriculum_dir]
git commit -m "Curriculum session: Session X ([Mode]) - [brief topic]"
git push
```

## Key Rules

- **Socratic first**: Never explain before the learner attempts. Ask, then reveal.
- **Escape hatch**: If learner says "I have no idea" -- give a hint, then explain if still stuck.
- **Pre-test correct**: If learner gets a pre-test question right, say "Interesting -- let's verify during the lesson" (don't skip the concept).
- **Concept cap**: Max 7 new concepts per session. Depth over breadth.
- **Zero hallucination**: Say "unsure" if unsure. Use web search for current data.
- **Quantify everything**: Market sizes, funding, growth rates, multiples.
- **Portfolio output**: Every exercise produces a real, usable artifact.
- **SM-2 discipline**: Always update the tracker. Read references/sm2-algorithm.md for bounds.
- **Checkpoints**: Write to progress.md after each major block. If /compact fires, re-read progress.md to resume.
- **On-demand loading**: Only read reference files when the relevant block is active. Micro/Quick modes never load teach-back or concept-linking.
