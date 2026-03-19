# Financial Modeling: Learning Curriculum

**Owner:** [Your Name]
**Goal:** Build professional-grade financial models and perform company valuations
**Timeline:** 4 weeks, ~2-3 hours/day
**Start Date:** TBD
**Created:** 2026-03-19

---

## TLDR

This curriculum takes you from reading financial statements to building full 3-statement models and DCF valuations in 20 sessions. Four phases: Foundations (accounting & ratios), Technical Depth (revenue/cost/capital modeling), Applied Valuation (DCF, comps, LBO), and Portfolio (sector models, scenarios, interview prep). By the end you'll have a complete investment memo with a working model.

---

## How This Curriculum Works

### Daily Session Format (2-3 hours)

| Block | Duration | What |
|-------|----------|------|
| **Learn** | 45-60 min | Read assigned material, then discuss with Claude |
| **Drill** | 20 min | Terminology quiz, ratio calculation, or concept check |
| **Build** | 60-90 min | Hands-on spreadsheet modeling or memo writing |
| **Reflect** | 10 min | Log what you learned, update your "explain it to a CFO" notes |

### How to Use with Claude

Type **"let's learn"** to start. Claude auto-resumes from `SESSION-STATE.md`. Type **"done learning"** to end early.

### Assessment System

| Assessment | When | Format | Pass Threshold |
|-----------|------|--------|---------------|
| **Phase 1 Gate** | End of Week 1 | 20 term quiz + explain ROIC vs ROE | 80% quiz, 4/5 explain |
| **Phase 2 Gate** | End of Week 2 | Build a 3-statement model from scratch | Model balances, 4/5 review |
| **Phase 3 Gate** | End of Week 3 | Full DCF + comps valuation defense | 4/5 defense score |
| **Phase 4 Gate** | End of Week 4 | Investment memo + model presentation | Pass mock interview |

### Folder Structure

```
financial-modeling/
+-- CURRICULUM.md
+-- CURRICULUM-CONFIG.md
+-- SESSION-STATE.md
+-- progress.md
+-- assessments/
+-- build-project/
+-- sessions/
```

---

## Phase 1: Foundations (Week 1, Days 1-5)

**Objective:** Read, interpret, and connect the three financial statements. Calculate and interpret key ratios.

### Day 1: Financial Statements 101

**Core question:** What are the three financial statements and how do they connect?

| Topic | Details |
|-------|---------|
| Income statement | Revenue, COGS, gross profit, operating expenses, EBIT, net income |
| Balance sheet | Assets = Liabilities + Equity, current vs non-current |
| Cash flow statement | Operating, investing, financing activities |
| The linkages | Net income flows to retained earnings; D&A adds back to cash flow; CapEx on cash flow creates PP&E on balance sheet |

**Reading:**
- Rosenbaum & Pearl, *Investment Banking* (2020), Chapter 2: Accounting Overview
- Damodaran, *Investment Valuation*, Chapter 3: Understanding Financial Statements

**Exercise:** Download Apple's (AAPL) latest 10-K. Trace $1 of revenue through all three statements to cash on the balance sheet.

**Bridge to your experience:** If you've ever managed a P&L or business budget, the income statement is your territory. The balance sheet is the snapshot; the cash flow statement is the movie.

---

### Day 2: Reading Real Financial Statements

**Core question:** How do you read a 10-K like an analyst, not an accountant?

| Topic | Details |
|-------|---------|
| SEC filings (10-K, 10-Q, 8-K) | Annual report, quarterly, material events |
| MD&A section | Management's narrative, where they hide the real story |
| Revenue recognition | ASC 606, when revenue actually counts |
| Segment reporting | How companies break down business units |
| Footnotes that matter | Debt maturities, lease obligations, stock comp |

**Reading:**
- Microsoft (MSFT) FY2025 10-K, MD&A section
- McKinsey, *Valuation* (7th ed), Chapter 7: Reorganizing Financial Statements

