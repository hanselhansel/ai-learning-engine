# Articulation Scoring Reference

> Hub-and-spoke reference loaded during Portfolio + Teach-Back blocks (Standard/Deep modes only).
> Purpose: Train interview-ready communication — concise, persuasive, specific.

## Three Scoring Dimensions (1-5 Scale)

| Dimension | 1 (Weak) | 3 (Adequate) | 5 (Strong) |
|-----------|----------|--------------|------------|
| **Conciseness** | 3x more words than needed | Some filler, could trim 30% | Every word earns its place |
| **Persuasiveness** | States facts only | Has structure but weak evidence | Clear thesis + evidence + so-what |
| **Specificity** | Vague generalities ("many companies") | Some names/numbers | Named companies, precise data, cited sources |

## Audience Tagging (E5)

Each exercise tagged with target audience. Scoring adjusts expectations: adjust conciseness standard based on audience context — flat rubric, audience as hint.

| Tag | Context |
|-----|---------|
| `VC` | Investor pitch — numbers-first, thesis-driven, time-pressured |
| `hiring_manager` | Job interview — demonstrate competence + culture fit, concise |
| `engineer` | Technical peer — precision matters, jargon OK, depth expected |
| `general` | Non-technical audience — analogies, no jargon, clarity paramount |

## Rewrite Challenge Mechanic

**Trigger:** Conciseness < 3 on any exercise.

**Flow:**
1. "Good content. Too many words. Rewrite in half the length."
2. Score the rewrite.
3. If improved: "Better. That's the version you'd use in an interview."
4. If NOT improved: give a model rewrite → save to `portfolio/best-practices.md`

**Skip allowed:** Learner can say "skip." Log as SKIPPED. After 3 consecutive skips, surface: "I notice you've been skipping rewrites — want me to lower the threshold?"

## Before/After Card (E1)

When Rewrite Challenge triggers, generate an HTML side-by-side comparison card. Save to session summary file.

```html
<div style="display:grid;grid-template-columns:1fr 1fr;gap:16px">
  <div style="background:#1e293b;padding:16px;border-radius:8px;border:1px solid #ef4444">
    <h4 style="color:#f87171">Before (XX words)</h4>
    <p>original text</p>
  </div>
  <div style="background:#1e293b;padding:16px;border-radius:8px;border:1px solid #4ade80">
    <h4 style="color:#4ade80">After (XX words)</h4>
    <p>rewritten text</p>
  </div>
</div>
```

## Progressive Difficulty Curve

| Sessions | Approach |
|----------|----------|
| 1-10 | Score all 3 dimensions, frame as "observation" not "grade" |
| 11-20 | Active coaching — "Can you tighten this?" |
| 21+ | Hard constraints — "30 words max. Go." |

## Word Count Tracking

- Log word count for every exercise response
- Track compression ratio (words/concept) over time
- words/concept = total exercise word count / number of new concepts in that session. If 0 concepts, skip metric.

## Interview Readiness Score (E2)

Composite: 60% content + 40% articulation.

| Component | Formula |
|-----------|---------|
| **Content score** | (avg quiz score / 10) * 100 |
| **Articulation score** | ((avg of 3 dimensions - 1) / 4) * 100 |
| **Composite** | 0.6 * content + 0.4 * articulation |

Display as dual bar showing content vs articulation components.
