# CLAUDE.md Snippet for Curriculum Integration

> **Instructions:** Copy the section below into your project's CLAUDE.md file.
> Replace all [BRACKETED] values with your specific details.
> This tells Claude how to find and run your curriculum.

---

## [YOUR TOPIC] Curriculum (COMMANDS)

When I say "let's learn", "learn", "today's lesson", "next lesson", "continue learning", "resume lesson", or "start lesson":
1. Read `[PATH_TO_CURRICULUM]/CURRICULUM-CONFIG.md` (curriculum config)
2. Read `[PATH_TO_CURRICULUM]/SESSION-STATE.md` (single source of truth)
3. Read `[PATH_TO_CURRICULUM]/CURRICULUM.md` (find section matching "Next Session Plan")
4. Run the adaptive learning engine from the `learn` skill

**Session flow (v2 — evidence-based):**
Pre-test (5 min) → SM-2 spaced repetition quiz (10 min) → Socratic lesson (25-30 min) → Interleaved practice (10 min) → Portfolio exercise (10-15 min) → Community (5 min) → Reflect + mastery check (5 min). Total: ~65-75 min.

**End-of-session auto-actions (EVERY session, no command needed):**
1. Update SESSION-STATE.md (advance session, update SM-2 tracker, velocity dashboard, set flags)
2. Update progress.md
3. Commit and push to GitHub

When I say "learn-end", "end lesson", "stop learning", "done learning", "save progress", "wrap up lesson", "pause lesson", or "that's enough for today":
- **Use ONLY for mid-session exits** (need to leave before lesson finishes)
- Saves partial progress, logs where I stopped, sets resume flags
- Read `[PATH_TO_CURRICULUM]/SESSION-STATE.md`
- Follow the end-session protocol from the `learn-end` skill
