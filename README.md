# ai-learning-engine

An open-source, AI-powered structured learning system. Design a curriculum on any topic, then learn it interactively with an AI tutor that tracks your progress, quizzes you with spaced repetition, and never lets you skip ahead.

Works with **Claude Code**, **OpenAI Codex**, **Cursor AI**, or any AI assistant that reads markdown files.

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

1. **Auto-resumes** from exactly where you left off. No manual tracking.
2. **Quizzes you** on previous material using spaced repetition. Terms you get wrong come back more often.
3. **Blocks advancement** until you demonstrate understanding. Phase gates require 80% quiz scores and verbal explanation.
4. **Forces you to explain** what you learned in 2-3 sentences, as if pitching to a specific audience. If you can't explain it simply, you don't know it yet.
5. **Tracks everything** in plain markdown. Your git history becomes a portfolio of consistent daily learning.
6. **Generates pre-reads** for tomorrow's session using live web research, so your material is always current.

---

## Quick Start

```bash
git clone https://github.com/YOUR_USERNAME/ai-learning-engine.git my-learning-project
cd my-learning-project
```

1. Copy `CURRICULUM-TEMPLATE.md` to `CURRICULUM.md` and fill in your topic
2. Update `SESSION-STATE.md` with your topic name and total days
3. Install the skills for your platform (see [Platform Setup](#platform-setup))
4. Type **"let's learn"** in your AI assistant

See `SETUP-GUIDE.md` for the full walkthrough.

---

## How a Session Works

```
You: "let's learn"

AI: [reads SESSION-STATE.md, loads today's lesson]

=== Day 7 of 50: How Robots See (Perception) ===

Flags from last session:
- You mixed up "perception" and "planning" again. Perception = sensing ONLY.

--- QUIZ (10 terms from Days 1-6) ---
Term 1: What is a VLA?
You: [answer]
Score: 7/10. Good, but remember: it's "LLM + eyes + hands"...

--- TODAY'S LESSON ---
[Interactive teaching, bridged to your existing knowledge]
[Comprehension questions throughout]

--- DRILL ---
[Hands-on exercise from curriculum]

--- REFLECT ---
"Explain perception to a hiring manager in 3 sentences."
You: [answer]
Score: 4/5. Clean explanation. Add one concrete example next time.

--- SESSION COMPLETE ---
Day 7 done. 14% complete.
Next session: Day 8 - How Robots Think (Planning)
[Auto-generates tomorrow's pre-read with latest research]
[Commits progress to git]
```

---

## The Methodology

### Daily Session Format (3-4 hours)

| Block | Duration | What |
|-------|----------|------|
| **Quiz** | 15 min | Spaced repetition on previous terms. Weak terms surface more often. |
| **Lesson** | 60-90 min | Interactive teaching. Not a wall of text. Questions throughout. |
| **Drill** | 30 min | Hands-on exercise. Build, analyze, or create something. |
| **Community** | 10 min | Track engagement in relevant communities. |
| **Reflect** | 15 min | "Explain it to [audience]" summary. Score 1-5. |

### Spaced Repetition

Every term gets tracked in the Terminology Mastery Tracker:

| Term | Times Correct | Status |
|------|--------------|--------|
| World Model | 3 | Known |
| Degrees of Freedom | 1 | Learning |
| NeRF | 0 | New |

- Terms answered correctly 3+ times = "Known" (quizzed less often)
- Terms answered wrong = resurface in the next quiz
- New terms from today's lesson added automatically

### Phase Gates

Each phase ends with a structured assessment. You cannot advance until you pass.

| Gate | Format | Threshold |
|------|--------|-----------|
| Phase 1 | Term quiz + verbal explanation | 80% quiz, 4/5 explain |
| Phase 2 | Term quiz + pitch a concept | 80% quiz, 4/5 explain |
| Phase 3 | Portfolio project defense | Project complete, 4/5 defense |
| Phase 4 | Mock interview | Pass 2/3 rounds |

### SWOT Evolution

At the end of Phase 1, 2, and 4, you complete a structured SWOT self-assessment. Comparing your SWOTs over time shows how your understanding and confidence evolved.

### Community Engagement (Parallel Track)

| Phase | Activity |
|-------|----------|
| 1-2 | Lurk. Join 8-10 communities. Observe. Don't post. |
| 3 | Narrow to 3-4. Start replying. Share your project. |
| 4+ | Contribute original content. DM people. Go IRL. |

---

## Repo Structure

```
ai-learning-engine/
+-- README.md                      <- You're here
+-- SETUP-GUIDE.md                 <- Step-by-step setup
+-- CURRICULUM-TEMPLATE.md         <- Template: design your curriculum
+-- SESSION-STATE.md               <- Template: session state machine
+-- progress.md                    <- Template: daily log
+-- COMMUNITIES-TEMPLATE.md        <- Template: community tracker
+-- RESEARCH-REFERENCE.md          <- Template: verified data/sources
+-- CLAUDE-SNIPPET.md              <- CLAUDE.md / AGENTS.md snippet
+-- skills/
|   +-- learn/SKILL.md             <- Session runner skill
|   +-- learn-end/SKILL.md         <- Session exit skill
+-- platforms/
|   +-- claude-code/README.md      <- Claude Code / Cowork setup
|   +-- openai-codex/README.md     <- OpenAI Codex setup
|   +-- cursor-ai/README.md        <- Cursor AI setup
+-- examples/
|   +-- spatial-ai/                <- Example: Spatial AI curriculum
+-- sessions/                      <- Pre-read files (auto-generated)
+-- assessments/                   <- Phase gate results
+-- swot/                          <- Self-assessments
+-- build-project/                 <- Portfolio project files
+-- outreach/                      <- Networking tracker
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

Pair this curriculum with a voice dictation tool for a truly conversational learning experience:

### Why Voice?

- **Quiz answers**: Explain terms out loud instead of typing. Builds verbal recall for interviews and networking.
- **"Explain it to [audience]" exercises**: Practice your pitch verbally. The AI scores your explanation.
- **Faster interaction**: Dictate at 170+ WPM vs typing at 60 WPM. Sessions feel like conversations, not homework.
- **Memory retention**: Speaking activates different memory pathways than reading/typing. You remember more.

### Recommended Tools

| Tool | Platform | AI Integration | Price |
|------|----------|---------------|-------|
| [WisprFlow](https://wisprflow.ai/) | macOS | Native Cursor, VS Code, terminal | Free tier / $10/mo |
| Apple Dictation | macOS/iOS | System-wide | Free |
| Windows Voice Typing | Windows | System-wide | Free |
| Whisper (local) | Any | Self-hosted, private | Free (open source) |

### Setup with WisprFlow

1. Install WisprFlow from [wisprflow.ai](https://wisprflow.ai/)
2. Open your AI tool (Claude Code, Codex, Cursor)
3. Hold the WisprFlow hotkey and speak
4. Your voice is transcribed directly into the AI's input field

During sessions: say your quiz answers, explain concepts verbally, dictate your reflection notes. The AI processes your spoken text exactly like typed text.

---

## Example: Spatial AI Curriculum

The `examples/spatial-ai/` folder contains sample sessions from a real 10-week curriculum on Spatial AI, World Models, and Embodied Intelligence. It demonstrates:

- How Day 2 and Day 3 sessions are structured
- Pre-read format with flags, quiz terms, lesson content, and exercises
- How terminology mastery tracking works across sessions
- The "bridge to existing knowledge" pattern in action

Use these as reference when designing your own curriculum.

---

## FAQ

**Q: Do I need Claude Code specifically?**
No. The methodology is plain markdown. Claude Code and OpenAI Codex have the best automation (auto-trigger, skills), but you can use this with any AI by reading the SKILL.md protocol to it.

**Q: How long does it take to design a curriculum?**
Phase 1 in detail: 2-3 hours. Rough outline for remaining phases: 1-2 hours. You refine later phases as you learn. Don't over-plan upfront.

**Q: Can I use this for non-technical topics?**
Yes. The methodology works for any structured learning: finance, law, history, language, music theory, etc. The quiz system, phase gates, and community engagement apply universally.

**Q: What if I miss a day?**
The state machine picks up where you left off. No penalty. The spaced repetition system will re-quiz weak terms from earlier days.

**Q: Can I share my curriculum with others?**
Yes. Fork this repo, fill in your CURRICULUM.md, and share. Others can clone and learn the same material with their own progress tracking.

---

## Contributing

PRs welcome. Areas where help is needed:
- Additional platform adapters (Windsurf, Aider, etc.)
- Example curricula for different topics
- Improvements to the quiz/spaced repetition algorithm
- Translations of the template files

---

## License

MIT

---

Built by [@ForBotSake](https://x.com/forbotsakeco). Powered by the methodology from a real 10-week Spatial AI learning sprint.
