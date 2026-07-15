# Intent triggers (supplement)

Main flow: [SKILL.md](../SKILL.md) **Decision order (first match wins)**. Below are **extra** synonyms to reduce missed routing.

## Wallet (`GET /wallet/{identity}`)

**Primary triggers** (route to [wallet-identity.md](wallet-identity.md), before universal profile): **wallet info**, **wallet information**.

Additional synonyms: **my wallet** (when clearly “look up API wallet identity / bindings”, not transfers), **wallet identity** (including the English phrase when it refers to this API’s data).

Anti-triggers (do **not** use this endpoint): **transfer**, **sign**, **balance**, **gas**, **private key** (usually not wallet-identity lookups).

## Universal

Beyond what SKILL lists, e.g.: **all**, **all related**, **what profiles exist**, **what other identities**, **linked accounts** (when clearly multi-platform aggregation).

## NS (brief)

Beyond what SKILL lists, e.g.: **summary**, **overview**, **key info only**, **NS** (standalone or English context).
