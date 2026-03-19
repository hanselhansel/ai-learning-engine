# Teach-Back & Peer Teaching Simulation

## When to Trigger
- Deep Dive mode: ALWAYS (dedicated block)
- Standard mode: every 3rd session (replaces portfolio exercise)
- Synthesis mode: ALWAYS (2-min pitch of the week's big idea)

## Teach-Back Flow

### Step 1: Set the Scene
"Imagine you're explaining [CONCEPT] to a colleague who's smart but knows nothing about this field. They're skeptical — they'll push back if something doesn't make sense."

### Step 2: Learner Teaches (3-5 min)
- Learner explains the concept in their own words
- NO notes, NO looking things up — pure retrieval
- Claude stays silent during the explanation

### Step 3: Skeptical Colleague Response (E3)
Claude plays a skeptical but fair colleague. Ask 2-3 follow-up questions:

**Question types (rotate):**
1. **Clarification**: "Wait, what do you mean by [term they used loosely]?"
2. **So-what**: "Okay, but why should I care? What's the business impact?"
3. **Edge case**: "What happens when [unusual scenario]?"
4. **Analogy challenge**: "You compared it to [X], but isn't [Y] a better analogy because...?"
5. **Depth probe**: "You said [surface claim]. But HOW does that actually work under the hood?"

**Skepticism calibration:**
- Early sessions (1-10): friendly skeptic (60% supportive, 40% challenging)
- Mid sessions (11-30): balanced skeptic (40% supportive, 60% challenging)
- Late sessions (31+): tough skeptic (20% supportive, 80% challenging)

### Step 4: Score
| Dimension | 1 (Weak) | 3 (Adequate) | 5 (Strong) |
|-----------|----------|--------------|------------|
| **Accuracy** | Major errors | Minor gaps | Fully correct |
| **Clarity** | Confusing | Understandable | Crystal clear |
| **Depth** | Surface only | Some mechanism | Root understanding |
| **Business connect** | None | Mentioned | Compelling case |

Overall score = average of 4 dimensions.
- Score >= 4.0: "You could teach this at a meetup"
- Score 3.0-3.9: "Solid. One area to sharpen: [specific]"
- Score < 3.0: "Let's revisit. Here's what to focus on: [specific]"

### Step 5: Corrective Feedback
- Highlight what was excellent (reinforce)
- Point out 1-2 specific gaps (not a laundry list)
- Give a "next time, try leading with..." suggestion

## Retention Boost
Teach-back achieves 90% retention (vs. 10% lecture, 50% discussion).
The skeptical colleague follow-ups force ELABORATION, which strengthens memory traces.
