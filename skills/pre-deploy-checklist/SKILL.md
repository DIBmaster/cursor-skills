---
name: pre-deploy-checklist
description: Run a pre-deployment checklist before pushing to production. Reviews changed files for security, correctness, edge cases, cross-app impact, and confirms builds pass. Use when the user says they are about to deploy, asks for a final review, pre-deploy check, or code review before production.
---

# Pre-Deploy Checklist

Run this checklist before any production deployment. Be thorough.

## Steps

### Step 1: Identify All Changes
- List every file changed since the last deploy (use `git diff` or `git log`).
- Group changes by area: frontend, backend, shared packages, database migrations, config.

### Step 2: Security Review
- [ ] No secrets, API keys, or tokens exposed to the client.
- [ ] All user inputs validated (Zod, Joi, or equivalent).
- [ ] No raw SQL strings (parameterized queries only).
- [ ] Access control / authorization on any new endpoints or pages.
- [ ] No sensitive data in logs or error messages.
- [ ] No money calculations using floating point (if applicable).

### Step 3: Cross-App Impact
- [ ] If shared types changed → all consuming apps checked.
- [ ] If database schema changed → all apps' queries verified.
- [ ] If API contracts changed → all consumers updated.
- [ ] If shared packages changed → types/builds regenerated.

### Step 4: Edge Cases & Correctness
- [ ] Error handling in place (try/catch with meaningful messages).
- [ ] Loading and empty states handled in UI changes.
- [ ] Null/undefined values handled in data flows.
- [ ] Race conditions considered for concurrent operations.

### Step 5: Build Verification
- Run the build command and confirm all apps pass.
- Report any TypeScript errors or warnings.

### Step 6: Migration Check (if applicable)
- [ ] Migration is additive (no destructive changes without discussion).
- [ ] Migration has a comment block explaining what and why.
- [ ] Types/schemas regenerated after migration.

### Step 7: Manual Steps Required
- List any scripts that need to be run manually post-deploy.
- List any environment variables or config changes needed.
- Provide copy-paste ready commands for anything the user needs to run.

## Output Format

```
## Pre-Deploy Review

**Status**: [GO ✅ / NEEDS FIXES 🟡 / DO NOT DEPLOY 🔴]

### Changes Summary
- [Area]: [Brief description of what changed]

### Security
- [Any concerns or "All clear"]

### Cross-App Impact
- [Any concerns or "No cross-app impact"]

### Edge Cases
- [Any concerns or "All covered"]

### Build Status
- App: [✅ Pass / ❌ Fail]

### Risks
- [Any risks flagged, or "No significant risks"]

### Manual Steps After Deploy
- [Any scripts to run, or "None"]

### Recommendation
[One sentence: deploy or fix first]
```
