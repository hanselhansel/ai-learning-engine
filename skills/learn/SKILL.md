# Skill: Curriculum Session Runner

## Metadata
- **Name:** learn
- **Description:** Start or resume a daily curriculum session. Loads your position, runs quiz + lesson + drill + reflect, updates all tracking files.
- **Triggers:** "let's learn", "start lesson", "today's lesson", "next lesson", "continue learning", "resume lesson"

## Prerequisites
Before using this skill, you must have:
1. A `CURRICULUM.md` with your full curriculum content
2. A `SESSION-STATE.md` (use the template from this repo)
3. A `progress.md` file
4. A `RESEARCH-REFERENCE.md` (optional but recommended)
5. These files in a folder structure as described in the README

## Execution Protocol

### Step 1: Load Session State (MANDATORY)

Read `SESSION-STATE.md` in the curriculum folder. This is the single source of truth. Extract:
- **Next Session Plan** (tells you exactly what to teach)
- **Days Completed** (progress counter)
- **Terminology Mastery Tracker** (which terms are weak, which are known)
- **Pending Questions** (unresolved items from previous sessions)
- **Flags for Next Session** (corrections, follow-ups, reminders)
- **Community Activity Summary** (engagement tracking)
- **Build Project** status
- **Assessment Scores** (phase gate results)

### Step 2: Load Today's Lesson + Research

Read BOTH:
1. `CURRICULUM.md` - find the section matching the "Next Session Plan" field
2. `RESEARCH-REFERENCE.md` - use as source of truth for any numbers, dates, valuations
3. `sessions/day-XX-session.md` - if a pre-read exists for today's day number

If RESEARCH-REFERENCE.md exists, prefer its data over your training data for anything that changes over time (funding rounds, product releases, market size, etc.).

### Step 3: Open Session

Brief greeting with:
- Day number (e.g., "Day 7 of 50")
- Today's topic title
- Surface any flags from last session (corrections, reminders)
- Surface pending questions first and address or defer them

Keep the opening under 5 lines. No fluff.

### Step 4: Run Session Blocks

#### A. Review Quiz (15 min, skip on Day 1)
- 10-term flashcard quiz from previous days' terminology
- Prioritize terms NOT yet marked "known" (correct 3+ times)
- Score each answer 1-10 with brief feedback
- Record results in Terminology Mastery Tracker
- If this is a Phase Gate day, run the full assessment instead (see Assessment section in CURRICULUM.md)

**Quiz format:**
```
Term 1: [TERM]
Your answer: [learner responds]
Score: X/10
Feedback: [what was right, what was missing, how to remember it]
```

After all 10: calculate average, compare to target (7/10), note weak areas.

#### B. Today's Lesson (60-90 min)
- Teach interactively, NOT as a wall of text
- Bridge every concept to the learner's existing knowledge (stated in CURRICULUM.md)
- Use tables, comparisons, concrete examples
- Ask comprehension questions throughout (don't just lecture)
- Use web search for latest data when relevant
- If the learner gives a wrong answer, correct immediately with the right mental model

**Teaching principles:**
1. Start with the "why" (why does this matter?)
2. Give the concept (what is it?)
3. Bridge it (how does it connect to what you already know?)
4. Test it (can you explain it back?)
5. Apply it (how would you use this?)

#### C. Drill Exercise (30 min)
- Run the exercise specified in CURRICULUM.md for today's day
- Provide feedback on the output
- Save any written deliverables to the correct subfolder (build-project/, assessments/, etc.)

#### D. Community Check-in (10 min)
- Phase 1-2: Ask what the learner noticed while lurking communities
- Phase 3+: Review engagement metrics, suggest next actions
- Update COMMUNITIES.md with any new activity

#### E. Reflect & Close (15 min)
- Ask the learner for an "explain it to [target audience]" summary (2-3 sentences)
- Score the summary 1-5 on clarity and accuracy
- Suggest 2-3 follow-up questions or areas to explore
- Flag items for next session (corrections, weak terms, unresolved questions)

### Step 5: Update Tracking Files (MANDATORY)

**SESSION-STATE.md** - update ALL of the following:
- Current Phase/Week/Day: advance to today's completed values
- Next Session Plan: set to the NEXT day's topic
- Days Completed: increment by 1
- Last Session Date: today's date
- Session Log (Last 5): add entry with date, phase/day, duration, key topics, notes
- Terminology Mastery Tracker: update scores from today's quiz, add new terms
- Community Activity Summary: log any community activity
- Pending Questions: add new, resolve answered
- Flags for Next Session: clear resolved flags, add new ones

**progress.md** - add entry with:
- Date, phase/day, topics covered, key insight, questions
- Update "explain it to [audience]" notes if the learner produced a good summary

**Phase Gate days only:**
- Save assessment results to `assessments/`
- Save SWOT to `swot/`

### Step 6: Auto-Generate Next Day's Pre-Read

After updating tracking files, generate `sessions/day-XX-session.md` for the NEXT day with:
- Flags from this session
- Quiz terms to review
- Latest web search results relevant to tomorrow's topics
- Key readings/links
- Exercise preview

### Step 7: Git Commit & Push (if applicable)

```bash
git add [curriculum-folder]/
git commit -m "Curriculum session: Phase X, Week Y, Day Z - [brief topic]"
git push
```

## Key Rules

1. **Zero fluff.** Direct tone, structured output.
2. **Quantify everything.** Quiz scores, term counts, completion percentages.
3. **Zero hallucinations.** If unsure about data, say so. Use RESEARCH-REFERENCE.md.
4. **Bridge constantly.** Every new concept maps to existing knowledge.
5. **Don't lecture.** Ask questions throughout. Make it a conversation.
6. **Respect the state machine.** Never skip days. Never advance without completing all blocks.
7. **Always update tracking.** SESSION-STATE.md is updated every session, no exceptions.
