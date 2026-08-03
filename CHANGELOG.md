# Changelog

## 0.4.0 — 2026-07-31

### Agent-visible

- Replaced the fixed `identity：` / `platform：` / `Request result：` shell with a portable Markdown result card.
- Added endpoint-aware summaries while preserving one complete JSON/text response block for copying.
- Removed the result-type subtitle and added clickable `https://web3.bio/{identity}` links to linked-identity tables.
- Added explicit no-invention, no-HTML, no-silent-truncation, and API-key redaction rules.
- Preserved strict Wallet output boundaries and Avatar URL-only handling.
- Bumped the routing manifest to version 5 and synchronized examples and regression cases.

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
