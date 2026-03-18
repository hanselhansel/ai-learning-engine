# [YOUR TOPIC]: Learning Curriculum

**Owner:** [Your Name]
**Goal:** [What you want to achieve, e.g., "Get hired as a PM in [field]", "Build expertise in [domain]", "Launch a [project]"]
**Timeline:** [X weeks], [Y hours/day]
**Start Date:** [Date]
**Created:** [Date]

---

## TLDR

[2-3 sentence summary of what this curriculum does and what outcome the learner will have at the end.]

---

## How This Curriculum Works

### Daily Session Format ([X] hours)

| Block | Duration | What |
|-------|----------|------|
| **Learn** | 60-90 min | Read/watch assigned material, then discuss with Claude |
| **Drill** | 30 min | Terminology quiz, concept explanation exercise, or problem breakdown |
| **Build/Analyze** | 60-90 min | Hands-on project work, analysis, or outreach prep |
| **Reflect** | 15 min | Log what you learned, update your "explain it to [target audience]" notes |

### Progress Tracking

After each session, update `progress.md` with:
- Date and phase/week/day
- Key concepts learned
- Questions that came up
- "Explain it to [target audience]" summary (2-3 sentences you could use at a networking event, interview, or pitch)

### How to Use with Claude

Just type: **"let's learn"** in any Claude session.

To end a session early: type **"done learning"** or **"learn-end"**

Claude auto-resumes from where you left off. No need to track phase/week/day. Everything is stored in `SESSION-STATE.md`, which Claude reads at session start.

**How it works:**
1. You type "let's learn"
2. Claude reads `SESSION-STATE.md` to find your exact position
3. Claude loads today's lesson from `CURRICULUM.md`
4. Session runs (quiz, lesson, drill, community check, reflect)
5. Claude advances the day counter and updates all tracking files
6. You never need to remember where you are

### Assessment System

Each phase ends with a structured assessment: quiz on terminology retention + verbal explanation exercise where you explain a concept to a specific audience. Claude scores on a 1-5 scale.

| Assessment | When | Format | Pass Threshold |
|-----------|------|--------|---------------|
| **Phase 1 Gate** | End of [Week X] | [X] term quiz + explain "[key concept]" in 2 min | 80% quiz, 4/5 explain |
| **Phase 2 Gate** | End of [Week X] | [X] term quiz + pitch a [domain concept] in 3 min | 80% quiz, 4/5 explain |
| **Phase 3 Gate** | End of [Week X] | Portfolio project review + defend your decisions | Project complete, 4/5 defense |
| **Phase 4 Gate** | End of [Week X] | Full mock interview (behavioral + technical + case) | Pass 2/3 rounds |
| **SWOT Self-Assessment** | End of Phase 1, 2, and 4 | Structured SWOT on your fit in this space | Honest completion |

### Community Engagement Strategy

| Phase | Community Activity |
|-------|-------------------|
| **Phase 1-2** | **Lurk mode.** Join communities. Read daily. Note who posts valuable content, what topics get traction. Do NOT post yet. |
| **Phase 3** | **Narrow + Engage.** Pick 3-4 communities. Start with replies and questions. Share your project for feedback. |
| **Phase 4+** | **Contribute.** Post original content. DM interesting people. Convert online connections to IRL meetings. |

### Folder Structure

```
your-curriculum/
+-- CURRICULUM.md          <- This file (master plan, read-only reference)
+-- SESSION-STATE.md       <- Auto-loaded each session (current state, scores)
+-- COMMUNITIES.md         <- Community tracker
+-- RESEARCH-REFERENCE.md  <- Verified data and sources
+-- progress.md            <- Daily learning log
+-- swot/                  <- SWOT self-assessments
+-- assessments/           <- Assessment results
+-- build-project/         <- Portfolio project files
+-- sessions/              <- Pre-read files (day-XX-session.md)
+-- outreach/              <- Contact lists, meeting notes
```

---

## Phase 1: [Phase Name] (Weeks [X-Y])

**Objective:** [What the learner should understand by the end of this phase.]

### Week 1: [Week Theme]

#### Day 1: [Topic]

**Core question:** [The one question this day answers.]

| Topic | Details |
|-------|---------|
| [Concept 1] | [Brief description] |
| [Concept 2] | [Brief description] |
| [Concept 3] | [Brief description] |

**Reading:**
- [Resource 1]
- [Resource 2]

**Exercise:** [Hands-on task that bridges the learner's existing knowledge to new material.]

**Bridge to your experience:** [How this connects to what the learner already knows.]

---

#### Day 2: [Topic]

<!-- Continue pattern for all days -->

---

## Phase 2: [Phase Name] (Weeks [X-Y])

**Objective:** [...]

<!-- Continue pattern for all phases -->

---

## Tips for Writing Your Curriculum

1. **Start with the end state.** What does "done" look like? Work backwards.
2. **Bridge constantly.** Every new concept should connect to something the learner already knows.
3. **Quantify progress.** Term counts, quiz scores, project milestones. Not vibes.
4. **Build in repetition.** The quiz system resurfaces weak terms automatically.
5. **Phase gates prevent skipping.** Don't advance until you've demonstrated understanding.
6. **Community is not optional.** Learning in isolation produces worse outcomes than learning in public.
7. **"Explain it to [audience]" forces clarity.** If you can't say it in 3 sentences, you don't understand it yet.
