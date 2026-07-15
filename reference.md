# Reference index

**Repo overview / install / FAQ**: [README.md](README.md) · **editing this repo**: [AGENTS.md](AGENTS.md) · **security**: [SECURITY.md](SECURITY.md) · **contributing**: [CONTRIBUTING.md](CONTRIBUTING.md) · **changelog**: [CHANGELOG.md](CHANGELOG.md) · **metadata**: [_meta.json](_meta.json).

**Role**: **sole catalog** of `references/`. [SKILL.md](SKILL.md) **does not** link each `.md` here individually; after intent is fixed per SKILL, **open files from this table**.

**Intent tree, order, and standard flow** follow SKILL; **paths, full trigger text, curl samples, logical names, and auth details** follow each dedicated page.  
**Execution precedence**: `routing-manifest.json` (machine-readable) > dedicated pages (human-readable).

**Read only files relevant to the task**—avoid loading everything at once.

| Topic | File |
|------|------|
| Routing manifest (priority, auth, path templates, output rules) | [references/routing-manifest.json](references/routing-manifest.json) |
| Requests (base, auth, `x-api-key` session rules, encoding) | [references/request-conventions.md](references/request-conventions.md) |
| Response shell (including Universal `platform:`) | [references/response-format.md](references/response-format.md) |
| Identity → platform routing table | [references/platform-routing.md](references/platform-routing.md) |
| Regex patterns (`REGEX`, `ROUTING_MATCH_ORDER`) | [references/regex-patterns.md](references/regex-patterns.md) |
| Intent triggers (supplement, incl. Wallet / Avatar / Domain / Batch) | [references/intent-cues.md](references/intent-cues.md) |
| Regression samples (smoke after changes) | [references/test-cases.md](references/test-cases.md) |
| `GET profile/{platform}/{identity}` | [references/profile-platform-identity.md](references/profile-platform-identity.md) |
| `GET ns/{platform}/{identity}` | [references/ns-platform-identity.md](references/ns-platform-identity.md) |
| `GET profile/{identity}` | [references/profile-identity.md](references/profile-identity.md) |
| `GET ns/{identity}` | [references/ns-identity.md](references/ns-identity.md) |
| `GET credential/{identity}` | [references/credential-identity.md](references/credential-identity.md) |
| `GET avatar/{identity}` | [references/avatar-identity.md](references/avatar-identity.md) |
| `GET domain/{identity}` | [references/domain-identity.md](references/domain-identity.md) |
| `GET profile/batch/{ids}` · `GET ns/batch/{ids}` | [references/batch-identity.md](references/batch-identity.md) |
| `GET /wallet/{identity}` (requires `x-api-key`) | [references/wallet-identity.md](references/wallet-identity.md) |

**Adding a new endpoint**: add a page under `references/`, update the table above and `routing-manifest.json`; if you need a new branch, add one line for intent/flow in [SKILL.md](SKILL.md)—**no need** to duplicate links in SKILL.
