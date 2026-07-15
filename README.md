# Web3.bio Agent Skills

This repository provides **Agent Skills** for the Web3.bio APIs. It standardizes routing, authentication boundaries, response-shell rules, and endpoint references to reduce incorrect calls and secret leakage.

## Capability Overview

| Scenario                     | Behavior                                                |
| ---------------------------- | ------------------------------------------------------- |
| Credential / credit          | `GET credential/{identity}` (do not resolve `platform`) |
| Wallet identity              | `GET wallet/{identity}` (**requires** `x-api-key`)      |
| Single-platform full profile | `GET profile/{platform}/{identity}`                     |
| Single-platform NS brief     | `GET ns/{platform}/{identity}`                          |
| Universal full profile       | `GET profile/{identity}`                                |
| Universal NS                 | `GET ns/{identity}`                                     |                                        |

- **Method**: all routes are `GET`; path segments must be URL-encoded (`encodeURIComponent`).
- **Auth**: only the wallet route may include `x-api-key`; all other routes must omit it.
- **Machine-readable routing source of truth**: `references/routing-manifest.json`.

## Repository Structure

```
.
|- SKILL.md                 # Core skill: triggers, order, extraction, request/response discipline
|- README.md                # This file
|- reference.md             # Index for references/ (open only what is needed)
|- AGENTS.md                # Guidance for AI agents editing this repo
|- CONTRIBUTING.md          # Contribution and review checklist
|- SECURITY.md              # Threat model and disclosure workflow
|- CHANGELOG.md             # Versioned change history
|- LICENSE                  # MIT
|- references/              # Endpoint docs, intent cues, regex patterns, response format, test cases
```

## Document Map

| File              | Audience             | Purpose                                                          |
| ----------------- | -------------------- | ---------------------------------------------------------------- |
| `SKILL.md`        | Runtime agents       | Activation rules, decision order, security and trust constraints |
| `reference.md`    | Runtime agents       | Single index for all `references/*` pages                        |
| `README.md`       | Humans / integrators | Install, compatibility, FAQ, maintenance overview                |
| `AGENTS.md`       | AI editors           | In-repo guardrails and sync requirements                         |
| `CONTRIBUTING.md` | Human contributors   | PR flow and reviewer checklist                                   |
| `SECURITY.md`     | Everyone             | Threat model and vulnerability reporting                         |
| `CHANGELOG.md`    | Maintainers / users  | Versioned changes                                                |

## Installation (Cursor and compatible clients)

1. Place the skill directory where your client discovers skills (must contain `SKILL.md`), for example:
   - Personal: `~/.cursor/skills/web3bio-skills/`
   - Project: `<project>/.cursor/skills/web3bio-skills/`
2. Reload the client/editor so the model can discover the skill from YAML metadata and trigger terms.
3. If your toolchain supports commands like `npx skills add <org/repo>`, publish this repository first and follow your client's install instructions.

### Naming Notes

The directory name can differ from the repository name, but `SKILL.md` must be at the loaded skill root. Keeping `web3bio-skills` is recommended for consistency with `_meta.json`.

## Runtime Reading Order

1. Read `SKILL.md`.
2. Read `reference.md`.
3. Open only the specific `references/*` files required for the current request.

## Routing Workflow (First Match Wins)

1. **Credential** -> `GET credential/{identity}`
2. **Wallet** -> `GET wallet/{identity}` (without key: output only the fixed key-request line and do not call)
3. **Profile branch** -> choose universal vs NS and single-platform vs universal using intent + `platform-routing` / `references/regex-patterns.md`

Intent and anti-intent cues are documented in `references/intent-cues.md`.

## FAQ

| Symptom                                          | Action                                                        |
| ------------------------------------------------ | ------------------------------------------------------------- |
| Wallet request targets a non-Web3.bio host       | Only `https://api.web3.bio` is allowed (see `SECURITY.md`)    |
| Wallet call attempted without key                | Forbidden; output only the fixed one-line key request         |
| `x-api-key` used on credential/profile/ns routes | Forbidden; remove the header                                  |
| Universal response `platform:` is unclear        | Use first match in `platform-routing.md`, else `none`         |
| Single-platform URL cannot determine platform    | Do not fabricate; ask for clarification or use universal flow |
| Routing behavior uncertain after edits           | Run smoke scenarios from `references/test-cases.md`           |

## Security and Compliance

- Use only `https://api.web3.bio`.
- Never commit or expose user API keys.
- For wallet responses, follow the strict shell format in `references/response-format.md`.

See `SKILL.md` and `SECURITY.md` for full constraints.

## Maintenance Checklist

- Route behavior changes: update `references/routing-manifest.json`, `reference.md`, and affected `references/*.md` together.
- Platform matching changes: update both `references/regex-patterns.md` and `references/platform-routing.md`.
- Behavior-visible updates: record in `CHANGELOG.md` and bump `_meta.json` version for releases.

## License and Terms

Repository documentation/config is licensed under [MIT](LICENSE). Use of `https://api.web3.bio` remains subject to Web3.bio API terms and limits.
