# Product Management: Learning Curriculum

**Owner:** [Your Name]
**Goal:** Transition from engineering to a Product Manager role at a top-tier tech company
**Timeline:** 6 weeks, ~2-3 hours/day
**Start Date:** TBD
**Created:** 2026-03-19

---

## TLDR

This curriculum takes an engineer through the full PM skill set in 30 sessions. Four phases: Foundations (frameworks, user research, strategy, metrics), Technical PM Skills (PRDs, prioritization, design, data-driven decisions), Applied (build a product from scratch, stakeholder management, GTM), and Portfolio & Interview (product sense, execution, analytical, and behavioral prep with mock interviews). You'll leave with a portfolio of PRDs, roadmaps, and interview-ready frameworks.

---

## How This Curriculum Works

### Daily Session Format (2-3 hours)

| Block | Duration | What |
|-------|----------|------|
| **Learn** | 45-60 min | Read assigned material, then discuss with Claude |
| **Drill** | 20 min | Framework application, concept quiz, or product teardown |
| **Build** | 60-90 min | PRD writing, roadmap design, or mock exercise |
| **Reflect** | 10 min | Log what you learned, update your "explain it to a CEO" notes |

### How to Use with Claude

Type **"let's learn"** to start. Claude auto-resumes from `SESSION-STATE.md`. Type **"done learning"** to end early.

### Assessment System

| Assessment | When | Format | Pass Threshold |
|-----------|------|--------|---------------|
| **Phase 1 Gate** | End of Week 2 | 20 term quiz + explain a prioritization decision | 80% quiz, 4/5 explain |
| **Phase 2 Gate** | End of Week 4 | PRD review + metrics dashboard defense | 4/5 on both |
| **Phase 3 Gate** | End of Week 5 | Product design presentation + GTM plan defense | 4/5 defense |
| **Phase 4 Gate** | End of Week 6 | Full mock interview (product sense + execution + analytical) | Pass 2/3 rounds |

### Folder Structure

```
product-management/
+-- CURRICULUM.md
+-- CURRICULUM-CONFIG.md
+-- SESSION-STATE.md
+-- progress.md
+-- assessments/
+-- build-project/
+-- sessions/
```

---

## Phase 1: Foundations (Weeks 1-2, Days 1-10)

**Objective:** Master the core PM frameworks, user research methods, strategy concepts, and metrics that every PM needs.

### Week 1: Frameworks & User Understanding

#### Day 1: What Product Managers Actually Do

**Core question:** What does a PM do all day, and how is it different from engineering?

| Topic | Details |
|-------|---------|
| The PM role | Vision, strategy, execution across engineering, design, business |
| PM archetypes | Technical PM, Growth PM, Platform PM, 0-to-1 PM |
| How PMs ship | Discovery, definition, delivery, iteration |
| PM vs engineering manager | Influence without authority vs direct management |
| The PM at different stages | Startup PM (generalist) vs big-tech PM (specialist) |

**Reading:**
- Cagan, *Inspired* (2nd ed), Chapters 1-5
- Lenny Rachitsky, "What distinguishes the top 1% of PMs" (newsletter)

**Exercise:** Shadow a PM for a day (or read 3 "day in the life" blog posts from PMs at Google, Stripe, and a startup). Write a 1-page summary of how the PM role maps to your engineering responsibilities.

**Bridge to your experience:** As an engineer, you've been on the receiving end of PRDs and sprint priorities. Now you're learning the other side: how those decisions get made.

---

#### Day 2: Jobs to Be Done (JTBD)

**Core question:** Why do customers "hire" products?

| Topic | Details |
|-------|---------|
| JTBD framework | Customers hire products to make progress in specific circumstances |
| Functional vs social vs emotional jobs | What they need done, how they want to be seen, how they want to feel |
| Switch interviews | Understanding the forces that drive switching behavior |
| Demand-side vs supply-side thinking | Start with the customer's struggle, not your feature list |

**Reading:**
- Christensen, *Competing Against Luck*, Chapters 1-3
- Intercom's JTBD playbook (free, intercom.com)

