# `GET domain/{identity}`

| | |
|--|--|
| **Logical name** | `get-domain` |
| **Path** | `domain/{identity}` (relative to base) |

## When to use

When the user wants **domain-level metadata**: ownership, resolver, manager, contenthash, text records, created / updated / expired timestamps (WHOIS-style), not a full social profile graph.

See triggers in [intent-cues.md](intent-cues.md). This branch is after Avatar and before Batch / profile flow.

## Identity

Extract a domain-like `identity` (ENS, Basenames, Linea, SNS / `.sol`, etc.). **Do not** put `platform` in the URL.

## Request and response

- **Request**: [request-conventions.md](request-conventions.md) (`GET`, `encodeURIComponent`, no auth).
- **Response**: [response-format.md](response-format.md). For this endpoint **`platform：` is always `none`**.

```bash
curl -sS "https://api.web3.bio/domain/sujiyan.eth"
```