**Exercise:** Read Microsoft's 10-K MD&A. Identify 3 things management is optimistic about and 2 risks they're burying in the footnotes. Write a 1-page analyst note.

---

### Day 3: Key Ratios & Metrics

**Core question:** Which ratios actually matter for investment decisions?

| Category | Ratio | Formula | What It Tells You |
|----------|-------|---------|-------------------|
| Profitability | Gross margin | Gross Profit / Revenue | Pricing power, cost structure |
| Profitability | EBITDA margin | EBITDA / Revenue | Operating efficiency before capital allocation |
| Profitability | ROE | Net Income / Equity | Returns to shareholders |
| Profitability | ROIC | NOPAT / Invested Capital | True business returns, ignores capital structure |
| Efficiency | Asset turnover | Revenue / Total Assets | How hard assets are working |
| Efficiency | Days sales outstanding | (AR / Revenue) x 365 | How fast customers pay |
| Leverage | Debt/EBITDA | Total Debt / EBITDA | Leverage capacity |
| Growth | Revenue CAGR | (End/Start)^(1/n) - 1 | Compound growth rate |

**Reading:**
- Damodaran, *The Little Book of Valuation*, Chapters 3-4
- Greenwald, *Value Investing* (2nd ed), Chapter 4: Earnings Power Value

**Exercise:** Calculate all 8 ratios for Costco (COST) and Walmart (WMT) using their latest 10-K. Which is a better business? Write a 1-paragraph verdict.

---

### Day 4: Time Value of Money & Discounting

**Core question:** Why is $1 today worth more than $1 tomorrow, and how does this drive all of valuation?

| Topic | Details |
|-------|---------|
| Present value | PV = FV / (1 + r)^n |
| Discount rate | Risk-free rate + risk premium |
| NPV (net present value) | Sum of discounted future cash flows minus investment |
| IRR (internal rate of return) | Discount rate that makes NPV = 0 |
| Perpetuity & growing perpetuity | PV = CF/r and PV = CF/(r-g) |
| WACC (weighted average cost of capital) | Blended cost of debt and equity |

**Reading:**
- Brealey, Myers & Allen, *Principles of Corporate Finance*, Chapter 2-3
- Damodaran's online lecture: "Time Value of Money" (YouTube, NYU Stern)

**Exercise:** A startup offers you $500K in 3 years or $350K today. Risk-free rate is 4.5%, but you estimate the startup's risk premium at 15%. Which do you take? Show your math.

---

### Day 5: Synthesis - Company Profile

**Core question:** Can you combine everything from this week into a coherent company analysis?

| Topic | Details |
|-------|---------|
| Company profile template | Business description, competitive position, financial summary |
| DuPont analysis | Decompose ROE into margin x turnover x leverage |
| Quality of earnings | Recurring vs one-time, cash vs accrual |
| Red flags checklist | Declining margins, rising DSO, growing goodwill, management turnover |

**Exercise:** Build a complete 2-page company profile for Chipotle (CMG): business description, 3-year financial summary table, DuPont decomposition, key ratios, 3 bull points, 3 bear points. This is your first portfolio artifact.

---

## Phase 2: Technical Depth (Week 2, Days 6-10)

**Objective:** Build a working 3-statement financial model from scratch. Understand revenue drivers, cost structures, working capital, and debt.

### Day 6: Revenue Modeling

**Core question:** How do you forecast revenue with defensible assumptions?

| Topic | Details |
|-------|---------|
| Top-down vs bottom-up | TAM/SAM/SOM vs unit x price |
| Revenue drivers | Volume, price, mix, market share |
| Scenario analysis | Bull, base, bear cases with probability weighting |
| Sensitivity tables | Data tables varying 2 key assumptions |
| Growth decay curves | High growth doesn't last forever |

**Reading:**
- Rosenbaum & Pearl, *Investment Banking*, Chapter 3: Building a Financial Model (revenue section)

**Exercise:** Build a revenue model for Shopify (SHOP) with 3 scenarios: bull ($12B rev by 2028), base ($9B), bear ($7B). Define 3 key drivers and build a sensitivity table around them.