**Exercise:** Pick an app you switched to recently (e.g., Notion over Confluence, Linear over Jira). Apply JTBD: What was the struggling moment? What were the push/pull forces? Write a 1-page JTBD analysis.

---

#### Day 3: Prioritization Frameworks

**Core question:** You have 50 feature requests and can build 5. How do you choose?

| Framework | How It Works | Best For |
|-----------|-------------|----------|
| RICE | Reach x Impact x Confidence / Effort | Quantitative comparison across many ideas |
| MoSCoW | Must/Should/Could/Won't | Stakeholder alignment, scope negotiation |
| Kano Model | Basic, Performance, Delighter features | Understanding customer satisfaction drivers |
| ICE | Impact x Confidence x Ease | Quick scoring, early-stage products |
| Opportunity scoring | Importance vs satisfaction gap | Finding underserved needs |
| Cost of delay | Revenue/value lost by waiting | Time-sensitive decisions |

**Exercise:** Take a real product backlog (use Figma's public roadmap or Linear's changelog). Score the top 10 items using RICE. Then re-score with Kano. Do the rankings change? Write a 1-paragraph explanation of when each framework fails.

---

#### Day 4: User Research Methods

**Core question:** How do you learn what users need without just asking them?

| Method | When to Use | Sample Size | Effort |
|--------|-----------|-------------|--------|
| User interviews | Discovery, understanding motivations | 5-15 | Medium |
| Surveys | Quantifying attitudes at scale | 100-1000+ | Low |
| Usability testing | Validating designs, finding friction | 5-8 | Medium |
| Analytics/data mining | Understanding actual behavior | All users | Low (if instrumented) |
| A/B testing | Measuring impact of changes | 1000+ per variant | High |
| Diary studies | Understanding behavior over time | 10-20 | High |
| Card sorting | Information architecture decisions | 15-30 | Low |

**Reading:**
- Torres, *Continuous Discovery Habits*, Chapters 4-7
- Steve Portigal, *Interviewing Users*, Chapters 1-4

**Exercise:** Write an interview guide (10 questions) for understanding why users abandon a SaaS product during onboarding. Include 3 warm-up questions, 5 core questions, and 2 follow-ups. No leading questions.

---

#### Day 5: Product Strategy (Synthesis)

**Core question:** How do vision, strategy, and roadmap connect?

| Level | Timeframe | Example (Spotify) |
|-------|-----------|-------------------|
| Vision | 3-5 years | "Audio for everyone" |
| Strategy | 1-2 years | Expand to podcasts, audiobooks, creator tools |
| Roadmap | Quarters | Q1: Launch audiobook marketplace, Q2: Creator analytics |
| Sprint plan | Weeks | This sprint: audiobook recommendation algorithm |

| Concept | Details |
|---------|---------|
| North Star metric | The single metric that captures value delivery (Spotify: time spent listening) |
| Strategy vs roadmap | Strategy is the approach; roadmap is the plan |
| Roadmap types | Feature-based (bad), outcome-based (good), now/next/later (practical) |

**Exercise:** Pick a product you use daily. Reverse-engineer its strategy: What's the vision? North Star metric? Current strategic bets? Write a 1-page strategy doc as if you were the PM.

---

### Week 2: Market, Metrics & Business Context

#### Day 6: Market Analysis & Competitive Positioning

**Core question:** How do you size a market and find your competitive edge?

