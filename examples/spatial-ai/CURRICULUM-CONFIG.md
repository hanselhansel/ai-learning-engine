# Curriculum Configuration: Spatial AI & Embodied Intelligence

> This file configures the Adaptive Learning Engine for the Spatial AI curriculum.
> The engine reads this config at session start.
> NOTE: This is the GENERIC gallery version. Fork and customize for your own background.

## Curriculum Identity

| Field | Value |
|-------|-------|
| **curriculum_name** | Spatial AI, World Models & Embodied Intelligence |
| **curriculum_dir** | [YOUR PATH, e.g., "career/spatial-ai-curriculum/"] |
| **curriculum_file** | CURRICULUM.md |
| **state_file** | SESSION-STATE.md |
| **progress_file** | progress.md |
| **portfolio_dir** | portfolio/ |
| **communities_file** | COMMUNITIES.md |
| **research_reference** | RESEARCH-REFERENCE.md |
| **target_sessions** | ~50 (flexible -- depends on concept cap splits) |

## Learner Bridges

Connect new concepts to the learner's existing knowledge. The engine uses these as Socratic entry points during lessons.

- **AI/ML background**: Familiar with LLMs, foundation models, transformers, and fine-tuning -- can relate spatial AI concepts to known NLP/vision patterns (world models as "next-token prediction for physics")
- **Software engineering**: Built production systems, APIs, and data pipelines -- can map robot software stacks to familiar architectures (perception = input pipeline, planning = orchestration, control = execution layer)
- **Business analysis**: Understands market sizing, competitive dynamics, and investment frameworks -- can evaluate robotics companies and business models with existing analytical tools
- **General technical literacy**: Comfortable reading papers, parsing technical blog posts, and understanding system diagrams -- can engage with research-level material without needing simplified versions

## Learner Profile

| Field | Value |
|-------|-------|
| **age_group** | Adult (18+) |
| **experience_level** | Professional |
| **domain_expertise** | AI marketing agency operator, multi-agent Claude systems, investing frameworks (FCF, EV/EBITDA, Rule-of-40) |
| **persona** | Professional |

## Learning Objective

| Field | Value |
|-------|-------|
| **primary_goal** | Career/Job Prep |
| **secondary_goals** | Investment/Business |
| **goal_weights** | career: 0.6, investment: 0.4 |
| **career_target** | Get hired by a spatial AI company in SF |
| **perspective_lenses** | ["interview readiness", "company landscape", "investment/valuation", "networking angles", "business strategy"] |
| **objective_statement** | I'm learning spatial AI so I can get hired by a spatial AI company in SF, combining business strategy with technical understanding |

## Exercise Types (Portfolio Artifacts)

Every drill produces a real artifact the learner can use. Rotate through these formats:

- Market analysis (1-2 page analysis of a company, sector, or technology with competitive positioning and thesis)
- Technical comparison (structured table comparing 3+ approaches, architectures, or companies on defined criteria)
- Investor thesis (1-page bull/bear case for a company or sector with quantified market sizing and risk assessment)
- Blog post draft (800-1200 word structured deep-dive on a spatial AI topic for a technical audience)
- System architecture diagram (visual diagram + 1-page description of how a robot/AI system's components interact)
- Teaching script (explain a concept like world models, VLAs, or sim-to-real to someone with zero robotics background)

## Mastery Thresholds

| Phase | Threshold | When |
|-------|-----------|------|
| Phase 1 (Foundations) | 7/10 | Sessions 1-10 |
| Phase 2+ (Market Intel, Build, Networking) | 8/10 | Sessions 11+ |

Mastery gates use these thresholds. Below threshold -> 10-min remediation -> re-test. Fail twice -> advance with a "weak" flag (the engine never blocks indefinitely).

## Synthesis Challenge Schedule

Weekly synthesis replaces interleaved practice + portfolio exercise on every 5th session:
- Session 5: Week 1 synthesis (terminology + landscape overview)
- Session 10: Week 2 synthesis (technical literacy project)
- Session 15: Week 3 synthesis (business model analysis)
- Session 20: Week 4 synthesis (product/GTM analysis)
- Session 25: Week 5 synthesis (build project kickoff)
- Session 30: Week 6 synthesis (build project midpoint review)
- Session 35: Week 7 synthesis (build project completion)
- Session 40: Week 8 synthesis (outreach + narrative)
- Session 45: Week 9 synthesis (interview prep)
- Session 50: Week 10 synthesis (immersion plan)

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

- Direct, quantitative, zero-fluff
- Use real company names, real funding amounts, real product names -- no generic placeholders
- Benchmark claims against verifiable data (funding rounds from Crunchbase, valuations from press, metrics from papers)
- Zero tolerance for hallucinations -- say "unsure" if unsure about funding amounts, company details, or technical claims
- Suggest 2-3 follow-up questions or areas to explore after each session
- Balance technical depth with business/market context -- this curriculum serves both builders and investors

## Community Engagement Phases

| Phase | Approach |
|-------|----------|
| Phase 1-2 | Lurk: join robotics Discord servers, r/robotics, Robotics Twitter/X, The Robot Report newsletter; observe who posts valuable content |
| Phase 3 | Narrow: pick 3-4 communities based on SWOT and interests, start with replies and questions, share build project for feedback |
| Phase 4+ | Contribute: post original analyses, attend meetups (Cerebral Valley, SF robotics meetups), convert online connections to IRL meetings |
