# `GET /wallet/{identity}`

| | |
|--|--|
| **Logical name** | `get-wallet-identity` |
| **Path** | `wallet/{identity}` (relative to base) |

## When to use

When Wallet intent matches (see [intent-cues.md](intent-cues.md)). This branch comes before universal profile.

## Required inputs

- Must be able to extract `identity` (and `encodeURIComponent`).
- Must have `x-api-key`.

Without a key: only output the single key request line from [request-conventions.md](request-conventions.md); do not send HTTP.

## Request and response

- Request rules: [request-conventions.md](request-conventions.md).
- Response shell: [response-format.md](response-format.md).
- For this endpoint `platform：` is always `none`; `identity：` is the `{identity}` in the path.
- After a request with key, only shell + body regardless of outcome; zero explanation outside the shell.

```bash
curl -sS -H "Accept: application/json" -H "x-api-key: <user-provided key>" \
  "https://api.web3.bio/wallet/sujiyan.eth"
```
