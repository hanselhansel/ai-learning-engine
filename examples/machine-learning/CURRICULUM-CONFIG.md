# Curriculum Configuration: Machine Learning

> This file configures the Adaptive Learning Engine for the Machine Learning curriculum.
> The engine reads this config at session start.

## Curriculum Identity

| Field | Value |
|-------|-------|
| **curriculum_name** | Machine Learning |
| **curriculum_dir** | [YOUR PATH, e.g., "career/machine-learning/"] |
| **curriculum_file** | CURRICULUM.md |
| **state_file** | SESSION-STATE.md |
| **progress_file** | progress.md |
| **portfolio_dir** | portfolio/ |
| **communities_file** | COMMUNITIES.md |
| **research_reference** | RESEARCH-REFERENCE.md |
| **target_sessions** | ~40 (flexible -- depends on concept cap splits) |

## Learner Bridges

Connect new concepts to the learner's existing knowledge. The engine uses these as Socratic entry points during lessons.

- **Programming (Python)**: Fluent in Python, data structures, algorithms -- can focus on ML concepts rather than language mechanics
- **Software engineering**: Built production systems with CI/CD, testing, monitoring -- can relate ML infrastructure to familiar patterns (model serving = microservice, experiment tracking = version control)
- **System design**: Designed distributed systems, databases, APIs -- can map ML system components to known architectural patterns
- **Math (calculus)**: Comfortable with derivatives and chain rule -- can engage with backpropagation and gradient descent mathematically, not just conceptually

## Exercise Types (Portfolio Artifacts)

Every drill produces a real artifact the learner can use. Rotate through these formats:

- Jupyter notebook (end-to-end analysis: EDA, modeling, evaluation, with clear markdown documentation)
- System design diagram (architecture for an ML system with data flow, components, and serving strategy)
- Paper summary (1-page summary of an ML paper: key contribution, method, results, limitations)
- Kaggle submission (competition entry with documented approach, feature engineering, and results)
- Blog post outline (structured technical deep-dive explaining an ML concept for a developer audience)
- Implementation from scratch (algorithm coded in NumPy without ML libraries, with unit tests)

## Mastery Thresholds

| Phase | Threshold | When |
|-------|-----------|------|
| Phase 1 (Foundations) | 7/10 | Sessions 1-10 |
| Phase 2+ (Deep Learning, Applied, Portfolio) | 8/10 | Sessions 11+ |

Mastery gates use these thresholds. Below threshold -> 10-min remediation -> re-test. Fail twice -> advance with a "weak" flag (the engine never blocks indefinitely).

## Synthesis Challenge Schedule

Weekly synthesis replaces interleaved practice + portfolio exercise on every 5th session:
- Session 5: Week 1 synthesis (classification project)
- Session 10: Week 2 synthesis (end-to-end ML project)
- Session 15: Week 3 synthesis (transformer implementation)
- Session 20: Week 4 synthesis (architecture decision guide)
- Session 25: Week 5 synthesis (ML pipeline)
- Session 30: Week 6 synthesis (system design document)
- Session 35: Week 7 synthesis (Kaggle/paper project)
- Session 40: Week 8 synthesis (mock interview loop)

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

- Technical, precise, code-first
- Show math when it builds intuition (not for its own sake)
- Use real datasets (Kaggle, HuggingFace) and real papers (arXiv links)
- Zero tolerance for hallucinations -- say "unsure" if unsure about model performance claims or paper details
- Suggest 2-3 coding exercises or papers to explore after each session

## Community Engagement Phases

| Phase | Approach |
|-------|----------|
| Phase 1-2 | Lurk: join Kaggle, r/MachineLearning, ML Twitter/X, Papers With Code; observe what gets discussed |
| Phase 3 | Narrow: pick 2-3 communities, share notebooks and project repos for feedback |
| Phase 4+ | Contribute: publish Kaggle notebooks, write blog posts, answer questions on Stack Overflow/ML forums |
