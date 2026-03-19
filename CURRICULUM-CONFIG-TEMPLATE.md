# Curriculum Configuration: [YOUR TOPIC]

> This file configures the Adaptive Learning Engine for your curriculum.
> The engine reads this config at session start. Replace all [BRACKETED] values with your details.
> Save as `CURRICULUM-CONFIG.md` when ready.

## Curriculum Identity

| Field | Value |
|-------|-------|
| **curriculum_name** | [YOUR TOPIC NAME] |
| **curriculum_dir** | [PATH TO YOUR CURRICULUM FOLDER, e.g., "career/my-topic/"] |
| **curriculum_file** | CURRICULUM.md |
| **state_file** | SESSION-STATE.md |
| **progress_file** | progress.md |
| **portfolio_dir** | portfolio/ |
| **communities_file** | COMMUNITIES.md |
| **research_reference** | RESEARCH-REFERENCE.md |
| **target_sessions** | ~[ESTIMATED TOTAL] (flexible — depends on concept cap splits) |

## Learner Bridges

Connect new concepts to the learner's existing knowledge. The engine uses these as Socratic entry points during lessons.

Think: "What do I already know that's similar to what I'm learning?"

- **[YOUR EXPERTISE 1]**: [Brief description, e.g., "5 years of Python — can relate to programming concepts"]
- **[YOUR EXPERTISE 2]**: [e.g., "MBA — understands business strategy, market sizing, competitive analysis"]
- **[YOUR EXPERTISE 3]**: [e.g., "Managed a team of 10 — understands coordination, delegation"]
- **[YOUR EXPERTISE 4]**: [e.g., "Built an e-commerce store — knows customer acquisition, unit economics"]

## Exercise Types (Portfolio Artifacts)

Every drill produces a real artifact the learner can use. Rotate through these formats:

- [EXERCISE TYPE 1, e.g., "LinkedIn post (2-3 paragraphs explaining a concept)"]
- [EXERCISE TYPE 2, e.g., "Analysis memo (1-page strategic analysis)"]
- [EXERCISE TYPE 3, e.g., "Pitch deck slides (2-3 slides for a presentation)"]
- [EXERCISE TYPE 4, e.g., "Cold email draft (personalized outreach using learned concepts)"]
- [EXERCISE TYPE 5, e.g., "Blog post outline (structured deep-dive for personal site)"]
- [EXERCISE TYPE 6, e.g., "Teaching script (explain concept to someone with zero background)"]

## Mastery Thresholds

| Phase | Threshold | When |
|-------|-----------|------|
| Phase 1 ([PHASE NAME]) | [X]/10 | Sessions 1-[Y] |
| Phase 2+ ([PHASE NAME]) | [X]/10 | Sessions [Y]+ |

Mastery gates use these thresholds. Below threshold → 10-min remediation → re-test. Fail twice → advance with a "weak" flag (the engine never blocks indefinitely).

## Synthesis Challenge Schedule

Weekly synthesis replaces interleaved practice + portfolio exercise on every 5th session:
- Session 5: Week 1 synthesis
- Session 10: Week 2 synthesis
- Session 15, 20, 25...: Continue pattern

## Tone & Style

- [YOUR PREFERRED TONE, e.g., "Direct, quantitative, zero-fluff"]
- [DATA PREFERENCES, e.g., "Quantify everything with numbers and sources"]
- [HONESTY PREFERENCE, e.g., "Zero tolerance for hallucinations — say 'unsure' if unsure"]
- [FOLLOW-UP, e.g., "Suggest 2-3 next questions after each session"]

## Community Engagement Phases

| Phase | Approach |
|-------|----------|
| Phase 1-2 | Lurk: observe communities, note interesting threads/people/topics |
| Phase 3 | Narrow: select 3-4 communities based on learning goals, start engaging |
| Phase 4+ | Contribute: active posting, connect online to IRL meetings |
