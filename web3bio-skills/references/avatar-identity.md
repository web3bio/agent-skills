# `GET avatar/{identity}`

| | |
|--|--|
| **Logical name** | `get-avatar` |
| **Path** | `avatar/{identity}` (relative to base) |

## When to use

When the user wants an **avatar URL** / profile picture / PFP for an identity—not the full profile JSON.

See triggers in [intent-cues.md](intent-cues.md). This branch is after Wallet and before Domain.

## Identity

Same primary-id extraction as profile. **Do not** put `platform` in the URL. The API prioritizes avatars by the queried identity’s platform.

## Request behavior (important)

- Issue `GET` **without** following the redirect into a binary download when possible.
- The API typically responds with **`307`** and a **`Location`** header whose value is the avatar URL (e.g. `https://euc.li/sujiyan.eth`).
- Put that URL string in the response shell body (`text` fence). **Do not** download, decode, or embed image bytes in the reply.
- If the tool only returns a final URL after redirect (and no body), use that URL the same way.
- If there is no usable `Location` / URL, put the raw status and headers or error body in a `text` fence.

## Request and response

- **Request**: [request-conventions.md](request-conventions.md) (`GET`, `encodeURIComponent`, no auth).
- **Response**: [response-format.md](response-format.md). For this endpoint **`platform：` is always `none`**.

```bash
# Prefer header-only; do not pipe image bytes into chat
curl -sS -D - -o /dev/null "https://api.web3.bio/avatar/sujiyan.eth"
# → read Location: …
```
