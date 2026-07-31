# `GET profile/batch/{ids}` · `GET ns/batch/{ids}`

| | |
|--|--|
| **Logical name** | `get-batch-profile` / `get-batch-ns` |
| **Paths** | `profile/batch/{ids}` · `ns/batch/{ids}` (relative to base) |

## When to use

When the user wants **two or more** identities in one call, or explicitly asks for **batch**. Prefer NS (`ns/batch/...`) when they ask for summary / brief / NS; otherwise full (`profile/batch/...`).

Max **30** items per request. See [intent-cues.md](intent-cues.md).

## Building `{ids}`

1. For each identity, resolve a **batch platform** (explicit user platform wins; else [platform-routing.md](platform-routing.md)).
2. Supported batch platforms (API): `ethereum`, `ens`, `basenames`, `linea`, `farcaster`, `lens`.
3. If a resolved platform is outside that list (e.g. `solana`, `sns`, `unstoppabledomains`), **do not** include it in batch—ask to drop it or look it up via single-identity profile flow.
4. Format each entry as `"platform,identity"` (comma, no spaces), e.g. `"ens,vitalik.eth"`, `"farcaster,#3"`.
5. Build a JSON array string, then **`encodeURIComponent` the entire array** as the single `{ids}` path segment.

Example array before encoding:

```json
[
  "ens,vitalik.eth",
  "lens,stani.lens",
  "farcaster,dwr.eth",
  "basenames,tony.base.eth",
  "ethereum,0x7cbba07e31dc7b12bb69a1209c5b11a8ac50acf5",
  "linea,name.linea.eth"
]
```

## Request and response

- **Request**: [request-conventions.md](request-conventions.md) (`GET`, no auth).
- **Response**: [response-format.md](response-format.md).
  - `identity：` — comma-separated list of the batch query ids (the `"platform,identity"` strings), or `batch` if too long.
  - `platform：` — always `none`.

```bash
curl -sS "https://api.web3.bio/profile/batch/$(python3 -c 'import urllib.parse; print(urllib.parse.quote("[\"ens,vitalik.eth\",\"lens,stani.lens\"]", safe=""))')"
```

Equivalent encoded path segment:

`%5B%22ens%2Cvitalik.eth%22%2C%22lens%2Cstani.lens%22%5D`
