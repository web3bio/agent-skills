# AGENTS.md

Instructions for AI coding agents working **in this repository** (not for end-user API keys).

## What this repo is

A git repo that **publishes one Agent Skill** in [`web3bio-skills/`](web3bio-skills/) for `https://api.web3.bio`.

Source of truth order (inside the skill package):

1. [`web3bio-skills/references/routing-manifest.json`](web3bio-skills/references/routing-manifest.json)
2. [`web3bio-skills/SKILL.md`](web3bio-skills/SKILL.md)
3. Pages under [`web3bio-skills/references/`](web3bio-skills/references/) linked from [`web3bio-skills/reference.md`](web3bio-skills/reference.md)

**Spec constraint**: the skill directory name must equal frontmatter `name` (`web3bio-skills`). Do not move `SKILL.md` back to the git root.

## Before you change behavior

- Read `web3bio-skills/SKILL.md` and only the `references/*.md` you touch.
- Route / auth / priority changes: update **both** `routing-manifest.json` and `reference.md`, plus affected endpoint pages.
- Platform matching: update `regex-patterns.md` and `platform-routing.md` together.
- Trigger / routing edits: reconcile `intent-cues.md`, `test-cases.md`, and `examples.md`.

## Security defaults (do not regress)

- Only `/wallet/{identity}` uses `x-api-key`.
- Never document or implement sending that header elsewhere.
- Do not add instructions that echo user API keys or commit them to the repo.

## Validate before PR

```bash
npx skills-ref validate ./web3bio-skills
npx skills add . -l
```

## Human-oriented docs

- Onboarding and install: [`README.md`](README.md)
- Contributing: [`CONTRIBUTING.md`](CONTRIBUTING.md)
- Security: [`SECURITY.md`](SECURITY.md)
