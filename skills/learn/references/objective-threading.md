# Learning Objective Threading

## How to Use This File
The engine loads this file to thread the learner's goal through every session block. The learner's primary_goal and perspective_lenses come from CURRICULUM-CONFIG.md.

## Goal Templates

### Career/Job Prep
| Block | Thread |
|-------|--------|
| **Socratic Questions** | "How would you explain this in an interview?" / "Which companies use this?" / "What would an interviewer want to hear?" |
| **Portfolio Exercises** | Interview answers, LinkedIn posts, networking soundbites, portfolio pieces, cold emails to hiring managers |
| **Quiz Emphasis** | Explaining clearly to non-experts, practical application over theory |
| **Pre-Test Angle** | "If asked about this in a technical screen, what would you say?" |
| **Mastery Criteria** | Can explain concept clearly, knows which companies use it, can discuss trade-offs |

**perspective_lenses**: interview readiness, company landscape, networking angles, role requirements, industry trends
**exercise_framing**: "Draft an answer you'd give if asked about [concept] in a technical interview."

### Academic
| Block | Thread |
|-------|--------|
| **Socratic Questions** | "What does the research say?" / "What are the open questions?" / "Who are the key researchers?" |
| **Portfolio Exercises** | Literature reviews, research proposals, paper summaries, annotated bibliographies |
| **Quiz Emphasis** | Precision, citations, methodology awareness |
| **Pre-Test Angle** | "What does the current literature suggest about...?" |
| **Mastery Criteria** | Can cite key papers, understands methodology, identifies open research questions |

**perspective_lenses**: research landscape, methodology, key papers, open problems, funding trends
**exercise_framing**: "Write a 1-paragraph literature review covering [concept]."

### Investment/Business
| Block | Thread |
|-------|--------|
| **Socratic Questions** | "What's the bull/bear case?" / "What's the TAM?" / "Who wins and why?" / "What's the moat?" |
| **Portfolio Exercises** | Investor memos, competitive analysis, market sizing, DCF assumptions, thesis construction |
| **Quiz Emphasis** | Strategic implications, market dynamics, competitive positioning |
| **Pre-Test Angle** | "If you were investing in this space, what would you want to know?" |
| **Mastery Criteria** | Can build investment thesis, size markets, identify moats and risks |

**perspective_lenses**: market sizing, competitive dynamics, valuation frameworks, risk factors, unit economics
**exercise_framing**: "Write a 1-paragraph investor thesis for a company using [concept]."

### Hobby/Curiosity
| Block | Thread |
|-------|--------|
| **Socratic Questions** | "What's the coolest thing about this?" / "What surprised you?" / "What would you want to try?" |
| **Portfolio Exercises** | Blog posts, community posts, creative projects, "today I learned" entries |
| **Quiz Emphasis** | Exploration, connections, surprising facts |
| **Pre-Test Angle** | "What's your intuition about how this works?" |
| **Mastery Criteria** | Can explain concept in their own words, makes creative connections |

**perspective_lenses**: surprising facts, creative applications, community discussions, DIY possibilities, fun experiments
**exercise_framing**: "Write a short blog post about why [concept] is fascinating."

### Teaching/Mentoring
| Block | Thread |
|-------|--------|
| **Socratic Questions** | "How would you explain this to a complete beginner?" / "What analogy would you use?" / "What's the most common misconception?" |
| **Portfolio Exercises** | Teaching scripts, workshop outlines, tutorial drafts, explainer videos scripts, curriculum snippets |
| **Quiz Emphasis** | Clarity, scaffolding, misconception awareness |
| **Pre-Test Angle** | "If you had to teach this in 2 minutes, what would you say?" |
| **Mastery Criteria** | Can explain at multiple levels, anticipates confusion, builds scaffolded explanations |

**perspective_lenses**: common misconceptions, progressive difficulty, analogy design, assessment design, learner engagement
**exercise_framing**: "Write a 5-minute teaching script explaining [concept] to someone with zero background."

### Building/Engineering
| Block | Thread |
|-------|--------|
| **Socratic Questions** | "How would you implement this?" / "What breaks first?" / "What's the architecture?" / "Where are the bottlenecks?" |
| **Portfolio Exercises** | Technical specs, architecture docs, code snippets, system design docs, API designs |
| **Quiz Emphasis** | Practical application, implementation details, failure modes |
| **Pre-Test Angle** | "If you had to build this, where would you start?" |
| **Mastery Criteria** | Can design a system, identify failure modes, make architecture decisions |

**perspective_lenses**: implementation details, system design, failure modes, performance, toolchain
**exercise_framing**: "Draft a technical spec for implementing [concept] in a real system."

## Multi-Objective Blending

When a learner has multiple goals (e.g., Career/Job Prep 60% + Investment/Business 40%), blend the threading:

### Weight Application Rules
1. **Socratic Questions**: Alternate angles proportional to weights. In a 10-question session with 60/40 split: ~6 career-angled, ~4 investment-angled.
2. **Portfolio Exercises**: Rotate exercise types based on weights. 3 career exercises per 2 investment exercises.
3. **Quiz Emphasis**: Combine criteria. "Can you explain this clearly (career) AND assess the market opportunity (investment)?"
4. **Pre-Test Angle**: Use primary objective's angle by default. Occasionally swap to secondary.

### Blending in Practice
```
If primary_goal weight >= 0.7:
  → Use primary threading for 70%+ of interactions
  → Sprinkle secondary angle 1-2 times per session

If weights are balanced (0.4-0.6 each):
  → Alternate angles per block
  → Socratic: primary angle, Exercise: secondary angle, Quiz: blend both

If 3+ objectives:
  → Primary gets ~50% of threading
  → Distribute remainder proportionally among secondaries
  → Never thread more than 2 angles in a single question
```

### Config Format (CURRICULUM-CONFIG.md)
```markdown
## Learning Objective

| Field | Value |
|-------|-------|
| **primary_goal** | Career/Job Prep |
| **secondary_goals** | Investment/Business |
| **goal_weights** | career: 0.6, investment: 0.4 |
| **career_target** | "Get hired as Spatial AI PM in SF" |
| **perspective_lenses** | ["interview readiness", "company landscape", "investment/valuation", "networking angles"] |
| **objective_statement** | "I'm learning spatial AI so I can get hired and invest intelligently in the space" |
```

## Cross-Reference
- **learner-personas.md**: Persona determines teaching STYLE; this file determines teaching ANGLE
- **compression-logic.md**: Objective affects which concepts get compressed vs. expanded
- **teach-back-protocol.md**: Teach-back scenarios should reflect the learner's objective
