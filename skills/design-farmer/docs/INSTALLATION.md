# Design Farmer Skill Installation Guide

This guide explains how to install the `design-farmer` skill quickly and consistently.

## Recommended Method (Automatic)

Use the repository installer:

```bash
curl -fsSL https://raw.githubusercontent.com/ohprettyhak/design-farmer/main/install.sh | bash
```

What this does:

1. Detects supported local AI tools.
2. Creates each tool-specific skill directory if needed.
3. Downloads `skills/design-farmer/SKILL.md` from this repository.

Supported tools:

- Claude Code
- Codex CLI
- Amp
- Gemini CLI
- OpenCode

## Why this is convenient

The installer pattern is adapted from `ohprettyhak/pr-review-skill`, which is a practical approach for multi-tool environments:

- One command for all supported tools.
- Safe to run repeatedly.
- Clear per-tool success/failure output.

## Manual Installation (Fallback)

If you prefer manual setup, copy the skill file into your tool's skill directory:

```bash
mkdir -p "<tool-skill-root>/design-farmer"
curl -fsSL \
  https://raw.githubusercontent.com/ohprettyhak/design-farmer/main/skills/design-farmer/SKILL.md \
  -o "<tool-skill-root>/design-farmer/SKILL.md"
```

Replace `<tool-skill-root>` with your tool's path (for example, `~/.claude/skills` or `~/.codex/skills`).

## Troubleshooting

- **"No supported tools detected"**
  - Install at least one supported tool first, then run the installer again.
- **Download failed for one or more tools**
  - Check internet connectivity and retry.
  - Confirm `curl` is available: `curl --version`.

## Notes for Maintainers

- The installer always sources the canonical skill file from:
  - `skills/design-farmer/SKILL.md`
- If installation behavior changes, update this guide in the same PR.
