# `GET credential/{identity}`

| | |
|--|--|
| **Logical name** | `get-credential` |
| **Path** | `credential/{identity}` (relative to base) |

## When to use

When the user wants data related to **credentials / credit / trust / trustworthiness**, use this endpoint **directly**; **do not** resolve `platform`, **do not** use Wallet, Avatar, Domain, Batch, or universal/single-platform/NS profile combos, **do not** use [platform-routing.md](platform-routing.md).

## Triggers (any one category)

Including but not limited to: **credit**, **trust**, **credential**, **trustworthiness**, **reputation**, **credibility**, **integrity**; English **credential** / **credentials** / **trustworthiness** when clearly on-chain / identity credentials—not interpersonal trust.

> If the same sentence mentions profile / dossier / social / wallet: if **credential/credit** is the main ask, still use this endpoint; if credit words are incidental and the core is profile (or Wallet), follow [SKILL.md](../SKILL.md) for that flow.

## Identity

Same primary-id extraction as profile (`trim` or tokenize, strip `@`/punctuation); you only need an `identity` string encodable in the path—shape is **not** limited to the routing table (**do not** force a `platform` into the URL).

## Request and response

- **Request**: [request-conventions.md](request-conventions.md) (`GET`, `encodeURIComponent`, no auth).  
- **Response**: [response-format.md](response-format.md). For this endpoint **`platform：` is always `none`**.

```bash
curl -sS "https://api.web3.bio/credential/sujiyan.eth"
```