---

### Day 7: Cost Structure Modeling

**Core question:** How do you model costs, and what is operating leverage?

| Topic | Details |
|-------|---------|
| Fixed vs variable costs | Rent/salaries vs COGS/commissions |
| Operating leverage | High fixed costs = profits amplify with revenue growth |
| Step-function costs | Costs that jump at capacity thresholds (new warehouse, new team) |
| Margin expansion modeling | How margins change as revenue scales |
| Stock-based compensation | Real cost or ignore it? (Always real, despite "adjusted" EBITDA) |

**Exercise:** Model the cost structure for a SaaS company (use Datadog, DDOG, as a template). Show how gross margin expands from 75% to 82% as revenue doubles. Calculate the operating leverage ratio.

---

### Day 8: Working Capital & Cash Conversion

**Core question:** Why can a profitable company run out of cash?

| Topic | Details |
|-------|---------|
| Working capital components | Accounts receivable, inventory, accounts payable |
| Cash conversion cycle | DSO + DIO - DPO |
| Working capital as % of revenue | The modeling convention |
| Negative working capital | Amazon, Costco: get paid before paying suppliers |
| Seasonal effects | Retailers have massive Q4 inventory builds |

**Exercise:** Calculate the cash conversion cycle for Amazon (AMZN) vs a traditional retailer like Macy's (M). Explain why Amazon's model is superior in a 1-paragraph memo.

---

### Day 9: Debt & Capital Structure

**Core question:** How does debt create value (and risk)?

| Topic | Details |
|-------|---------|
| Cost of debt vs cost of equity | Debt is cheaper (tax shield, seniority) |
| Debt schedule modeling | Revolving credit, term loans, bonds, maturities |
| Leverage ratios | Debt/EBITDA, interest coverage, fixed charge coverage |
| Optimal capital structure | Modigliani-Miller theory vs real-world tradeoffs |
| Credit ratings | Investment grade vs high yield, what triggers downgrades |

**Reading:**
- Rosenbaum & Pearl, *Investment Banking*, Chapter 4: Capital Structure

**Exercise:** Build a debt schedule for a company with $2B in total debt across 3 tranches (revolver, term loan A, high-yield notes). Model mandatory amortization and optional prepayment.

---

### Day 10: Synthesis - Complete 3-Statement Model

**Core question:** Can you build a fully integrated 3-statement model?

| Topic | Details |
|-------|---------|
| Model architecture | Income statement drives balance sheet drives cash flow |
| Circular references | Interest expense depends on debt depends on cash flow depends on interest |
| Balancing the balance sheet | Cash or revolver as the plug |
| Error checking | Assets = L + E, cash flow reconciliation |
| Model best practices | Color coding (blue = input, black = formula), clear assumption blocks |

**Exercise:** Build a complete 3-statement model for Starbucks (SBUX) with 3-year projections. The model must balance, have a clear assumptions page, and include scenarios. This is your Phase 2 portfolio artifact.

---

## Phase 3: Applied Valuation (Week 3, Days 11-15)

**Objective:** Apply DCF, comparable company analysis, precedent transactions, and LBO to value a real company.

### Day 11: DCF Valuation

**Core question:** How do you value a company using discounted cash flows?

| Topic | Details |
|-------|---------|
| Unlevered free cash flow | EBIT(1-t) + D&A - CapEx - change in NWC |
| WACC calculation | Cost of equity (CAPM) + after-tax cost of debt, weighted |
| Terminal value | Gordon growth model vs exit multiple method |
| Sensitivity analysis | WACC vs terminal growth rate matrix |
| Football field chart | Visualizing the valuation range |

**Reading:**
- Damodaran, *Investment Valuation*, Chapters 12-13
- McKinsey, *Valuation* (7th ed), Chapter 8: Forecasting Performance

**Exercise:** Build a DCF for Nike (NKE). Calculate WACC, project 5 years of free cash flow, apply both terminal value methods, build a sensitivity table. What's your implied share price vs current market price?

