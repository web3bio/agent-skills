# Contributing

Thanks for helping improve this skill repository. The project is primarily **Markdown + JSON** and does not include runtime backend service code.

## Read Before You Contribute

- `AGENTS.md` - in-repo guidance for AI coding agents
- `SKILL.md` - intent tree and runtime behavior rules
- `SECURITY.md` - security boundaries, especially `x-api-key` scope

## Recommended Contribution Flow

1. **Keep PRs focused**: one concern per PR (for example: intent cues only, or one platform addition).
2. **Synchronize route-related changes** across:
   - `references/routing-manifest.json`
   - `reference.md`
   - affected `references/<topic>.md`
   - `SKILL.md` when decision flow changes
3. **Keep regex/table parity**: if `references/regex-patterns.md` changes, also update `references/platform-routing.md` (or vice versa) and explain why in the PR.
4. **Add regression context**: note whether smoke checks in `references/test-cases.md` were reviewed; add new cases when behavior changes.

## Documentation Style

- Keep repository documents in English.
- Use concise, action-oriented instructions.
- Avoid duplicating the full reference table inside `SKILL.md`; use `reference.md` for progressive disclosure.

## Behavioral Changes vs Editorial Changes

- **Behavioral changes** (routing, auth, response shell, key request wording): mark as **BREAKING** or **agent-visible** in the PR and update `CHANGELOG.md`.
- **Editorial changes** (typos, links, wording): regular docs updates are fine.

## Reviewer Checklist

- [ ] `x-api-key` appears only on the wallet route in docs and manifest.
- [ ] `GET`-only and URL-encoding requirements remain intact.
- [ ] Wallet strict shell-only output rule in `references/response-format.md` is unchanged.
- [ ] New endpoints are added to both `reference.md` and `references/routing-manifest.json`.
