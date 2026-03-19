# ai-learning-engine

An open-source, AI-powered adaptive learning system. Design a curriculum on any topic, then learn it interactively with an AI tutor that uses **evidence-based learning science** to maximize retention and understanding.

Works with **Claude Code**, **OpenAI Codex**, **Cursor AI**, or any AI assistant that reads markdown files.

---

## v2: Evidence-Based Methodology

This engine is built on research from 40+ academic sources in cognitive science and learning theory. Key upgrades from v1:

| Feature | v1 (Old) | v2 (Current) | Research Basis |
|---------|----------|-------------|----------------|
| **Pre-session** | Pre-read (passive) | Pre-test (active errors) | Pretesting effect — errors before learning create stronger memory traces |
| **Teaching** | Explain-then-ask | Socratic (ask-then-reveal) | Generation effect — producing answers before seeing them improves retention 30-50% |
| **Review** | Simple flashcards (3+ correct = known) | SM-2 spaced repetition with confidence calibration | SM-2 algorithm — adaptive intervals based on ease factor and performance |
| **Practice** | Single-topic drills | Interleaved practice (mix topics) | Interleaving — mixing related concepts improves transfer and discrimination |
| **Exercises** | Generic assignments | Portfolio-grade artifacts | Real-world application — contextual learning outperforms abstract exercises |
| **Advancement** | Fixed daily progression | Mastery-based with escape valve | Mastery learning — progress when you understand, not when the calendar says so |
| **Concepts** | Unlimited per session | 7-concept cap, multi-session days | Cognitive load theory — fewer concepts with more depth beats more concepts with less |
| **Metacognition** | Not tracked | Confidence calibration (1-5 per answer) | Calibration training — knowing what you don't know is as valuable as knowing |
| **Session length** | 3-4 hours | 65-75 minutes | Attention research — shorter, focused sessions outperform long ones |

---

## The Problem

Self-directed learning falls apart because:
- You skip the hard parts and only study what's comfortable
- You forget 80% of what you read within a week
- You have no way to measure if you actually understand something
- You study alone with no feedback loop
- You never build the muscle of explaining what you learned

## The Solution

This repo gives you a **state machine for learning**. You design a curriculum (or use an example), and your AI tutor:

1. **Pre-tests** you on material you haven't learned yet. Getting wrong answers primes your brain for deeper learning.
2. **Quizzes you** using SM-2 spaced repetition. Weak terms surface more often with algorithmically optimal intervals.
3. **Teaches Socratically** — asks you to reason about concepts before revealing answers. You learn by generating, not reading.
4. **Mixes concepts** across sessions. Today's practice includes problems from last week, forcing transfer and connection.
5. **Produces portfolio artifacts** — every exercise creates something real (LinkedIn posts, pitch slides, analysis memos).
6. **Gates progression** on mastery, not time. Below threshold? Targeted remediation. Fail twice? Advance with a flag (never blocks indefinitely).
7. **Tracks everything** in plain markdown. Your git history becomes a portfolio of consistent learning.

---

## Quick Start

```bash
git clone https://github.com/hanselhansel/ai-learning-engine.git my-learning-project
cd my-learning-project
```

