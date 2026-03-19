# Curriculum Configuration: Financial Modeling

> This file configures the Adaptive Learning Engine for the Financial Modeling curriculum.
> The engine reads this config at session start.

## Curriculum Identity

| Field | Value |
|-------|-------|
| **curriculum_name** | Financial Modeling |
| **curriculum_dir** | [YOUR PATH, e.g., "career/financial-modeling/"] |
| **curriculum_file** | CURRICULUM.md |
| **state_file** | SESSION-STATE.md |
| **progress_file** | progress.md |
| **portfolio_dir** | portfolio/ |
| **communities_file** | COMMUNITIES.md |
| **research_reference** | RESEARCH-REFERENCE.md |
| **target_sessions** | ~20 (flexible -- depends on concept cap splits) |

## Learner Bridges

Connect new concepts to the learner's existing knowledge. The engine uses these as Socratic entry points during lessons.

- **Business operations**: Managed P&Ls, budgets, or business units -- can relate revenue/cost concepts to real operational experience
- **Spreadsheet skills**: Comfortable with Excel/Google Sheets formulas, pivot tables, and data manipulation -- can focus on financial logic rather than tool mechanics
- **Basic accounting**: Understands debits/credits, accrual vs cash basis, and chart of accounts at a functional level
- **Investing experience**: Familiar with stock markets, basic valuation concepts (P/E ratios, market cap) from personal investing

## Exercise Types (Portfolio Artifacts)

Every drill produces a real artifact the learner can use. Rotate through these formats:

- Financial model (spreadsheet with assumptions page, 3-statement integration, scenarios)
- Investment memo (2-5 page written analysis with thesis, financials, risks, recommendation)
- Pitch deck slides (3-5 slides summarizing a valuation or investment thesis)
- Peer comparison table (comps table with multiples, growth rates, margins across 5+ companies)
- Sensitivity analysis (2-variable data table or tornado chart showing key driver impact)
- Teaching script (explain a concept like WACC or DCF to someone with zero finance background)

## Mastery Thresholds

| Phase | Threshold | When |
|-------|-----------|------|
| Phase 1 (Foundations) | 7/10 | Sessions 1-5 |
| Phase 2+ (Technical Depth, Applied, Portfolio) | 8/10 | Sessions 6+ |

Mastery gates use these thresholds. Below threshold -> 10-min remediation -> re-test. Fail twice -> advance with a "weak" flag (the engine never blocks indefinitely).

## Synthesis Challenge Schedule

Weekly synthesis replaces interleaved practice + portfolio exercise on every 5th session:
- Session 5: Week 1 synthesis (company profile)
- Session 10: Week 2 synthesis (3-statement model)
- Session 15: Week 3 synthesis (full valuation)
- Session 20: Week 4 synthesis (investment memo capstone)

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
- Quantify everything: margins, multiples, growth rates, dollar amounts
- Zero tolerance for hallucinations -- say "unsure" if unsure about specific financial data
- Use real company examples whenever possible, not hypothetical "Company A"
- Suggest 2-3 follow-up questions after each session

## Community Engagement Phases

| Phase | Approach |
|-------|----------|
| Phase 1-2 | Lurk: join r/financialmodelling, Wall Street Oasis, Fintwit; observe what gets discussed |
| Phase 3 | Narrow: pick 2-3 communities, start sharing your analyses for feedback |
| Phase 4+ | Contribute: post original models/memos, connect with professionals |
