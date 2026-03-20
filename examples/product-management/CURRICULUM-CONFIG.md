# Curriculum Configuration: Product Management

> This file configures the Adaptive Learning Engine for the Product Management curriculum.
> The engine reads this config at session start.

## Curriculum Identity

| Field | Value |
|-------|-------|
| **curriculum_name** | Product Management |
| **curriculum_dir** | [YOUR PATH, e.g., "career/product-management/"] |
| **curriculum_file** | CURRICULUM.md |
| **state_file** | SESSION-STATE.md |
| **progress_file** | progress.md |
| **portfolio_dir** | portfolio/ |
| **communities_file** | COMMUNITIES.md |
| **research_reference** | RESEARCH-REFERENCE.md |
| **target_sessions** | ~30 (flexible -- depends on concept cap splits) |

## Learner Bridges

Connect new concepts to the learner's existing knowledge. The engine uses these as Socratic entry points during lessons.

- **Engineering background**: Built and shipped software products -- understands technical tradeoffs, system design, and engineering constraints firsthand
- **System design**: Designed distributed systems, APIs, and data pipelines -- can relate architecture decisions to product requirements
- **Data analysis**: Comfortable with SQL, analytics dashboards, and interpreting metrics -- can focus on product framing rather than data mechanics
- **Agile/Scrum experience**: Worked in sprints, participated in stand-ups and retros -- understands the ceremonies from the engineering side

## Learner Profile

| Field | Value |
|-------|-------|
| **age_group** | Adult (18+) |
| **experience_level** | Beginner |
| **domain_expertise** | Software engineering background, understands technical systems but new to product strategy |
| **persona** | Adult Beginner |

## Learning Objective

| Field | Value |
|-------|-------|
| **primary_goal** | Career/Job Prep |
| **secondary_goals** | — |
| **goal_weights** | career: 1.0 |
| **career_target** | Transition from engineering to PM role |
| **perspective_lenses** | ["interview readiness", "PM frameworks", "stakeholder communication", "product strategy"] |
| **objective_statement** | I'm learning product management so I can transition from engineering to a PM role at a tech company |

## Exercise Types (Portfolio Artifacts)

Every drill produces a real artifact the learner can use. Rotate through these formats:

- PRD draft (2-3 page product requirements document with all standard sections)
- Roadmap slide (now/next/later format with prioritization rationale)
- Metrics dashboard design (North Star + supporting KPIs + guardrails, with layout sketch)
- Stakeholder email (1-paragraph executive update, launch brief, or decision request)
- Product teardown (2-page analysis of an existing product's strategy, metrics, and improvement opportunities)
- Interview answer script (structured STAR-format answer or product sense framework walkthrough)

## Mastery Thresholds

| Phase | Threshold | When |
|-------|-----------|------|
| Phase 1 (Foundations) | 7/10 | Sessions 1-10 |
| Phase 2+ (Technical PM, Applied, Portfolio) | 8/10 | Sessions 11+ |

Mastery gates use these thresholds. Below threshold -> 10-min remediation -> re-test. Fail twice -> advance with a "weak" flag (the engine never blocks indefinitely).

## Synthesis Challenge Schedule

Weekly synthesis replaces interleaved practice + portfolio exercise on every 5th session:
- Session 5: Week 1 synthesis (product strategy doc)
- Session 10: Week 2 synthesis (full strategy document)
- Session 15: Week 3 synthesis (PRD + stakeholder sim)
- Session 20: Week 4 synthesis (PRD + roadmap package)
- Session 25: Week 5 synthesis (build project presentation)
- Session 30: Week 6 synthesis (full mock interview loop)

## Flex Session Defaults

| Parameter | Value |
|-----------|-------|
| **default_mode** | Standard (~60 min) |
| **micro_available** | true |
| **quick_available** | true |
| **deep_available** | true |
| **synthesis_interval** | 5 sessions |

## Compression Settings

| Parameter | Value |
|-----------|-------|
| **max_concepts_per_session** | 7 |
| **multi_session_split** | true (auto-split days with >7 concepts) |
| **acceleration_enabled** | true (skip basics if pre-test shows mastery) |

## Tone & Style

- Practical, framework-driven, concise
- Use real product examples (Slack, Notion, Spotify, Figma) rather than hypotheticals
- Challenge assumptions: "Why that metric?" "What would you deprioritize?"
- Zero tolerance for hallucinations -- say "unsure" if unsure
- Suggest 2-3 follow-up questions or practice prompts after each session

## Community Engagement Phases

| Phase | Approach |
|-------|----------|
| Phase 1-2 | Lurk: join Mind the Product, Lenny's Newsletter, r/ProductManagement; note recurring themes |
| Phase 3 | Narrow: pick 2-3 communities, share your product teardowns and PRDs for feedback |
| Phase 4+ | Contribute: post original analyses, answer questions, connect with practicing PMs |
