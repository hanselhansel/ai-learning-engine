# Setup Guide

Step-by-step instructions to create your own AI-powered curriculum using the Adaptive Learning Engine v4.

---

## Step 1: Fork or Clone This Repo

```bash
git clone https://github.com/hanselhansel/ai-learning-engine.git my-learning-project
cd my-learning-project
```

Or click "Use this template" on GitHub.

## Step 2: Design Your Curriculum

Open `CURRICULUM-TEMPLATE.md` and fill it in:

1. **Define your goal.** What does "done" look like? Be specific: "Get hired as X", "Ship project Y", "Pass certification Z".
2. **Set the timeline.** How many weeks? How many hours per day? This determines your total session count.
3. **Define phases.** Recommended structure:
   - Phase 1: Foundations (build mental model)
   - Phase 2: Technical Literacy (go deeper)
   - Phase 3: Applied Knowledge (build something)
   - Phase 4: Portfolio + Networking (demonstrate and connect)
4. **Write day-by-day content.** For each day, include:
   - Core question (the one thing this day answers)
   - Topics table (max 7 concepts per day — the engine splits larger days across sessions)
   - Resources
   - Exercise (bridges to existing knowledge)
5. **Define phase gates.** What does the learner need to demonstrate before advancing?
6. **List terminology.** Group terms into Tier 1 (must-know) and Tier 2 (know by end of phase).

Save as `CURRICULUM.md`.

## Step 2.5: Set Your Learner Profile (NEW in v4)

If you're using `/generate-curriculum`, this is handled automatically during the 8-question setup. If you're configuring manually:

1. **Learner Profile**: In CURRICULUM-CONFIG.md, fill in the `Learner Profile` section:
   - `age_group`: Your age range (this affects analogies and vocabulary)
   - `experience_level`: How much you know about the topic
   - `persona`: Auto-assigned, or manually set to Elementary / Teen / Adult Beginner / Professional / Expert

2. **Learning Objective**: Fill in the `Learning Objective` section:
   - `primary_goal`: Why you're learning this (career, academic, investing, hobby, teaching, building)
   - `career_target`: Your specific end goal
   - `perspective_lenses`: The angles you want threaded through every lesson
   - `objective_statement`: One sentence summarizing your why

3. **Placement Test** (optional): Run `/generate-curriculum` even for an existing curriculum — it will detect the existing files and offer to run just the placement test to auto-assign your persona.

The engine adapts its teaching style (vocabulary, analogies, question difficulty, feedback tone) based on your persona, and threads your learning goal through every question and exercise.

## Step 3: Configure the Engine

Open `CURRICULUM-CONFIG-TEMPLATE.md` and customize:

1. **Curriculum Identity**: Set file paths to match your folder structure
2. **Learner Bridges**: List your existing expertise that connects to new material
3. **Exercise Types**: Define the portfolio artifact formats for your field
4. **Mastery Thresholds**: Set per-phase pass/fail scores
5. **Tone & Style**: How you want the AI to communicate

Save as `CURRICULUM-CONFIG.md`.

## Step 4: Set Up Session State

Open `SESSION-STATE.md` and customize:
- Replace `[YOUR TOPIC]` with your topic
- Set `[TARGET_SESSIONS]` (estimate: ~1.3x your curriculum day count, since multi-concept days split)
- Update Phase names in Assessment Scores table
- Leave the SM-2 tracker empty — the engine fills it during sessions

## Step 5: Set Up Communities (Optional)

Open `COMMUNITIES-TEMPLATE.md` and:
- Research 8-10 communities in your field (Discord, Reddit, X/Twitter, newsletters)
- Fill in the tables
- Save as `COMMUNITIES.md`

## Step 6: Install the Skills

### Option A: Claude Code / Cowork (Recommended)

Copy the skill folders into your Claude skills directory:

```bash
cp -r skills/learn ~/.claude/skills/learn
cp -r skills/learn-end ~/.claude/skills/learn-end
```

### Option B: CLAUDE.md Integration

If you prefer natural language triggers:
1. Open `CLAUDE-SNIPPET.md`
2. Copy the content
3. Paste into your project's `CLAUDE.md` file
4. Replace all `[BRACKETED]` values with your paths

## Step 7: Populate Research Reference (Optional)

Open `RESEARCH-REFERENCE.md` and:
- Run web searches for your topic's latest data
- Fill in companies, metrics, papers, events
- Include timestamps for all data points

The engine uses this file as source of truth during sessions.

## Step 8: Commit and Start Learning

```bash
git add .
git commit -m "Initialize curriculum: [your topic]"
git push
```

Then open Claude and type: **"let's learn"**

---

## Folder Structure After Setup

```
your-curriculum/
├── CURRICULUM.md              <- Your filled-in curriculum
├── CURRICULUM-CONFIG.md       <- Engine configuration + learner profile + objectives
├── SESSION-STATE.md           <- Session state (auto-managed)
├── COMMUNITIES.md             <- Your community tracker
├── RESEARCH-REFERENCE.md      <- Verified data for your topic
├── progress.md                <- Session log (auto-updated)
├── skills/
│   ├── learn/SKILL.md         <- Adaptive learning engine
│   └── learn-end/SKILL.md    <- Session exit handler
├── portfolio/                 <- Portfolio artifacts + analytics dashboard + showcase
├── sessions/
│   ├── summaries/             <- Per-session receipt cards
│   ├── digests/               <- Weekly learning digests
│   └── archive/               <- Archived state history
├── assessments/               <- Phase gate results
├── swot/                      <- Self-assessments
├── build-project/             <- Portfolio project files
└── outreach/                  <- Networking tracker
```

## Tips

- **Don't over-plan.** Write Phase 1 in detail, outline Phase 2-4 at a higher level, refine as you learn.
- **Use the bridges.** Every concept should connect to something you already know. Write these into CURRICULUM-CONFIG.md.
- **Trust the state machine.** Don't manually edit SESSION-STATE.md unless something breaks.
- **Commit often.** Your learning history is a portfolio piece.
- **Do multiple sessions.** Sessions are decoupled from calendar days. Go as fast as you want.