---

### Day 12: Comparable Company Analysis

**Core question:** What is a company worth relative to its peers?

| Topic | Details |
|-------|---------|
| Selecting comparables | Business model, size, growth, margins, geography |
| Key multiples | EV/Revenue, EV/EBITDA, EV/EBIT, P/E, P/FCF |
| Calendarization | Aligning fiscal years across companies |
| Forward vs trailing | LTM vs NTM multiples |
| Applying the range | Mean, median, and where your target sits |

**Exercise:** Build a comps table for the athletic apparel industry: Nike (NKE), Adidas (ADDYY), Lululemon (LULU), On Holding (ONON), Deckers (DECK). Calculate EV/EBITDA, EV/Revenue, and P/E. What does the implied valuation range say about Nike?

---

### Day 13: Precedent Transactions

**Core question:** What have acquirers actually paid for similar companies?

| Topic | Details |
|-------|---------|
| Finding precedent transactions | Capital IQ, Bloomberg, SEC filings |
| Transaction premiums | Premium to undisturbed price (typically 20-40%) |
| Control premium vs synergies | Why acquirers pay more than public market value |
| Adjusting for market conditions | 2021 multiples vs 2024 multiples are different worlds |
| Limitations | Small sample sizes, unique deal dynamics |

**Reading:**
- Rosenbaum & Pearl, *Investment Banking*, Chapter 6: Precedent Transactions Analysis

**Exercise:** Research 5 recent acquisitions in consumer/retail (e.g., Tapestry/Capri, Albertsons/Kroger). Build a precedent transactions table with EV/EBITDA, EV/Revenue, and premium paid.

---

### Day 14: LBO Basics

**Core question:** How do private equity firms use leverage to generate returns?

| Topic | Details |
|-------|---------|
| LBO mechanics | Buy with debt, use cash flow to pay down, sell at exit |
| Sources & uses | Where the money comes from and where it goes |
| IRR and MOIC | Internal rate of return and multiple on invested capital |
| Debt paydown modeling | Mandatory amortization + cash sweep |
| Sensitivity | Entry multiple, exit multiple, leverage, growth |

**Reading:**
- Rosenbaum & Pearl, *Investment Banking*, Chapter 7: LBO Analysis

**Exercise:** Build a simple LBO model: acquire a company at 8x EBITDA with 5x leverage, hold for 5 years, exit at 8x. What IRR and MOIC does the PE firm earn? How does it change if exit multiple compresses to 6x?

---

### Day 15: Synthesis - Full Company Valuation

**Core question:** Can you triangulate a company's value using multiple methods?

| Topic | Details |
|-------|---------|
| Triangulation | DCF + comps + precedent transactions |
| Football field visualization | Range of values from each methodology |
| Key judgment calls | Which method to weight most and why |
| Sanity checks | Does the implied growth rate make sense? Implied margins? |

**Exercise:** Produce a complete valuation of Target (TGT) using DCF, comps (vs Walmart, Costco, Dollar General), and precedent transactions. Build a football field chart showing the range. Write a 1-page recommendation: buy, hold, or sell at current price.

---

## Phase 4: Portfolio (Week 4, Days 16-20)

**Objective:** Apply everything to specialized contexts. Prepare for interviews. Deliver a complete investment memo.

### Day 16: Sector-Specific Modeling

**Core question:** How do financial models differ by industry?

| Sector | Key Differences |
|--------|----------------|
| SaaS | ARR, net retention, CAC/LTV, Rule of 40, deferred revenue |
| Retail | Same-store sales, inventory turnover, square footage growth |
| Manufacturing | Capacity utilization, raw material costs, CapEx intensity |
| Banks | NIM, loan loss provisions, book value, CET1 ratio |

**Exercise:** Build a SaaS revenue model for CrowdStrike (CRWD): ARR, net retention rate, new customer adds, expansion revenue, churn. Project 3 years and calculate Rule of 40.

---

### Day 17: Scenario Analysis & Monte Carlo

**Core question:** How do you quantify uncertainty in financial models?

