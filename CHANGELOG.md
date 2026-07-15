# Changelog

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
