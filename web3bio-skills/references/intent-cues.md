# Intent triggers (supplement)

Main flow: [SKILL.md](../SKILL.md) **Decision order (first match wins)**. Below are **extra** synonyms to reduce missed routing.

## Wallet (`GET /wallet/{identity}`)

**Primary triggers** (route to [wallet-identity.md](wallet-identity.md), before avatar / domain / profile): **wallet info**, **wallet information**.

Additional synonyms: **my wallet** (when clearly “look up API wallet identity / bindings”, not transfers), **wallet identity** (including the English phrase when it refers to this API’s data).

Anti-triggers (do **not** use this endpoint): **transfer**, **sign**, **balance**, **gas**, **private key** (usually not wallet-identity lookups).

## Avatar (`GET /avatar/{identity}`)

**Primary triggers**: **avatar**, **profile picture**, **profile pic**, **pfp**, **avatar URL**.

Anti-triggers: user wants a full profile / social graph / credentials—not just the image URL.

## Domain (`GET /domain/{identity}`)

**Primary triggers**: **domain info**, **domain metadata**, **WHOIS**, **domain owner**, **resolver**, **expiry** / **expires**, **text records** (when clearly domain-record focused).

Anti-triggers: general “who is X” / social profile → profile flow; trust/credentials → credential.

## Batch (`GET /profile/batch/{ids}` · `GET /ns/batch/{ids}`)

**Primary triggers**: **batch**, **multiple identities**, two or more distinct identities in one ask (e.g. “look up A, B, and C”).

Prefer **NS batch** when the same ask is summary / brief / NS; otherwise full profile batch.

Anti-triggers: a single identity even if the user says “profiles” (plural generically)—use profile flow.

## Universal

Beyond what SKILL lists, e.g.: **all**, **all related**, **what profiles exist**, **what other identities**, **linked accounts** (when clearly multi-platform aggregation for **one** identity).

## NS (brief)

Beyond what SKILL lists, e.g.: **summary**, **overview**, **key info only**, **NS** (standalone or English context).
