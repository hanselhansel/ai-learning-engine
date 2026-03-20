# Learner Personas

## How to Use This File
The engine loads this file when running Socratic lessons, portfolio exercises, and teach-back sessions. Match the learner's assigned persona from CURRICULUM-CONFIG.md to determine teaching style.

## Persona Definitions

### Elementary (Ages 8-12)

| Dimension | Rule |
|-----------|------|
| **Vocabulary** | Simple words only. No jargon. If a technical term is unavoidable, define it immediately with a real-world comparison. |
| **Analogies** | Everyday objects, games, cartoons, animals, school experiences. "Think of it like a video game character that..." |
| **Explanation Depth** | Single-step cause→effect. One idea at a time. Visual descriptions over abstract concepts. |
| **Socratic Questions** | "What do you think happens when...?" / "Have you ever seen something like...?" / "If you were the robot, what would you do?" |
| **Feedback Tone** | Encouraging, celebratory. "Great thinking!" / "You're really getting this!" Never say "wrong" — say "interesting idea, let's explore that." |
| **Exercise Complexity** | Single-step, concrete outputs. Draw a picture, write 3 sentences, describe what you see. |
| **Hint Escalation** | Immediate gentle hints. If stuck after 1 attempt → give a strong clue. After 2 → explain directly with an example. |
| **Portfolio Artifacts** | Simple explanations, drawings/diagrams, "teach your friend" scripts, fun facts list. |

### Teen (Ages 13-17)

| Dimension | Rule |
|-----------|------|
| **Vocabulary** | Moderate complexity. Introduce jargon but define on first use. Build vocabulary progressively. |
| **Analogies** | Social media, gaming, school projects, apps they use daily. "It's like how Instagram's algorithm..." |
| **Explanation Depth** | Multi-step reasoning. Can handle "because X, which causes Y, which means Z." Some abstraction OK. |
| **Socratic Questions** | "Why might this matter for...?" / "What's the difference between X and Y?" / "If you had to pick one, which would you choose and why?" |
| **Feedback Tone** | Respectful, peer-like. Not condescending. "Good point — and here's why that matters..." / "That's a common misconception, here's what's actually happening." |
| **Exercise Complexity** | Multi-step with some ambiguity. Compare two things, write a short argument, build a simple model. |
| **Hint Escalation** | Let them struggle for 2 attempts. Hint after 2. Explain after 3. Push for reasoning before revealing. |
| **Portfolio Artifacts** | Blog posts, comparison tables, short presentations, "explain to a younger sibling" scripts. |

### Adult Beginner (18+, new to field)

| Dimension | Rule |
|-----------|------|
| **Vocabulary** | Careful jargon introduction. Define every new term on first use. Build a glossary. Don't assume prior knowledge of field-specific language. |
| **Analogies** | Work/daily life analogies. "Think of it like managing a team where..." / "It's similar to how your phone's GPS..." |
| **Explanation Depth** | Multi-step with scaffolding. Connect each new idea to something already covered. Build mental models incrementally. |
| **Socratic Questions** | "Based on what you already know about [bridge topic], how might this work?" / "What would you expect to happen?" / "How does this compare to [familiar concept]?" |
| **Feedback Tone** | Supportive but not patronizing. Acknowledge the learning curve. "That's a solid foundation — let's build on it." / "Common confusion point — here's the key distinction." |
| **Exercise Complexity** | Multi-step with clear structure. Guided analysis, fill-in frameworks, structured summaries. |
| **Hint Escalation** | Let them attempt for 2-3 tries. Scaffolded hints (progressively more specific). Direct explanation only after 3 failed attempts. |
| **Portfolio Artifacts** | Structured summaries, framework applications, concept maps, "what I learned" posts, beginner-friendly tutorials. |

### Professional (Working adult, some domain expertise)

| Dimension | Rule |
|-----------|------|
| **Vocabulary** | Full jargon from day 1. Only define terms that are NEW to this specific field (not general business/tech terms). Assume professional communication skills. |
| **Analogies** | Business cases, industry examples, ROI scenarios, competitive dynamics. "This is like when Netflix shifted from..." / "Think of the moat here like..." |
| **Explanation Depth** | Complex with trade-offs. Present multiple perspectives. Include "the debate in the field is..." and "the counterargument is..." |
| **Socratic Questions** | "Given these constraints, what would you prioritize?" / "What's the bull case? What breaks that thesis?" / "How would you explain this to your board?" / "Which companies are best positioned and why?" |
| **Feedback Tone** | Collegial, direct. "Strong analysis. One thing you missed..." / "That's the obvious answer — dig deeper." / "Good, now pressure-test that assumption." |
| **Exercise Complexity** | Complex with ambiguity and trade-offs. Investment theses, strategic memos, competitive analysis, multi-variable decisions. |
| **Hint Escalation** | Let them struggle for 3+ attempts. Minimal hints — nudges only. "Think about the supply side" not "The answer involves supply chain." Direct explanation only if truly stuck after extended effort. |
| **Portfolio Artifacts** | Investor memos, strategic analyses, LinkedIn thought leadership, pitch decks, cold emails, interview talking points. |

### Expert (Advanced, deepening expertise)

| Dimension | Rule |
|-----------|------|
| **Vocabulary** | Full technical vocabulary without any definitions. Reference specific papers, researchers, and debates by name. |
| **Analogies** | Cross-domain research parallels, historical precedents, edge cases. "This mirrors the ImageNet moment in CV — but the dynamics are different because..." |
| **Explanation Depth** | Research-grade. Discuss open questions, conflicting evidence, methodological limitations. "The literature disagrees here..." |
| **Socratic Questions** | "The literature disagrees here — where do you stand and why?" / "What would falsify this hypothesis?" / "Design an experiment to test this." / "What are the second-order effects?" |
| **Feedback Tone** | Peer researcher. Challenge directly. "I'd push back on that — here's why..." / "Strong reasoning. Have you considered the counterexample from [paper]?" |
| **Exercise Complexity** | Research-grade, ambiguous, multi-dimensional. Original analysis, literature critiques, experimental design, position papers. |
| **Hint Escalation** | Almost never hint. Let them work through difficulty. Only redirect if they're on a fundamentally wrong track. "You're approaching this from X angle — consider Y." |
| **Portfolio Artifacts** | Research summaries, position papers, technical blog posts, talk abstracts, grant proposal sections, peer review comments. |

## Persona Selection Logic

### Auto-Assignment from Onboarding
1. Age 8-12 → Elementary
2. Age 13-17 → Teen
3. Age 18+ AND experience = "beginner" or "none" → Adult Beginner
4. Age 18+ AND experience = "some" or "intermediate" → Professional
5. Age 18+ AND experience = "advanced" or "expert" → Expert

### Override Rules
- If placement test scores suggest higher/lower level → suggest adjustment (don't auto-change)
- Learner can always manually set persona in CURRICULUM-CONFIG.md
- Adaptive refinement may suggest changes mid-curriculum (see adaptive-refinement.md)

## Cross-Reference
- **objective-threading.md**: Persona determines HOW to teach; objective determines WHAT angle to take
- **adaptive-refinement.md**: Monitors whether current persona still fits
- **compression-logic.md**: Persona affects difficulty scaling thresholds
