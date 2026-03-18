# Cursor AI Setup

Cursor doesn't have a skills system equivalent to Claude Code or Codex, but you can achieve similar results using Cursor Rules + the Composer/Agent mode.

## Setup

### Option 1: MDC Rules (Recommended)

Create a rule file at `.cursor/rules/curriculum.mdc`:

```yaml
---
description: "AI-powered structured curriculum system"
globs: ["**/SESSION-STATE.md", "**/CURRICULUM.md", "**/progress.md"]
alwaysApply: false
---
```

Then paste the contents of the `learn` skill's SKILL.md below the frontmatter.

### Option 2: .cursorrules

Add the curriculum instructions to your `.cursorrules` file in the project root. Copy the key protocol from the `learn` skill's SKILL.md.

## How It Works

1. Open your curriculum folder in Cursor
2. Open Composer (Cmd+I) or Agent mode
3. Reference `SESSION-STATE.md` in your message: "Read @SESSION-STATE.md and run today's lesson"
4. Cursor follows the curriculum protocol from the rules

## Limitations vs Claude Code / Codex

| Feature | Cursor | Claude Code / Codex |
|---------|--------|-------------------|
| Auto-trigger on "let's learn" | No (must reference files manually) | Yes |
| Persistent state across sessions | Yes (reads files) | Yes |
| Auto-commit to git | Manual | Automatic |
| Web search during lessons | Via Agent mode | Built-in |
| Skill auto-loading | Rules always loaded | Progressive disclosure |

Cursor works best for the curriculum if you use Agent mode and explicitly reference your curriculum files. The methodology and file formats are identical; only the automation layer differs.

## Voice Integration (Optional)

WisprFlow has native Cursor integration. Install WisprFlow, then dictate your curriculum responses directly into Cursor's Composer. See the main README for full voice setup instructions.
