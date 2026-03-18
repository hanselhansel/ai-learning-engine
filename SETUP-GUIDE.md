# Setup Guide

Step-by-step instructions to create your own AI-powered curriculum.

---

## Step 1: Fork or Clone This Repo

```bash
git clone https://github.com/[YOUR_USERNAME]/claude-curriculum.git my-learning-project
cd my-learning-project
```

Or click "Use this template" on GitHub.

## Step 2: Design Your Curriculum

Open `CURRICULUM-TEMPLATE.md` and fill it in:

1. **Define your goal.** What does "done" look like? Be specific: "Get hired as X", "Ship project Y", "Pass certification Z".
2. **Set the timeline.** How many weeks? How many hours per day? This determines your total day count.
3. **Define phases.** Recommended structure:
   - Phase 1: Foundations (build mental model)
   - Phase 2: Technical Literacy (go deeper)
   - Phase 3: Applied Knowledge (build something)
   - Phase 4: Portfolio + Networking (demonstrate and connect)
4. **Write day-by-day content.** For each day, include:
   - Core question (the one thing this day answers)
   - Topics table
   - Readings / resources
   - Exercise (hands-on, bridges to existing knowledge)
5. **Define phase gates.** What does the learner need to demonstrate before advancing?
6. **List terminology.** Group terms into Tier 1 (must-know) and Tier 2 (know by end of phase).

Save as `CURRICULUM.md` (replace the template).

## Step 3: Set Up Session State

Open `SESSION-STATE.md` and customize:
- Replace `[YOUR TOPIC]` with your topic
- Set `[TOTAL_DAYS]` to your curriculum's total day count
- Update the Phase names in Assessment Scores table
- Leave everything else as-is (Claude fills it in during sessions)

## Step 4: Set Up Communities (Optional)

Open `COMMUNITIES-TEMPLATE.md` and:
- Research 8-10 communities in your field (Discord, Reddit, X/Twitter, newsletters)
- Fill in the tables
- Save as `COMMUNITIES.md`

## Step 5: Install the Skills

### Option A: Claude Code / Cowork (Recommended)

Copy the skill folders into your Claude skills directory:

```bash
cp -r skills/learn ~/.claude/skills/curriculum-learn
cp -r skills/learn-end ~/.claude/skills/curriculum-learn-end
```

Or if using Cowork, copy to your `.skills/skills/` folder.

### Option B: CLAUDE.md Integration

If you prefer natural language triggers instead of slash commands:
1. Open `CLAUDE-SNIPPET.md`
2. Copy the content
3. Paste it into your project's `CLAUDE.md` file
4. Replace all `[BRACKETED]` values with your actual paths

## Step 6: Populate Research Reference (Optional)

Open `RESEARCH-REFERENCE.md` and:
- Run web searches for your topic's latest data
- Fill in companies, metrics, papers, events
- Include timestamps for all data points

Claude uses this file as source of truth during sessions. Keeps your lessons current.

## Step 7: Commit and Start Learning

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
+-- CURRICULUM.md              <- Your filled-in curriculum
+-- SESSION-STATE.md           <- Session state (auto-managed by Claude)
+-- COMMUNITIES.md             <- Your community tracker
+-- RESEARCH-REFERENCE.md      <- Verified data for your topic
+-- progress.md                <- Daily learning log (auto-updated)
+-- skills/
|   +-- learn/SKILL.md         <- Session runner skill
|   +-- learn-end/SKILL.md     <- Session exit skill
+-- sessions/                  <- Pre-read files (auto-generated)
+-- assessments/               <- Phase gate results
+-- swot/                      <- Self-assessments
+-- build-project/             <- Portfolio project files
+-- outreach/                  <- Networking tracker
```

## Tips

- **Don't over-plan.** Write Phase 1 in detail, outline Phase 2-4 at a higher level, and refine as you learn.
- **Use the bridge.** Every concept should connect to something you already know. Write these bridges into your curriculum.
- **Trust the state machine.** Don't manually edit SESSION-STATE.md unless something breaks. Let Claude manage it.
- **Review pre-reads.** Claude auto-generates next-day material. Skim it before your session for better retention.
- **Commit often.** Your learning history is a portfolio piece. Show consistent daily progress.