1. Copy `CURRICULUM-TEMPLATE.md` → `CURRICULUM.md` and fill in your topic
2. Copy `CURRICULUM-CONFIG-TEMPLATE.md` → `CURRICULUM-CONFIG.md` and customize
3. Update `SESSION-STATE.md` with your topic name and target sessions
4. Install the skills for your platform (see [Platform Setup](#platform-setup))
5. Type **"let's learn"** in your AI assistant

See `SETUP-GUIDE.md` for the full walkthrough.

---

## How a Session Works (~65-75 min)

```
You: "let's learn"

AI: [reads CURRICULUM-CONFIG.md → SESSION-STATE.md → CURRICULUM.md]

=== Session 7 of ~65: How Robots See (Perception) ===

Flags from last session:
- You mixed up "perception" and "planning" again. Perception = sensing ONLY.

--- PRE-TEST (5 min) ---
Before we start today's lesson, let me see what you already know...
Q1: What does a LiDAR sensor measure?
You: [attempt — probably wrong, and that's good]
"We'll come back to this during the lesson."

--- SPACED REPETITION QUIZ (10 min, SM-2) ---
Term 1: What is a VLA?
You: [answer]
Confidence (1-5): 4
Result: Correct. Ease: 2.7 → 2.8. Next review: 8 days.

--- SOCRATIC LESSON (25-30 min, max 7 concepts) ---
"How would your 16 Claude agents 'see' a physical room?"
You: [reason about it]
"Good — you got the sensor fusion part right. What you missed is..."
[Connects to your pre-test answer]

--- INTERLEAVED PRACTICE (10 min) ---
Problem mixing today's Perception with last week's VLA architecture...

--- PORTFOLIO EXERCISE (10-15 min) ---
"Draft a LinkedIn post explaining why LiDAR + cameras > cameras alone"
[Saved to portfolio/]

--- MASTERY CHECK ---
Score: 7.5/10. Above threshold. Advancing to Session 8.

--- SESSION COMPLETE ---
[Updates SM-2 tracker, velocity dashboard, commits to git]
```

---

## The Methodology

### Session Flow

| Block | Duration | What |
|-------|----------|------|
| **Pre-Test** | 5 min | 3-5 questions on NEW material. Errors prime the brain. |
| **SR Quiz** | 10 min | SM-2 selects terms for review. Confidence calibration. |
| **Socratic Lesson** | 25-30 min | Ask-then-reveal. Max 7 concepts. Bridge to existing knowledge. |
| **Interleaved Practice** | 10 min | 3 problems mixing today's + previous sessions' concepts. |
| **Portfolio Exercise** | 10-15 min | Real artifact (LinkedIn post, pitch slides, memo). |
| **Community** | 5 min | Lurk → Engage → Contribute progression. |
| **Mastery Check** | 5 min | Gate with escape valve. Never blocks indefinitely. |

### SM-2 Spaced Repetition

Every term is tracked with the SM-2 algorithm:

| Term | Correct | Interval | Next Review | Ease | Confidence | Status |
|------|---------|----------|-------------|------|------------|--------|
| World Model | 3 | 8 days | 2026-04-01 | 2.8 | Calibrated | Known |
| DoF | 1 | 1 day | 2026-03-25 | 2.3 | Overconfident | Learning |
| NeRF | 0 | 1 day | 2026-03-24 | 2.5 | - | New |

- **Correct**: ease goes up, interval grows → reviewed less often
- **Wrong**: ease goes down, interval resets to 1 → reviewed tomorrow
- **Confidence calibration**: flags blind spots (high confidence + wrong answer)

### Phase Gates

| Gate | Format | Threshold |
|------|--------|-----------|
| Phase 1 | Term quiz + verbal explanation | Per config (default 6/10) |
| Phase 2 | Term quiz + pitch a concept | Per config (default 7/10) |
| Phase 3 | Portfolio project defense | Project complete |
| Phase 4 | Mock interview | Pass 2/3 rounds |

### Weekly Synthesis (every 5th session)

Replaces practice + exercise with a 20-min cross-topic challenge that integrates the full week's concepts into a single portfolio artifact.

---

## Repo Structure

```
ai-learning-engine/
├── README.md                          <- You're here
├── SETUP-GUIDE.md                     <- Step-by-step setup
├── CURRICULUM-TEMPLATE.md             <- Template: design your curriculum
├── CURRICULUM-CONFIG-TEMPLATE.md      <- Template: engine configuration (NEW in v2)
├── SESSION-STATE.md                   <- Template: session state machine (SM-2)
├── progress.md                        <- Template: session log
├── COMMUNITIES-TEMPLATE.md            <- Template: community tracker
├── RESEARCH-REFERENCE.md              <- Template: verified data/sources
├── CLAUDE-SNIPPET.md                  <- CLAUDE.md / AGENTS.md snippet
├── LICENSE                            <- MIT License
├── skills/
│   ├── learn/SKILL.md                 <- Adaptive learning engine (v2)
│   └── learn-end/SKILL.md            <- Session exit handler (v2)
├── platforms/
│   ├── claude-code/README.md          <- Claude Code / Cowork setup
│   ├── openai-codex/README.md         <- OpenAI Codex setup
│   └── cursor-ai/README.md           <- Cursor AI setup
├── examples/
│   └── spatial-ai/                    <- Example: Spatial AI curriculum
├── portfolio/                         <- Portfolio artifacts (NEW in v2)
├── sessions/                          <- Session archives
├── assessments/                       <- Phase gate results
├── swot/                              <- Self-assessments
├── build-project/                     <- Portfolio project files
└── outreach/                          <- Networking tracker
```

---

## Platform Setup

| Platform | Skill Format | Auto-Trigger | Setup Guide |
|----------|-------------|-------------|-------------|
| **Claude Code / Cowork** | SKILL.md in `.claude/skills/` | Yes ("let's learn") | [platforms/claude-code/](platforms/claude-code/) |
| **OpenAI Codex** | SKILL.md in `.agents/skills/` | Yes ("let's learn") | [platforms/openai-codex/](platforms/openai-codex/) |
| **Cursor AI** | .mdc rules or .cursorrules | Partial (must reference files) | [platforms/cursor-ai/](platforms/cursor-ai/) |
| **Any AI assistant** | Read the SKILL.md as instructions | Manual (paste the protocol) | Copy SKILL.md contents into your prompt |

The core methodology is **plain markdown**. The skills are automation wrappers. You can use this with ChatGPT, Gemini, or any LLM by manually following the SKILL.md protocol.

---

## Voice Integration (Recommended)

Pair this with a voice dictation tool for conversational learning:

- **Quiz answers**: Explain terms out loud. Builds verbal recall for interviews.
- **Socratic responses**: Reason verbally before the AI reveals. Activates different memory pathways.
- **Portfolio exercises**: Dictate your LinkedIn posts and memos at 170+ WPM.

Recommended: [WisprFlow](https://wisprflow.ai/) (macOS), Apple Dictation (free), or Whisper (self-hosted).

---

## Example: Spatial AI Curriculum

The `examples/spatial-ai/` folder contains sample sessions from a real 10-week curriculum on Spatial AI, World Models, and Embodied Intelligence.

---

## FAQ

**Q: Do I need Claude Code specifically?**
No. The methodology is plain markdown. Claude Code and OpenAI Codex have the best automation, but any LLM works.

**Q: How long does it take to set up?**
Design your curriculum: 2-3 hours. Configure the engine: 15 minutes. Start learning: immediately.

**Q: What's new in v2?**
Pre-testing, Socratic method, SM-2 spaced repetition, confidence calibration, interleaved practice, portfolio exercises, mastery gates, concept caps, weekly synthesis challenges, learning velocity dashboard, and a generic engine architecture with CURRICULUM-CONFIG.md.

**Q: Can I use this for non-technical topics?**
Yes. Finance, law, history, language, music theory — any structured learning works.

**Q: What if I miss a day?**
The engine uses session numbers, not calendar days. Pick up where you left off. SM-2 recalculates review priorities automatically.

**Q: What if I want multiple sessions in one sitting?**
Go for it. Sessions are decoupled from calendar days. Do as many as you want.

---

## Contributing

PRs welcome. Areas where help is needed:
- Additional platform adapters (Windsurf, Aider, etc.)
- Example curricula for different topics
- Improvements to the SM-2 algorithm or confidence calibration
- Translations of the template files

---

## License

MIT

---

Built by [@ForBotSake](https://x.com/forbotsakeco). Powered by evidence-based learning science and a real 10-week Spatial AI learning sprint.
