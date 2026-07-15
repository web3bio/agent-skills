---
name: web3bio-skills
description: >-
  Query Web3.bio (api.web3.bio) for profiles, NS summaries, credentials, domain
  WHOIS, avatars, batch lookups, and wallet identity. Use whenever the user
  mentions an Ethereum/Solana address, .eth/.lens/.sol/base.eth domain, ENS,
  Lens, Farcaster, Basenames, Linea, SNS, web3.bio, on-chain identity, linked
  socials, avatar/pfp, domain owner/expiry, or wallet identity mapping—even if
  they do not say "Web3.bio" or "API".
license: MIT
compatibility: Requires network access to https://api.web3.bio. Wallet route needs a user-provided x-api-key.
metadata:
  author: web3bio
  version: "0.3.0"
---

# Web3.bio Skills

## Decision order (first match wins)

1. **Credential** → `GET credential/{identity}` (no `platform`)
2. **Wallet** → `GET wallet/{identity}` (**requires** `x-api-key`; see request-conventions)
3. **Avatar** → `GET avatar/{identity}` (report `Location` URL only; no image bytes)
4. **Domain** → `GET domain/{identity}` (WHOIS / owner / resolver / expiry)
5. **Batch** (≥2 identities or explicit batch) → `GET profile/batch/{ids}` or `GET ns/batch/{ids}`
6. **Profile flow**:
   - Single + full → `GET profile/{platform}/{identity}`
   - Single + NS → `GET ns/{platform}/{identity}`
   - Universal + full → `GET profile/{identity}`
   - Universal + NS → `GET ns/{identity}`

Triggers: [references/intent-cues.md](references/intent-cues.md). Examples: [examples.md](examples.md).

## Field extraction

- `identity`: tokenize, strip `@` / punctuation, first usable token from the left.
- `platform` (single-platform URL only): explicit allow-listed platform wins; else first match in [references/platform-routing.md](references/platform-routing.md); never invent a platform.
- Batch `ids`: JSON array of `"platform,identity"` (max 30); `encodeURIComponent` the whole array as one path segment. Supported batch platforms: `ethereum`, `ens`, `basenames`, `linea`, `farcaster`, `lens`.

## Request rules

- Base URL **only** `https://api.web3.bio`. All `GET`. Encode path segments.
- Send `x-api-key` **only** on `wallet/{identity}`. Never echo or commit keys.
- Prefer [references/routing-manifest.json](references/routing-manifest.json) as machine-readable source of truth.
- For auth session rules, response shell, or endpoint details, open [reference.md](reference.md) and then **only** the needed page—do not load every reference file.

## Response discipline

- Output per [references/response-format.md](references/response-format.md).
- Wallet without key: only `Please provide x-api-key (wallet endpoint only).`
- After wallet call with key: shell only (no extra prose).
