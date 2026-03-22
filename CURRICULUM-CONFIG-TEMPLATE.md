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
| **sessions_dir** | sessions/ |
| **summaries_dir** | sessions/summaries/ |
| **archive_dir** | sessions/archive/ |
| **analytics_dashboard** | portfolio/analytics-dashboard.html |
| **concept_map** | portfolio/concept-map.md |
| **target_sessions** | ~[ESTIMATED TOTAL] (flexible — depends on concept cap splits) |

## Learner Bridges

Connect new concepts to the learner's existing knowledge. The engine uses these as Socratic entry points during lessons.

Think: "What do I already know that's similar to what I'm learning?"

- **[YOUR EXPERTISE 1]**: [Brief description, e.g., "5 years of Python — can relate to programming concepts"]
- **[YOUR EXPERTISE 2]**: [e.g., "MBA — understands business strategy, market sizing, competitive analysis"]
- **[YOUR EXPERTISE 3]**: [e.g., "Managed a team of 10 — understands coordination, delegation"]
- **[YOUR EXPERTISE 4]**: [e.g., "Built an e-commerce store — knows customer acquisition, unit economics"]

## Learner Profile

| Field | Value |
|-------|-------|
| **age_group** | [Elementary (8-12) / Teen (13-17) / Adult (18+)] |
| **experience_level** | [Beginner / Intermediate / Professional / Expert] |
| **domain_expertise** | [Brief description of relevant background, e.g., "5 years Python, MBA, built SaaS products"] |
| **persona** | [Auto-assigned from placement test: Elementary / Teen / Adult Beginner / Professional / Expert] |

The engine uses your persona to adjust teaching style, analogies, question difficulty, and feedback tone. See `references/learner-personas.md` for details on each persona.

## Learning Objective

| Field | Value |
|-------|-------|
| **primary_goal** | [Career/Job Prep / Academic / Investment/Business / Hobby / Teaching / Building] |
| **secondary_goals** | [Optional: additional goals, e.g., "Investment/Business"] |
| **goal_weights** | [e.g., "career: 0.6, investment: 0.4" — weights must sum to 1.0] |
| **career_target** | [Specific outcome, e.g., "Get hired as ML engineer at a robotics company"] |
| **perspective_lenses** | [Array of angles the engine threads through questions, e.g., "interview readiness, company landscape, valuation frameworks"] |
| **objective_statement** | [One sentence: "I'm learning X so that I can Y"] |

The engine threads your learning objective through every Socratic question, exercise, and quiz. Multi-objective blending distributes angles proportional to goal_weights. See `references/objective-threading.md`.

## Exercise Types (Portfolio Artifacts)

Every drill produces a real artifact the learner can use. Rotate through these formats:

- [EXERCISE TYPE 1, e.g., "LinkedIn post (2-3 paragraphs explaining a concept)"]
- [EXERCISE TYPE 2, e.g., "Analysis memo (1-page strategic analysis)"]
- [EXERCISE TYPE 3, e.g., "Pitch deck slides (2-3 slides for a presentation)"]
- [EXERCISE TYPE 4, e.g., "Cold email draft (personalized outreach using learned concepts)"]
- [EXERCISE TYPE 5, e.g., "Blog post outline (structured deep-dive for personal site)"]
- [EXERCISE TYPE 6, e.g., "Teaching script (explain concept to someone with zero background)"]

## Mastery Thresholds

| Phase | Quiz Threshold | Explain Threshold | When |
|-------|---------------|-------------------|------|
| Phase 1 ([PHASE_NAME]) | [X]/10 ([X]%) | [Y]/5 | Sessions 1-[N] |
| Phase 2 ([PHASE_NAME]) | [X]/10 ([X]%) | [Y]/5 | Sessions [N]-[M] |
| Phase 3 ([PHASE_NAME]) | [X]/10 ([X]%) or N/A (project-based) | [Y]/5 | Sessions [M]-[P] |
| Phase 4 ([PHASE_NAME]) | [X]/10 ([X]%) | [Y]/5 | Sessions [P]-[Q] |

Mastery gates use these thresholds. Below threshold → 10-min remediation → re-test. Fail twice → advance with "weak" flag (the engine never blocks indefinitely).

## Flex Session Defaults

| Setting | Value |
|---------|-------|
| **default_mode** | [Standard] |
| **synthesis_frequency** | [every 5th session] |
| **teach_back_frequency** | [every 3rd Standard session] |
| **growth_reflection_frequency** | [every 10th session] |
| **concept_cap** | [7 per session] |
| **sm2_quiz_cap** | [10 terms (3 for Micro)] |
| **interleaved_cap** | [5 questions (1 for Micro, 3 for Quick)] |

## Compression Settings

| Setting | Value |
|---------|-------|
| **skip_known_threshold** | [ease > 2.5 AND correct_count >= 3] |
| **compress_lesson_threshold** | [pre_test_score >= 80%] |
| **light_socratic_threshold** | [pre_test_score >= 60%] |
| **velocity_fast** | [> 1.3x average] |
| **velocity_slow** | [< 0.7x average] |
| **velocity_struggling** | [< 0.5x average] |

## Synthesis Challenge Schedule

Weekly synthesis replaces Standard on every 5th session:
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

## Session Variety (C4) — Rotation

For Deep Dive mode, occasionally swap portfolio exercise for:
- **Debate**: [argue both sides of a controversial topic in the space]
- **Case study**: [analyze a real company's strategic decision]
- **Deep-dive single concept**: [30-min exploration of one concept from multiple angles]
- **Reverse quiz**: [learner writes quiz questions, Claude answers (tests depth of understanding)]

Rotation: every 4th Deep session, use a variety format instead of standard portfolio exercise.

## Mastery Gate Configuration

| Field | Value |
|-------|-------|
| **mastery_gate_enabled** | true |
| **gate_modes** | Standard, Deep, Synthesis, Quick |
| **quick_mode_questions** | 5 |
| **standard_mode_questions** | 10 |
| **escape_valve_attempts** | 2 |
| **recovery_questions_per_day** | 2 |

Thresholds are read from the `Mastery Thresholds` table in this config.

## Articulation Scoring

| Setting | Value |
|---------|-------|
| **enabled** | true |
| **progressive_difficulty** | true |
| **rewrite_threshold** | 3 |
| **word_count_tracking** | true |
| **audience_tags** | VC, hiring_manager, engineer, general |
