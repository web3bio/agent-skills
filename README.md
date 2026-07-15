# Web3.bio Agent Skills

Agent Skill for calling [`https://api.web3.bio`](https://api.web3.bio): profiles, NS, credentials, avatar, domain, batch, and wallet identity—with fixed routing and auth boundaries.

## Install

**Recommended** (Skills CLI, all detected agents):

```bash
npx skills add web3bio/agent-skills -g -y
```

What this does:

- Clones `web3bio/agent-skills`, installs the only skill `web3bio-skills`
- Writes to `~/.agents/skills/web3bio-skills`
- Registers it for **all agents the CLI detects** on your machine (omit `-a` = same as targeting every detected agent)
- `-g` = user/global scope; `-y` = non-interactive

Other useful variants:

| Goal | Command |
|------|---------|
| Cursor only | `npx skills add web3bio/agent-skills -g -a cursor -y` |
| Explicit all agents | `npx skills add web3bio/agent-skills -g -a '*' -y` (quote `*` so the shell does not expand it) |
| List skills in the repo (no install) | `npx skills add web3bio/agent-skills -l` |
| Project scope (current project only) | omit `-g` (run inside that project) |

**Manual** (no CLI) — copy the **skill package**, not the git root:

```bash
git clone https://github.com/web3bio/agent-skills.git
mkdir -p ~/.agents/skills
cp -R agent-skills/web3bio-skills ~/.agents/skills/web3bio-skills
```

Requirements:

- Installed folder name **must** be `web3bio-skills` (matches `name` in `SKILL.md`)
- That folder must contain `SKILL.md` at its root (not one level deeper)
- Do **not** point the agent at the git repo root (`agent-skills/`) as the skill

Start a **new** agent chat after install (reload alone may not pick up new skills).

### Verify

```bash
npx skills-ref validate ~/.agents/skills/web3bio-skills
npx skills list -g
```

You should see `web3bio-skills` under Global Skills. Then ask: `Profile for vitalik.eth` or `Avatar for sujiyan.eth`.

## Quick start (usage)

| You ask                             | Skill routes to                                  |
| ----------------------------------- | ------------------------------------------------ |
| Profile / who is `vitalik.eth`      | `GET /profile/{identity}` (or platform-specific) |
| Credentials / trust for an identity | `GET /credential/{identity}`                     |
| Avatar / PFP URL                    | `GET /avatar/{identity}`                         |
| Domain owner / expiry               | `GET /domain/{identity}`                         |
| Several identities at once          | `GET /profile/batch/{ids}` or `/ns/batch/{ids}`  |
| Wallet identity bundle              | `GET /wallet/{identity}` (needs `x-api-key`)     |

Worked examples: [`web3bio-skills/examples.md`](web3bio-skills/examples.md).

## Capability overview

| Scenario                  | Behavior                                                  |
| ------------------------- | --------------------------------------------------------- |
| Credential / credit       | `GET credential/{identity}`                               |
| Wallet identity           | `GET wallet/{identity}` (**requires** `x-api-key`)        |
| Avatar URL                | `GET avatar/{identity}` (`Location` only; no image bytes) |
| Domain metadata           | `GET domain/{identity}`                                   |
| Batch full / NS           | `GET profile/batch/{ids}` · `GET ns/batch/{ids}`          |
| Single-platform full / NS | `GET profile\|ns/{platform}/{identity}`                   |
| Universal full / NS       | `GET profile\|ns/{identity}`                              |

- Method: all `GET`; path segments URL-encoded.
- Auth: only wallet may send `x-api-key`.
- Source of truth: `web3bio-skills/references/routing-manifest.json`.

## Repository layout

```
.
|- README.md                 # Humans: install + overview
|- AGENTS.md / CONTRIBUTING.md / SECURITY.md / CHANGELOG.md
|- package.json
|- web3bio-skills/           # ← installable skill (name == directory)
|  |- SKILL.md
|  |- reference.md
|  |- examples.md
|  |- _meta.json
|  |- references/
```

## Decision order (first match wins)

1. Credential → 2. Wallet → 3. Avatar → 4. Domain → 5. Batch → 6. Profile / NS

## FAQ

| Symptom                                | Action                                                                                                                |
| -------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| `skills list` shows nothing            | Use `npx skills list -g` for global installs                                                                          |
| `skills-ref` fails on repo root        | Validate `./web3bio-skills` (or the installed path), not the git root                                                 |
| Manual `cp .../web3bio-skills` missing | Publish/pull the nested layout first; older flat releases: copy the clone itself to `~/.agents/skills/web3bio-skills` |
| Skill not triggering                   | New chat after install; mention address/domain keywords                                                               |
| Wrong install folder name              | Must be `web3bio-skills`, not `agent-skills`                                                                          |
| Wallet without key                     | Agent outputs only: `Please provide x-api-key (wallet endpoint only).`                                                |
| Avatar dumps binary                    | Forbidden—use `Location` URL only                                                                                     |

## Security

- Host: only `https://api.web3.bio`.
- Never commit API keys. See [SECURITY.md](SECURITY.md).

## Maintainers

Route changes: update `web3bio-skills/references/routing-manifest.json`, `web3bio-skills/reference.md`, and affected pages together. Bump `web3bio-skills/_meta.json` + [CHANGELOG.md](CHANGELOG.md) on release.

## License

MIT for this repository. API use follows Web3.bio terms.
