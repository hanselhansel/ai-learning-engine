# Session Summary Card Template

Generate this card at the end of every session. Save to `sessions/summaries/session-XX.md`.

## Format

```
╔══════════════════════════════════════════════╗
║          LEARNING SESSION RECEIPT            ║
╠══════════════════════════════════════════════╣
║                                              ║
║  Session:    #[NUMBER]                       ║
║  Mode:       [Micro/Quick/Standard/Deep/Syn] ║
║  Duration:   [X] min                         ║
║  Date:       [YYYY-MM-DD]                    ║
║  Streak:     [X] days 🔥                     ║
║                                              ║
╠══════════════════════════════════════════════╣
║  PERFORMANCE                                 ║
╠══════════════════════════════════════════════╣
║                                              ║
║  Pre-test:   [X/Y] → Post: [X/Y] (Δ +[Z])  ║
║  SM-2 Quiz:  [X/Y] correct ([Z]%)           ║
║  Confidence: [X]% calibrated                 ║
║  Mastery:    [X/Y] concepts passed           ║
║                                              ║
╠══════════════════════════════════════════════╣
║  PROGRESS                                    ║
╠══════════════════════════════════════════════╣
║                                              ║
║  Terms Known:    [X] / [TOTAL]               ║
║  Terms Learning: [X]                         ║
║  Terms New:      [X]                         ║
║  Overall:        [X]% complete               ║
║                                              ║
╠══════════════════════════════════════════════╣
║  TODAY'S HIGHLIGHTS                          ║
╠══════════════════════════════════════════════╣
║                                              ║
║  ★ Key insight: [learner's founder summary]  ║
║  📄 Artifact: [portfolio piece created]      ║
║  ⚡ Strongest: [best-scored concept]         ║
║  🔧 Focus next: [weakest concept]            ║
║                                              ║
╠══════════════════════════════════════════════╣
║  NEXT SESSION                                ║
╠══════════════════════════════════════════════╣
║                                              ║
║  Topic: [next session topic]                 ║
║  SM-2 due: [X] terms for review              ║
║  Flags: [any items to address]               ║
║                                              ║
╚══════════════════════════════════════════════╝
```

## Field Population Rules

- **Session number**: from SESSION-STATE.md sessions_completed + 1
- **Mode**: the flex mode chosen at session open
- **Duration**: approximate elapsed time
- **Streak**: from SESSION-STATE.md streak_count
- **Pre-test scores**: only for Standard/Deep modes (others show "—")
- **SM-2 Quiz**: correct/total from this session's quiz
- **Confidence**: % of calibrated responses (vs over/underconfident)
- **Mastery**: concepts that passed the mastery gate (Standard/Deep only)
- **Terms Known/Learning/New**: count from terminology tracker
- **Overall %**: sessions_completed / target_sessions
- **Key insight**: learner's "explain to a founder" summary
- **Artifact**: file saved during portfolio exercise (if any)
- **Strongest/Focus**: best and worst scored concepts this session

## Mode-Specific Adjustments
- **Micro**: omit Pre-test, Mastery, Artifact rows. Show only Quiz + Terms + Next.
- **Quick**: omit Pre-test, Mastery rows.
- **Synthesis**: replace Pre-test with "Integration Challenge: [score]"
