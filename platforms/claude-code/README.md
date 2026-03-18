# Claude Code / Cowork Setup

## Install Skills

Copy the skill folders to your Claude skills directory:

```bash
# Claude Code CLI
cp -r ../../skills/learn ~/.claude/skills/curriculum-learn
cp -r ../../skills/learn-end ~/.claude/skills/curriculum-learn-end

# Or for Cowork mode
cp -r ../../skills/learn /path/to/.skills/skills/curriculum-learn
cp -r ../../skills/learn-end /path/to/.skills/skills/curriculum-learn-end
```

## Add to CLAUDE.md

Copy the contents of `CLAUDE-SNIPPET.md` (in the repo root) into your project's `CLAUDE.md` file.

Replace all `[BRACKETED]` values with your actual file paths.

## How It Works

- Type `"let's learn"` or use `/learn` to start a session
- Type `"learn-end"` or use `/learn-end` to exit mid-session
- Claude reads SESSION-STATE.md automatically and resumes where you left off
- All progress is tracked and committed to git

## Voice Integration (Optional)

Pair with [WisprFlow](https://wisprflow.ai/) or similar voice dictation tools for a conversational learning experience:

1. Install WisprFlow (macOS, $10/month or free tier)
2. Open Claude Code or Cowork
3. Dictate instead of type: say "let's learn" to start a session
4. During quizzes: explain terms verbally instead of typing. WisprFlow transcribes in real time.
5. During "explain it to a founder" exercises: practice your verbal pitch while WisprFlow captures it

This turns the curriculum into a verbal rehearsal system, not just a reading exercise.
