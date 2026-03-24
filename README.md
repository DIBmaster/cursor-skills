# Cursor Skills Collection

I'm a product manager, not an engineer. I run a fintech company with two apps, a legacy accounting system, regulatory requirements, and no full-time dev team.

I ship product with [Cursor](https://cursor.com).

These are the [Agent Skills](https://docs.cursor.com/context/skills) I built to stop repeating myself. They turn Cursor into a page review team, a deployment safety net, and a stakeholder communication tool — so I can move fast without breaking things in a business where breaking things means breaking people's money.

## Why Skills?

Every time I asked Cursor to review a page, I had to re-explain what "good" looks like. Every time I deployed, I had to remind it to check both apps, verify security, look for floating point math in payment logic. Every time my investors asked "what shipped this week?" I had to manually go through git commits and translate them into human language.

Skills fix that. You write the playbook once, and the AI follows it every time.

## The Page Review Team

These four skills replaced what would normally require a marketing agency, a UX consultant, a content strategist, and an SEO specialist. Run them all on a landing page before launch and you get a structured, graded review from four different perspectives.

| Skill | Perspective | What You Get |
|-------|------------|--------------|
| [CMO Conversion Review](./skills/cmo-conversion-review/) | "Will this page make money?" | Conversion grade, competitive positioning, prioritized 1-hour fix list |
| [Content Review](./skills/content-review/) | "Is the copy clear and on-brand?" | Tone consistency, readability, specific rewrite suggestions |
| [SEO & AI Citation Review](./skills/seo-ai-review/) | "Will Google and ChatGPT find this?" | Metadata, structured data, heading hierarchy, AI citation readiness |
| [UX / Design Review](./skills/ux-design-review/) | "Does this feel right to use?" | Mobile responsiveness, accessibility, visual hierarchy, touch targets |

Each review outputs a letter grade (A+ to F) and categorizes issues as red (critical), yellow (should fix), or green (nice to have) — so you know what to fix first.

**How to use**: Say *"Do a CMO review of this page"* or run all four in sequence for a full page audit.

## The Deployment Safety Net

When you're a PM shipping code to production for a regulated product, there's no QA team catching your mistakes. These skills are the safety net.

| Skill | What It Does |
|-------|-------------|
| [Pre-Deploy Checklist](./skills/pre-deploy-checklist/) | Reviews every changed file for security issues, cross-app breakage, missing error handling, and floating point money bugs. Gives a GO / NEEDS FIXES / DO NOT DEPLOY verdict |
| [Product Update](./skills/product-update/) | Reads your git history and generates a clean, non-technical summary you can paste into Slack or email to stakeholders. No jargon, no commit hashes — just what changed and who it helps |

The pre-deploy checklist was born from real near-misses — a shared type change that broke the admin panel, a payment endpoint missing validation, secrets almost exposed to the client. Now the AI checks for all of that automatically before every deploy.

**How to use**: Say *"Run the pre-deploy checklist"* before deploying, or *"Generate a product update for this week"* on Friday afternoon.

## Cursor Meta-Skills

Skills for building more skills and managing Cursor itself.

| Skill | What It Does |
|-------|-------------|
| [Create Rule](./skills/create-rule/) | Helps you create `.cursor/rules/` files — persistent instructions the AI follows every session |
| [Create Skill](./skills/create-skill/) | Guides you through authoring new skills with proper structure, descriptions, and best practices |
| [Update Cursor Settings](./skills/update-cursor-settings/) | Modifies Cursor/VSCode settings.json — knows file locations for macOS, Linux, and Windows |

## Installation

### Copy individual skills

1. Browse the [`skills/`](./skills) folder
2. Copy any skill folder into your project's `.cursor/skills/` directory
3. Cursor will automatically detect and use them

### Copy all skills

```bash
# From your project root
cp -r /path/to/cursor-skills/skills/* .cursor/skills/
```

### Personal skills (available across all projects)

```bash
cp -r /path/to/cursor-skills/skills/* ~/.cursor/skills/
```

## Make Them Yours

These skills are generic starting points. They get much more powerful when you add your own context:

- **Hardcode your brand voice** into the Content Review so you don't have to describe it every time
- **Add your build commands and app names** to the Pre-Deploy Checklist
- **Add your competitors** to the CMO Review so it always benchmarks against them
- **Customize the Product Update categories** to match your team's Slack format
- **Add industry-specific security checks** — if you handle payments, PII, health data, add those checks to the pre-deploy checklist

The best skills are the ones that encode the things you keep repeating. If you've told Cursor the same thing three times, it should be a skill.

## How Skills Work

```
~/.cursor/skills/          ← Personal skills (all your projects)
.cursor/skills/            ← Project skills (shared with your team)

skill-name/
├── SKILL.md               ← Required — the playbook
├── reference.md           ← Optional — detailed docs
└── examples.md            ← Optional — usage examples
```

Cursor reads the `SKILL.md` when it detects a matching request. The `description` in the frontmatter is how Cursor decides when to apply a skill — make it specific.

## Contributing

PRs welcome. If you've built a skill that saves you time, share it.

## License

MIT