| Topic | Details |
|-------|---------|
| TAM/SAM/SOM | Total, Serviceable, Obtainable market sizing |
| Top-down vs bottom-up sizing | Industry reports vs unit economics extrapolation |
| Competitive analysis frameworks | Porter's Five Forces, competitive feature matrices |
| Positioning | Category creation vs category entry (April Dunford's Obviously Awesome) |

**Exercise:** Size the market for an AI-powered code review tool. Use both top-down (developer market size) and bottom-up (# of dev teams x willingness to pay). Build a competitive matrix against GitHub Copilot, Cursor, and Sourcegraph.

---

#### Day 7: Metrics That Matter

**Core question:** Which numbers should a PM obsess over?

| Metric Category | Examples | What It Tells You |
|----------------|----------|-------------------|
| Acquisition | CAC, signup rate, channel mix | How efficiently you get users |
| Activation | Time to value, onboarding completion | First-experience quality |
| Engagement | DAU/MAU, session frequency, feature adoption | Product-market fit strength |
| Retention | D1/D7/D30 retention, churn rate, cohort curves | Long-term value |
| Monetization | ARPU, LTV, conversion rate, expansion revenue | Business sustainability |
| Referral | NPS, viral coefficient, organic share rate | Growth flywheel |

**Reading:**
- Croll & Yoskovitz, *Lean Analytics*, Chapters 4-6
- Amplitude's "North Star Playbook" (free, amplitude.com)

**Exercise:** Design a metrics dashboard for Notion. Define the North Star metric, 5 supporting KPIs, and 3 guardrail metrics. Sketch the dashboard layout and explain what each metric tells the PM team.

---

#### Day 8: Product Analytics & Experimentation

**Core question:** How do you use data to make product decisions?

| Topic | Details |
|-------|---------|
| Funnel analysis | Where users drop off in a flow |
| Cohort analysis | Comparing user groups over time |
| A/B testing mechanics | Sample size, statistical significance, MDE, runtime |
| Common pitfalls | Peeking, novelty effects, Simpson's paradox |
| Qualitative + quantitative | Numbers tell you what; interviews tell you why |

**Exercise:** Design an A/B test for Slack: "Does adding an AI-generated summary at the top of channels increase DAU?" Define: hypothesis, success metric, guardrail metrics, sample size estimate, and minimum runtime.

---

#### Day 9: Business Models & Unit Economics

**Core question:** How does the product make money, and is it sustainable?

| Model | Examples | Key Metrics |
|-------|----------|-------------|
| SaaS subscription | Slack, Notion, Datadog | ARR, NRR, CAC payback |
| Freemium | Spotify, Dropbox | Free-to-paid conversion, ARPU |
| Marketplace | Airbnb, Uber | Take rate, liquidity, GMV |
| Advertising | Google, Meta | CPM, CPC, ad load, ARPU |
| Usage-based | AWS, Twilio, Snowflake | Consumption growth, net retention |
| Hardware + software | Apple, Peloton | ASP, attach rate, services revenue |

**Exercise:** Compare the unit economics of Slack (SaaS) vs Zoom (freemium/SaaS hybrid). Calculate CAC payback period, LTV/CAC ratio, and net revenue retention. Which business is healthier? Write a 1-page analysis.

---

#### Day 10: Synthesis - Product Strategy Document

**Core question:** Can you synthesize everything from Phase 1 into a coherent product strategy?

**Exercise:** Write a complete Product Strategy Document for a new product (choose one):
- AI writing assistant for legal professionals
- Developer productivity tool for remote teams
- Personal finance app for Gen Z

Include: Vision, target user (JTBD), market sizing, competitive positioning, North Star metric, key metrics, prioritized roadmap (now/next/later), and risks. 3-5 pages. This is your Phase 1 portfolio artifact.

---

## Phase 2: Technical PM Skills (Weeks 3-4, Days 11-20)

**Objective:** Master the day-to-day execution skills: PRDs, working with design and engineering, and data-driven decision making.

### Week 3: Writing & Working with Teams

#### Day 11: Writing PRDs and Specs

**Core question:** How do you write a document that aligns an entire team?

| Section | What to Include |
|---------|----------------|
| Problem statement | User pain point, business justification, data supporting urgency |
| Goals & success metrics | Measurable outcomes, not feature completions |
| User stories | As a [user], I want to [action], so that [outcome] |
| Scope | In scope, out of scope, future considerations |
| Design & UX | Wireframes, user flows, edge cases |
| Technical considerations | Dependencies, APIs, performance requirements, scale |
| Launch plan | Rollout stages, feature flags, monitoring |
| Open questions | Decisions still needed, stakeholder input required |

**Reading:**
- Lenny Rachitsky, "How to write a great PRD" (newsletter)
- Figma's PRD template (publicly shared)

**Exercise:** Write a PRD for "AI-powered search in Slack." Include all sections above. Make it 2-3 pages, concise but complete.

---

#### Day 12: Prioritization in Practice

**Core question:** How do you say no to your CEO, your biggest customer, and your eng lead in the same week?

| Topic | Details |
|-------|---------|
| Stakeholder mapping | Power vs interest grid |
| Saying no with data | "Here's what we'd need to deprioritize" |
| Technical debt negotiation | The 20% rule, paying interest vs principal |
| Roadmap communication | Different views for different audiences (board, eng, sales) |
| Feature creep prevention | Scope anchoring, "parking lot" technique |

**Exercise:** Scenario: You're PM for a B2B SaaS product. Your CEO wants a mobile app (6 months), your biggest customer wants SSO (2 months), and your eng lead wants to refactor the database (3 months). You have one engineering team. Write a 1-page decision memo recommending a sequence with reasoning.

---

#### Day 13: Working with Design

**Core question:** How do you collaborate with designers without micromanaging or abdicating?

| Topic | Details |
|-------|---------|
| Design thinking | Empathize, Define, Ideate, Prototype, Test |
| PM-designer collaboration | PM owns the "what" and "why," design owns the "how" |
| Giving design feedback | Critique the design against user goals, not personal taste |
| Wireframing basics | Low-fidelity vs high-fidelity, when each is appropriate |
| Design reviews | Structured critique format: what works, what doesn't, open questions |

**Exercise:** Take a feature you'd improve in an app you use daily (e.g., Spotify's queue, Gmail's compose). Sketch 3 low-fidelity wireframes showing different approaches. Write a brief explaining which you'd test first and why.

---

#### Day 14: Working with Engineering

**Core question:** How do you partner with engineers without being a project manager?

| Topic | Details |
|-------|---------|
| Sprint planning | Story points, velocity, capacity planning |
| Technical debt conversations | When to invest, how to quantify impact |
| Architecture decisions | PM's role: define constraints, not solutions |
| Engineering estimates | How to use them, why they're always wrong, padding strategies |
| Incident management | PM's role during outages and escalations |
| Build vs buy | Framework: core competency, speed to market, maintenance cost |

**Reading:**
- Cagan, *Empowered*, Chapters on product teams
- Will Larson, *An Elegant Puzzle*, Chapters on engineering management

**Exercise:** Write a technical brief for engineering: "We need to add real-time collaboration to our document editor." Define the user requirements, performance constraints (latency < 200ms), scale requirements (10K concurrent editors), and 3 open technical questions you want eng's input on.

---

#### Day 15: Data-Driven Decision Making (Synthesis)

**Core question:** When should you trust data vs intuition?

| Topic | Details |
|-------|---------|
| Cohort analysis deep dive | Build retention curves, identify "aha moment" |
| Funnel optimization | Identify biggest drop-off, estimate impact of fixing it |
| A/B test interpretation | Beyond p-values: practical significance, segmentation |
| When data misleads | Survivorship bias, correlation vs causation, Goodhart's law |
| Intuition-based decisions | When data doesn't exist (new markets, 0-to-1 products) |

**Exercise:** You're given this data for a SaaS product: 30-day retention is 25%, users who complete onboarding retain at 60%, but only 40% complete onboarding. Write a 1-page analysis: What's the opportunity? What would you prioritize? Design an experiment to validate your hypothesis.

---

### Week 4: Advanced Execution

#### Day 16: Platform & API Product Management

**Core question:** How is building a platform different from building a product?

| Topic | Details |
|-------|---------|
| Platform vs product | Two-sided value creation, developer experience matters |
| API design principles | RESTful, versioning, backwards compatibility, rate limiting |
| Developer experience | Documentation, SDKs, sandbox environments, error messages |
| Platform metrics | API calls, developer adoption, time to first call, churn |

**Exercise:** Design the API for a "smart calendar" platform. Define 5 core endpoints, the authentication model, rate limits, and write the developer quickstart guide (1 page).

---

#### Day 17: Growth & Experimentation

**Core question:** How do you systematically grow a product?

| Topic | Details |
|-------|---------|
| Growth loops | Viral, content, paid, sales-led loops |
| Growth models | Bottoms-up (Slack, Figma) vs top-down (Salesforce) vs PLG |
| Activation optimization | Finding and reinforcing the "aha moment" |
| Retention levers | Habit formation, switching costs, network effects |
| Growth experimentation | High-tempo testing, ICE scoring, learning velocity |

**Exercise:** Map the growth loop for Figma: How does one user lead to the next? Identify 3 interventions that could accelerate the loop. Estimate the impact of each using ICE scoring.

---

#### Day 18: Pricing & Monetization

**Core question:** How do you set prices and design packaging?

| Topic | Details |
|-------|---------|
| Value-based pricing | Price based on value delivered, not cost |
| Packaging tiers | Good/better/best, feature gating vs usage gating |
| Pricing psychology | Anchoring, decoy effect, round numbers |
| Usage-based pricing | Pros (aligns with value) vs cons (unpredictable bills) |
| Free tier strategy | Generous enough to hook, limited enough to convert |

**Exercise:** Redesign Notion's pricing page. Define 3 tiers, what goes in each, and the price points. Write a 1-page rationale for your packaging decisions.

---

#### Day 19: Stakeholder Communication

**Core question:** How do you keep everyone aligned without spending all day in meetings?

| Topic | Details |
|-------|---------|
| Status updates | Weekly snippets: shipped, in progress, blocked, next |
| Executive reviews | QPR format: goals, progress, learnings, asks |
| Launch communications | Internal launch brief, external announcement, support enablement |
| Difficult conversations | Killing a feature, missing a deadline, pivoting strategy |
| Written vs verbal | Amazon's 6-pager culture, when to write vs when to meet |

**Exercise:** Write 3 communications for the same product update (launching AI search in your product): (1) a 3-sentence Slack message to engineering, (2) a 1-paragraph email to the CEO, (3) a 1-page brief for the sales team. Notice how the message changes by audience.

---

#### Day 20: Synthesis - Full PRD + Roadmap

**Core question:** Can you produce a complete product definition package?

**Exercise:** Create a full product package for an AI feature in a product of your choice:
1. PRD (2-3 pages) with all sections from Day 11
2. Prioritized roadmap (now/next/later format)
3. Metrics dashboard design
4. Launch plan with rollout stages

This is your Phase 2 portfolio artifact.

---

## Phase 3: Applied (Week 5, Days 21-25)

**Objective:** Design a product from scratch. Apply every framework, tool, and skill from Phases 1-2 in an integrated build project.

### Day 21-22: Product Design from Scratch

**Exercise:** Design a new product end-to-end. Choose one:
- AI copilot for customer support teams
- Collaborative budgeting tool for small businesses
- Developer tool for API monitoring and debugging

Day 21: User research plan, JTBD analysis, market sizing, competitive positioning.
Day 22: Product vision, strategy, North Star metric, wireframes, PRD.

---

### Day 23: Stakeholder Management Simulation

**Exercise:** Claude plays 4 stakeholders (CEO, Head of Sales, Engineering Lead, Customer Success Lead). Each has a different priority. Run a simulated product review meeting: present your roadmap, handle objections, negotiate scope, and reach alignment. Write up the meeting notes and action items.

---

### Day 24: Go-to-Market Planning

**Core question:** How do you launch a product successfully?

| Topic | Details |
|-------|---------|
| Beta program design | User selection, feedback loops, success criteria |
| Launch tiers | Soft launch, limited GA, full GA |
| Sales enablement | Battle cards, demo scripts, objection handling |
| Marketing collaboration | Positioning, messaging, channels, timing |
| Success metrics | 30/60/90 day targets |

**Exercise:** Write a GTM plan for your Day 21-22 product. Include: beta program (who, how many, how long), launch sequence, sales enablement materials, and 90-day success metrics.

---

### Day 25: Synthesis - Product Presentation

**Exercise:** Create a 10-slide product review deck for your build project. Present it to Claude (playing the role of VP of Product). Defend your decisions for 15 minutes. Claude scores on: problem definition, strategy clarity, metric selection, prioritization rationale, and communication quality.

---

## Phase 4: Portfolio & Interview (Week 6, Days 26-30)

**Objective:** Prepare for PM interviews across all dimensions. Polish your portfolio. Practice until you're confident.

### Day 26: Product Sense Interview Prep

**Core question:** How do you design a product for a given user and use case under time pressure?

| Question Type | Example |
|--------------|---------|
| Design a product | "Design a parking app for a city" |
| Improve a product | "How would you improve Instagram for creators?" |
| New market entry | "Should Spotify launch a podcast creation tool?" |

**Framework:** User -> Pain point -> Solutions (3) -> Evaluate -> Recommend -> Metrics

**Exercise:** Practice 3 product sense questions with Claude as interviewer. 15 minutes each, then debrief.

---

### Day 27: Execution Interview Prep

| Question Type | Example |
|--------------|---------|
| Prioritization | "You have these 5 projects. How do you prioritize?" |
| Tradeoffs | "Ship fast with bugs or slow with quality?" |
| Debugging | "Feature adoption is 10%. Diagnose and fix." |
| Resource allocation | "You just lost 2 engineers. What changes?" |

**Exercise:** Practice 3 execution questions with Claude as interviewer.

---

### Day 28: Analytical / Metrics Interview Prep

| Question Type | Example |
|--------------|---------|
| Metric definition | "How would you measure success for YouTube Shorts?" |
| Root cause analysis | "Daily active users dropped 15%. Walk me through your investigation." |
| A/B test design | "Design an experiment to test a new checkout flow." |
| Goal setting | "Set Q1 goals for the Uber Eats delivery team." |

**Exercise:** Practice 3 analytical questions. Show your math and framework.

---

### Day 29: Leadership & Behavioral Prep

| Question Type | Example |
|--------------|---------|
| Influence | "Tell me about a time you convinced a skeptical stakeholder" |
| Failure | "Tell me about a product decision that didn't work out" |
| Cross-functional | "How do you resolve a disagreement between design and engineering?" |
| Why PM | "Why do you want to move from engineering to product?" |

**Exercise:** Prepare STAR-format answers for 5 behavioral questions. Record yourself answering and review.

---

### Day 30: Mock Interviews (Full Loop)

**Exercise:** Full mock interview with Claude simulating a PM interview loop:
1. Round 1 (30 min): Product Sense -- design a product
2. Round 2 (30 min): Execution -- prioritization and tradeoffs
3. Round 3 (30 min): Analytical -- metrics and experimentation
4. Debrief: Claude provides detailed feedback on each round with a hire/no-hire recommendation and specific improvement areas.

This is your Phase 4 capstone. Record your learnings in progress.md.

---

## Appendix: Key Resources

### Books
1. Cagan, *Inspired* (2nd ed) -- the PM bible
2. Torres, *Continuous Discovery Habits* -- modern product discovery
3. Cagan, *Empowered* -- product leadership
4. Christensen, *Competing Against Luck* -- JTBD framework
5. Croll & Yoskovitz, *Lean Analytics* -- metrics and analytics

### Free Resources
1. Lenny's Newsletter (lennysnewsletter.com) -- best PM newsletter
2. Reforge (reforge.com) -- advanced growth/product programs
3. Product School YouTube -- free PM lectures
4. Exponent (tryexponent.com) -- PM interview practice

### Communities
1. Mind the Product (mindtheproduct.com)
2. Product School Slack
3. r/ProductManagement (Reddit)
4. Lenny's Newsletter community

---

*Last updated: 2026-03-19*
