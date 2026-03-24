# Cursor Skills Collection

A collection of ready-to-use [Agent Skills](https://docs.cursor.com/context/skills) for [Cursor](https://cursor.com) — the AI code editor.

These skills teach Cursor's AI agent how to perform specialized tasks: reviewing web pages like a CMO, running pre-deploy checklists, generating product updates from git history, and more.

## What Are Skills?

Skills are markdown instruction files that give Cursor's AI agent domain-specific knowledge. When you ask Cursor to do something that matches a skill, it reads the instructions and follows them — like giving a smart colleague a playbook.

## Quick Start

### Option 1: Copy individual skills

1. Browse the [`skills/`](./skills) folder
2. Copy any skill folder into your project's `.cursor/skills/` directory
3. That's it — Cursor will automatically detect and use them

### Option 2: Copy all skills

```bash
# From your project root
cp -r /path/to/cursor-skills/skills/* .cursor/skills/
```

### Option 3: Personal skills (available across all projects)

```bash
# Copy to your personal skills directory
cp -r /path/to/cursor-skills/skills/* ~/.cursor/skills/
```

## Skills

### Web Page Reviews

These skills turn Cursor into a page review team. Point it at a URL and get structured, graded feedback.

| Skill | What It Does |
|-------|-------------|
| [CMO Conversion Review](./skills/cmo-conversion-review/) | Reviews a page as a CMO — grades conversion readiness, trust signals, competitive positioning, and gives a prioritized fix list |
| [Content Review](./skills/content-review/) | Reviews copy quality — tone, clarity, brand consistency, microcopy, spelling, and suggests specific rewrites |
| [SEO & AI Citation Review](./skills/seo-ai-review/) | Checks metadata, structured data, heading hierarchy, image optimization, and AI citation readiness (ChatGPT, Gemini, Perplexity) |
| [UX / Design Review](./skills/ux-design-review/) | Reviews layout, mobile responsiveness, CTAs, accessibility, visual hierarchy, and touch targets |

**How to use**: Open a chat in Cursor and say something like *"Do a CMO review of this page"* while viewing the page's code, or give it a URL to fetch.

### Developer Workflows

| Skill | What It Does |
|-------|-------------|
| [Pre-Deploy Checklist](./skills/pre-deploy-checklist/) | Runs a security, correctness, and cross-app impact review before you deploy. Gives a GO / NEEDS FIXES / DO NOT DEPLOY verdict |
| [Product Update](./skills/product-update/) | Generates a non-technical product update from git history — ready to paste into Slack or send to stakeholders |

**How to use**: Say *"Run the pre-deploy checklist"* or *"Generate a product update for this week"*.

### Cursor Meta-Skills

Skills for working with Cursor itself — creating rules, creating more skills, and managing settings.

| Skill | What It Does |
|-------|-------------|
| [Create Rule](./skills/create-rule/) | Helps you create `.cursor/rules/` files with proper frontmatter, scoping, and best practices |
| [Create Skill](./skills/create-skill/) | Guides you through authoring new skills — structure, descriptions, patterns, and anti-patterns |
| [Update Cursor Settings](./skills/update-cursor-settings/) | Modifies Cursor/VSCode settings.json — knows the file locations for macOS, Linux, and Windows |

**How to use**: Say *"Create a new rule for our TypeScript standards"* or *"Create a skill for reviewing database migrations"*.

## Customization

These skills are designed to be generic starting points. To get the most out of them:

1. **Add your brand context** — The CMO and Content Review skills ask about your industry and voice. You can hardcode these into the skill file so you don't have to repeat yourself.
2. **Add your stack** — The Pre-Deploy Checklist works for any project, but you can add your specific build commands, app names, and security requirements.
3. **Add your templates** — The Product Update skill has a default format. Change it to match your team's Slack or email style.

## How Skills Work

```
~/.cursor/skills/          ← Personal skills (all projects)
.cursor/skills/            ← Project skills (this repo only)

skill-name/
├── SKILL.md               ← Required — main instructions
├── reference.md           ← Optional — detailed docs
└── examples.md            ← Optional — usage examples
```

Cursor reads the `SKILL.md` file when it detects a matching request. The `description` field in the frontmatter is what Cursor uses to decide when to apply a skill — make it specific.

## Contributing

Found a bug? Have an improvement? PRs welcome.

Want to add a new skill? Follow the structure in [Create Skill](./skills/create-skill/SKILL.md) for best practices.

## License

MIT — use these however you want.
