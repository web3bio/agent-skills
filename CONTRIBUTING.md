# Contributing

Thanks for helping improve this skill repository. The project is primarily **Markdown + JSON** and does not include runtime backend service code.

## Read Before You Contribute

- `AGENTS.md` - in-repo guidance for AI coding agents
- `web3bio-skills/SKILL.md` - intent tree and runtime behavior rules
- `SECURITY.md` - security boundaries, especially `x-api-key` scope

## Recommended Contribution Flow

1. **Keep PRs focused**: one concern per PR (for example: intent cues only, or one platform addition).
2. **Synchronize route-related changes** across:
   - `web3bio-skills/references/routing-manifest.json`
   - `web3bio-skills/reference.md`
   - affected `web3bio-skills/references/<topic>.md`
   - `web3bio-skills/SKILL.md` when decision flow changes
3. **Keep regex/table parity**: if `regex-patterns.md` changes, also update `platform-routing.md` (or vice versa) and explain why in the PR.
4. **Add regression context**: note whether smoke checks in `test-cases.md` / `examples.md` were reviewed; add new cases when behavior changes.
5. **Validate**: `npx skills-ref validate ./web3bio-skills`

## Documentation Style

- Keep repository documents in English.
- Use concise, action-oriented instructions.
- Avoid duplicating the full reference table inside `SKILL.md`; use `reference.md` for progressive disclosure.

## Behavioral Changes vs Editorial Changes

- **Behavioral changes** (routing, auth, response shell, key request wording): mark as **BREAKING** or **agent-visible** in the PR and update `CHANGELOG.md`.
- **Editorial changes** (typos, links, wording): regular docs updates are fine.

## Reviewer Checklist

- [ ] Skill lives under `web3bio-skills/` and `skills-ref validate` passes.
- [ ] `x-api-key` appears only on the wallet route in docs and manifest.
- [ ] `GET`-only and URL-encoding requirements remain intact.
- [ ] Wallet strict shell-only output rule in `response-format.md` is unchanged.
- [ ] New endpoints are added to both `reference.md` and `routing-manifest.json`.
- [ ] README install commands still match Skills CLI behavior.
