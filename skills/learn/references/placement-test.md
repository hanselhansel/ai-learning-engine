# Placement Test

## How to Use This File
The generate-curriculum skill reads this file during onboarding to auto-assign a learner persona. The test consists of 3 diagnostic questions at increasing difficulty.

## Test Design

### Question Selection
Generate 3 questions about the curriculum topic at these levels:

| Question | Difficulty | Tests For | Maps To |
|----------|-----------|-----------|---------|
| Q1: Easy | Elementary/Teen | Basic awareness. Can they recognize the topic? Do they know what it IS? | If wrong → Elementary or Teen (based on age) |
| Q2: Medium | Adult Beginner/Professional | Applied understanding. Can they explain WHY something matters or HOW it connects to other things? | If wrong → Adult Beginner. If right → at least Professional. |
| Q3: Hard | Professional/Expert | Depth and nuance. Can they analyze trade-offs, cite specifics, or critique an approach? | If right → Expert. If partially right → Professional. |

### Question Format
- Open-ended, not multiple choice (to assess vocabulary and depth)
- Topic-specific (generated from the curriculum's subject matter)
- Brief — each answer should take 1-2 minutes

### Example (Spatial AI Curriculum)
```
Q1 (Easy): "In your own words, what is spatial AI? Don't worry if you're not sure — just share your best guess."

Q2 (Medium): "Why might a robot that works perfectly in simulation fail when deployed in the real world? What factors could cause this gap?"

Q3 (Hard): "Compare two approaches to training robots: reinforcement learning in simulation vs. imitation learning from human demonstrations. What are the trade-offs of each?"
```

### Scoring Rubric

| Response Quality | Persona Assignment |
|-----------------|-------------------|
| Q1 wrong or very vague | Elementary (if young) or Adult Beginner (if adult) |
| Q1 right, Q2 wrong | Adult Beginner |
| Q1 right, Q2 partially right | Adult Beginner (high end) |
| Q1 right, Q2 right, Q3 wrong | Professional |
| Q1 right, Q2 right, Q3 partially right | Professional (high end) |
| All three right with depth | Expert |

### Fallback
If the diagnostic is inconclusive (mixed signals, unclear answers):
→ Default to **Adult Beginner**
→ Flag for refinement in Session 1
→ Add to SESSION-STATE.md flags: "Placement test inconclusive — observe closely in Session 1"

### Warm-Start Exception
If SESSION-STATE.md already exists (returning learner or existing curriculum):
→ SKIP the placement test entirely
→ Auto-assign persona from session history data (vocabulary level, answer depth, quiz scores)
→ Professional is default for learners with 5+ completed sessions and quiz scores ≥ 70%

### Tone Preview
After persona assignment, show the learner a brief preview:

```
Based on your answers, I'll teach at a [PERSONA] level:
- [1-sentence description of what that means]
- [Example Socratic question they'd see]
- [Example exercise type]

Does this feel right? You can always adjust later.
```

If the learner wants to adjust → update persona in config immediately.

## Cross-Reference
- **learner-personas.md**: Defines the personas being assigned
- **adaptive-refinement.md**: Takes over persona monitoring after initial assignment
