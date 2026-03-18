# OpenAI Codex Setup

## Install Skills

Codex uses the same SKILL.md format. Copy the skill folders to your Codex skills directory:

```bash
# Repository-level (recommended)
mkdir -p .agents/skills
cp -r ../../skills/learn .agents/skills/curriculum-learn
cp -r ../../skills/learn-end .agents/skills/curriculum-learn-end

# Or user-level (available across all projects)
cp -r ../../skills/learn ~/.agents/skills/curriculum-learn
cp -r ../../skills/learn-end ~/.agents/skills/curriculum-learn-end
```

Enable skills if not already enabled:
```bash
codex --enable skills
```

## Add to AGENTS.md

Create or edit `AGENTS.md` in your project root. Copy the contents of `CLAUDE-SNIPPET.md` (in repo root) and adapt:

- Replace `CLAUDE.md` references with `AGENTS.md`
- Replace any Claude-specific terminology

The trigger phrases ("let's learn", "learn-end") work the same way in Codex via AGENTS.md.

## How It Works

- Type "let's learn" in a Codex session to start
- Type "learn-end" to exit mid-session
- Codex reads SESSION-STATE.md and follows the skill protocol
- Progress is tracked in the same markdown files

## Differences from Claude Code

| Feature | Claude Code | Codex |
|---------|------------|-------|
| Skill trigger | Automatic or `/learn` | Automatic via AGENTS.md |
| Web search in session | Built-in | Requires tool configuration |
| Git commit/push | Automatic | Automatic |
| Voice pairing | WisprFlow (native) | WisprFlow (via terminal) |

## Voice Integration (Optional)

WisprFlow has native Codex integration. Install WisprFlow, then dictate your responses during quizzes and reflection exercises. See the main README for full voice setup instructions.
