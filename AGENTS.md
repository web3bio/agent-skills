# AGENTS.md

Instructions for AI coding agents working **in this repository** (not for end-user API keys).

## What this repo is

A single **Agent Skill** for calling `https://api.web3.bio` (profiles, credentials, NS summaries, avatar, domain, batch, wallet). Source of truth order:

1. [`references/routing-manifest.json`](references/routing-manifest.json)
2. [`SKILL.md`](SKILL.md) (intent order, field extraction, response discipline)
3. Per-topic files under [`references/`](references/) linked from [`reference.md`](reference.md)

## Before you change behavior

- Read [`SKILL.md`](SKILL.md) and the specific `references/*.md` you touch; avoid loading all reference files at once.
- If you change route templates, auth, or priority: update **both** `routing-manifest.json` and [`reference.md`](reference.md), and any affected endpoint page.
- If you change platform matching: update [`references/regex-patterns.md`](references/regex-patterns.md) and [`references/platform-routing.md`](references/platform-routing.md) together.
- After trigger or routing edits: reconcile [`references/intent-cues.md`](references/intent-cues.md) and [`references/test-cases.md`](references/test-cases.md).

## Security defaults (do not regress)

- Only `/wallet/{identity}` uses `x-api-key`.
- Never document or implement sending that header elsewhere.
- Do not add instructions that echo user API keys or commit them to the repo.

## Human-oriented docs

- Onboarding and install: [`README.md`](README.md)
- Contributing checklist: [`CONTRIBUTING.md`](CONTRIBUTING.md)
- Vulnerability reporting: [`SECURITY.md`](SECURITY.md)
