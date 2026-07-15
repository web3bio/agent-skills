# Changelog

## 0.3.0 — 2026-07-15

### Agent-visible / packaging

- Moved the installable skill into `web3bio-skills/` so directory name matches frontmatter `name` (`skills-ref validate` passes).
- Rewrote install docs for `npx skills add web3bio/agent-skills` and `~/.agents/skills/` (not outdated `~/.cursor/skills/`-only paths).
- Stronger `description` triggers; added `license`, `compatibility`.
- Slimmed `SKILL.md` (removed editor Maintenance section); added `examples.md`.
- Softened “must read all docs first” friction—agents can call from decision order, opening references on demand.

## 0.2.0 — 2026-07-15

### Agent-visible

- Unified `SKILL.md` decision order (removed conflicting early draft section).
- Added routes: `GET avatar/{identity}`, `GET domain/{identity}`, `GET profile/batch/{ids}`, `GET ns/batch/{ids}`.
- Avatar: report redirect `Location` URL only; do not download image bytes.
- Documented `ROUTING_MATCH_ORDER` in `references/regex-patterns.md`.
- Bumped routing manifest to version 4.

### Docs / packaging

- Added `CHANGELOG.md` and `_meta.json`.
- Synced `reference.md`, `README.md`, intent cues, test cases, and response shell rules.