| Topic | Details |
|-------|---------|
| Scenario analysis | Discrete scenarios (bull/base/bear) with probability weights |
| Sensitivity tables | 2-variable data tables in Excel |
| Monte Carlo simulation | Random sampling from probability distributions |
| Key risk factors | Revenue growth, margin, WACC, terminal growth |
| Presenting uncertainty | Ranges, confidence intervals, tornado charts |

**Exercise:** Take your Starbucks model from Day 10. Add Monte Carlo simulation (1,000 runs) varying revenue growth (+/- 3%), margins (+/- 2%), and WACC (+/- 1%). Plot the distribution of implied share prices.

---

### Day 18: Presentation & Storytelling with Numbers

**Core question:** How do you present financial analysis to decision-makers?

| Topic | Details |
|-------|---------|
| Slide structure | Situation, analysis, recommendation (pyramid principle) |
| Chart best practices | Less is more, one message per chart, label everything |
| Executive summary | The 1-pager that busy people actually read |
| Anticipating pushback | "What if you're wrong about X?" -- have the sensitivity ready |
| The "so what" test | Every slide must answer "so what does this mean?" |

**Reading:**
- Minto, *The Pyramid Principle*, Chapters 1-3
- Tufte, *The Visual Display of Quantitative Information*, Chapter 1

**Exercise:** Create a 5-slide investment recommendation deck for your Target (TGT) valuation. Slides: Executive Summary, Business Overview, Valuation Summary, Key Risks, Recommendation.

---

### Day 19: Interview Prep

**Core question:** How do you perform under pressure in a modeling test or case study?

| Interview Type | What to Expect | Prep Strategy |
|---------------|----------------|---------------|
| Modeling test | Build a model in 60-90 min from a case packet | Practice with timer, memorize formulas |
| Technical questions | "Walk me through a DCF," "What drives WACC?" | Rehearse 20 standard questions |
| Case study | "Should Company A acquire Company B?" | Framework: strategic rationale, valuation, financing, risks |
| Behavioral | "Tell me about a time you used data to make a decision" | STAR format with financial examples |

**Exercise:** Timed practice: Claude gives you a simplified case packet for a mock company. Build a DCF in 45 minutes. Then defend your assumptions for 15 minutes.

---

### Day 20: Final Project - Investment Memo

**Core question:** Can you produce a professional-quality investment memo?

| Component | Details |
|-----------|---------|
| Executive summary | 1-paragraph thesis with price target |
| Business description | What the company does, competitive moats |
| Industry analysis | TAM, growth drivers, competitive landscape |
| Financial analysis | Historical analysis, key ratios, DuPont decomposition |
| Projections | 3-5 year model with clear assumptions |
| Valuation | DCF + comps + precedent transactions |
| Risk factors | Top 5 risks with mitigation or scenario impact |
| Recommendation | Buy/hold/sell with conviction level |

**Exercise:** Write a complete 5-8 page investment memo on a company of your choice. Include the financial model as an appendix. This is your capstone portfolio artifact -- suitable for sharing with employers, interview panels, or investment clubs.

---

## Appendix: Key Resources

### Textbooks
1. Rosenbaum & Pearl, *Investment Banking* (3rd ed, 2020) -- the practitioner's bible
2. Damodaran, *Investment Valuation* (3rd ed) -- the academic standard
3. McKinsey, *Valuation* (7th ed) -- the consultant's perspective
4. Koller, Goedhart & Wessels, *Measuring and Managing the Value of Companies*

### Free Resources
1. Damodaran's NYU Stern lectures (YouTube) -- full MBA-level valuation course
2. Macabacus.com -- free model templates and technical guides
3. EDGAR / SEC.gov -- all US public company filings
4. Mergr.com -- precedent transaction database (limited free)

### Practice
1. Wall Street Prep self-study courses
2. Breaking Into Wall Street (BIWS) modeling courses
3. Corporate Finance Institute (CFI) -- free introductory courses

---

*Last updated: 2026-03-19*
