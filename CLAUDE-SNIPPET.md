# CLAUDE.md Snippet for Curriculum Integration

> **Instructions:** Copy the section below into your project's CLAUDE.md file.
> Replace all [BRACKETED] values with your specific details.
> This tells Claude how to find and run your curriculum.

---

## [YOUR TOPIC] Curriculum (COMMANDS)

When I say "let's learn", "learn", "today's lesson", "next lesson", "continue learning", "resume lesson", or "start lesson":
1. Read `[PATH_TO_CURRICULUM]/SESSION-STATE.md` (single source of truth)
2. Read `[PATH_TO_CURRICULUM]/CURRICULUM.md` (find the section matching "Next Session Plan")
3. If it exists, load the pre-read at `[PATH_TO_CURRICULUM]/sessions/day-XX-session.md`
4. Run the full session protocol from the `learn` skill

**End-of-session auto-actions (EVERY session, no command needed):**
1. Update SESSION-STATE.md (advance day, log session, update terminology tracker, set flags)
2. Update progress.md
3. Commit and push to GitHub (if repo is set up)
4. **AUTO-GENERATE next day's pre-read** at `sessions/day-XX-session.md` with:
   - Web search for latest developments in the topic area
   - Papers, news, company announcements relevant to next day's topics
5. Commit and push the pre-read

When I say "learn-end", "end lesson", "stop learning", "done learning", "save progress", "wrap up lesson", "pause lesson", or "that's enough for today":
- **Use ONLY for mid-session exits** (need to leave before lesson finishes)
- Saves partial progress, logs where I stopped, sets resume flags
- Read `[PATH_TO_CURRICULUM]/SESSION-STATE.md`
- Follow the end-session protocol from the `learn-end` skill
