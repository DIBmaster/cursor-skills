---
name: product-update
description: Generate a human-readable product update from recent git history. Creates a non-technical summary suitable for sharing with the team, stakeholders, or in Slack. Use when the user asks for a product update, release notes, team update, weekly summary, or changelog.
---

# Product Update Generator

Generate a clean, non-technical product update from recent git commits. This is for sharing with the team — no code, no jargon, just what changed and why it matters.

## Steps

1. **Pull recent commits**: Use `git log --oneline --since="1 week ago"` (or the user's specified timeframe).
2. **Group by area**: Organize changes into categories.
3. **Translate to plain language**: Convert commit messages into human-readable updates.
4. **Skip internal/technical changes**: Don't mention refactors, type fixes, or dependency updates unless they fixed a user-visible issue.

## Categories

Group updates into these sections (skip empty ones):

- **New Features** — things customers or staff can now do that they couldn't before
- **Improvements** — things that work better than before
- **Bug Fixes** — things that were broken and are now fixed
- **Website** — marketing site changes, new pages, SEO improvements
- **Security & Compliance** — anything related to regulations, audit, or security

## Output Format

```
# Product Update — [Date Range]

## New Features
- [Feature name]: [One sentence explaining what it does and who it helps]

## Improvements
- [What improved]: [One sentence explaining the benefit]

## Bug Fixes
- [What was fixed]: [One sentence explaining what users experienced before]

## Website
- [What changed]: [One sentence]

## Security & Compliance
- [What changed]: [One sentence]
```

## Rules

- **No technical jargon**: "Fixed a bug where fees showed as negative" not "Fixed sign inversion in fee_amount column"
- **Focus on impact**: What does the user/staff member notice?
- **Keep it short**: One sentence per item max
- **Skip noise**: Don't mention code cleanups, type fixes, or linting unless they fixed a real bug
- **Be honest**: If something was broken and fixed, say so plainly
