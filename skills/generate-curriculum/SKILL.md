---
name: generate-curriculum
description: Generate a complete curriculum from scratch. Interactive skill that asks 5 questions about what you want to learn, then creates CURRICULUM.md, CURRICULUM-CONFIG.md, and SESSION-STATE.md ready for /learn. Use when starting a new learning journey. Triggers on "generate curriculum", "create curriculum", "new curriculum", "I want to learn", "set up a curriculum", or "/generate-curriculum".
---

# Curriculum Generator

Creates a complete, ready-to-learn curriculum in 5 questions. Generates all files needed for the Adaptive Learning Engine v3.

## Step 1: Gather Information (5 Questions)

Ask these questions ONE AT A TIME. Wait for each answer before asking the next.

### Q1: Topic
"What do you want to learn? Be as specific or broad as you like."
- Examples: "Machine learning for product managers", "Financial modeling", "Rust programming", "Product management for engineers"
- Follow up: "What's the end goal? (career switch, add a skill, personal interest, certification prep)"

### Q2: Timeline
"How many weeks do you have? And how many hours per day can you dedicate?"
- Map to session count: weeks x 5 sessions/week (weekdays)
- Suggest modes: "With 2 hours/day, Standard mode (60 min) works well with time for homework"

### Q3: Current Knowledge
"What do you already know that might connect to this topic? List your expertise areas."
- These become learner_bridges in the config
- Probe: "Any technical skills? Business experience? Domain knowledge?"
- Examples: "I know Python but not ML", "I have an MBA but no coding experience"

### Q4: Exercise Preferences
"How do you prefer to practice? Pick your top 3-4:"
- Writing (blog posts, memos, LinkedIn posts)
- Building (code, prototypes, tools)
- Analyzing (case studies, market analysis, data)
- Presenting (pitch decks, teaching scripts, talks)
- Discussing (debates, role-play, Socratic dialogue)
- Creating (diagrams, frameworks, templates)

### Q5: Communities & Resources
"Are there any communities, books, courses, or people you already follow in this space?"
- Use web search to find additional resources
- Suggest 5-8 relevant communities (Reddit, Discord, Slack, Twitter/X accounts)

## Step 2: Research (Web Search)

Use web search to gather:
- Current state of the field (latest developments, key players)
- Key terminology (30-60 terms organized by difficulty)
- Recommended resources (papers, books, podcasts, newsletters)
- Active communities
- Job market data (if career-oriented goal)

## Step 3: Generate CURRICULUM.md

Create a structured curriculum with 4 phases:

### Phase Structure
```
Phase 1: Foundations (25% of total time)
  - Core concepts, terminology, history
  - "What is this and why does it matter?"

Phase 2: Technical/Domain Depth (30% of total time)
  - Deeper understanding of key areas
  - "How does this actually work?"

Phase 3: Applied/Building (30% of total time)
  - Hands-on project work
  - "Can I actually do this?"

Phase 4: Portfolio/Networking (15% of total time)
  - Polish deliverables, prepare for interviews/opportunities
  - "Can I prove I know this?"
```

### Per-Day Format
Each day should include:
- **Core question**: The driving question for the day
- **Topics table**: Concept | What It Is | Why It Matters
- **Reading/resources**: 2-3 specific resources
- **Exercise**: A concrete, portfolio-worthy deliverable
- **Bridge**: Connection to the learner's existing expertise

### Assessment Gates
- Phase 1 Gate: terminology quiz + verbal explain
- Phase 2 Gate: deeper quiz + business/technical pitch
- Phase 3 Gate: project review + defense
- Phase 4 Gate: mock interview or portfolio review

Save to the curriculum directory as CURRICULUM.md.

## Step 4: Generate CURRICULUM-CONFIG.md

Fill the config template with the learner's answers:
- curriculum_name, paths, target_sessions
- learner_bridges (from Q3)
- exercise_types (from Q4, mapped to specific formats)
- mastery_thresholds (default: 70% Phase 1, 80% Phase 2+)
- flex_session_defaults (standard defaults)
- compression_settings (standard defaults)
- tone (inferred from conversation or ask)
- community_engagement_phases

Save as CURRICULUM-CONFIG.md.

## Step 5: Generate SESSION-STATE.md

Create a fresh v3 state file:
- All position fields initialized to Phase 1, Day 1
- Empty tracker tables
- Streak: 0
- No terms yet (populated during first session)

Save as SESSION-STATE.md.

## Step 6: Generate Supporting Files

Create:
- progress.md (empty template with header)
- COMMUNITIES.md (populated with researched communities from Q5 + web search)
- portfolio/ directory
- sessions/ directory
- sessions/summaries/ directory
- sessions/archive/ directory

## Step 7: Summary & Next Steps

Display to the learner:
```
CURRICULUM GENERATED

Topic: [topic]
Timeline: [X] weeks ([Y] sessions)
Phases: Foundations > Depth > Building > Portfolio

Files created:
  |- CURRICULUM.md          (master plan, [X] days)
  |- CURRICULUM-CONFIG.md   (your personalized settings)
  |- SESSION-STATE.md       (progress tracker, initialized)
  |- COMMUNITIES.md         (communities to join)
  +- progress.md            (daily log)

To start learning, type: /learn
```

## Key Rules

- **Web search is mandatory.** Every curriculum must include current, real data.
- **Be specific.** Don't generate vague topics like "Advanced concepts." Name specific papers, tools, companies.
- **Realistic scope.** A 4-week curriculum should have ~20 sessions, not 50. Adjust depth to fit timeline.
- **Portfolio-first.** Every phase should produce something the learner can show.
- **Bridge everything.** Every day's lesson should connect to the learner's existing expertise.
- **7-concept cap.** No day should introduce more than 7 new terms/concepts.
