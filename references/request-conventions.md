# Request conventions

## Base URL

Production: `https://api.web3.bio` (same as [SKILL.md](../SKILL.md)).

## Method and authentication (default)

- **GET**, no `Authorization`; optional `Accept: application/json`.
- **Most paths**: **do not** send `x-api-key`, even if the user already shared a key in the session (see below).

## Authenticated endpoints and x-api-key

Only this call **must** include the header `x-api-key: <user-provided api-key>` (header name exactly as shown).

| Path (relative to `https://api.web3.bio`) | Reference                                |
| ----------------------------------------- | ---------------------------------------- |
| `/wallet/{identity}`                      | [wallet-identity.md](wallet-identity.md) |

### In-session api-key (Wallet · prescribed I/O)

#### When there is no key yet — Agent **output** (single line only)

- **Must only** send the following line to the user, **verbatim** (no title, no list, no Markdown, no quotes, no prefix/suffix, no second sentence or line break):  
  `Please provide x-api-key (wallet endpoint only).`
- **Forbidden**: rephrasing, extra politeness, long explanations, sample keys, security tips, `curl` samples, etc.
- **Do not issue any HTTP this turn**; no requests with missing or placeholder keys.

#### User **input** key (next message)

- The user’s **immediate next** message: `trim` the full text, take the **first non-empty line** as the api-key string and **store** it for this session; text **after** that line in the same message is **ignored** (not part of the key).
- If `trim` yields no non-empty line: next turn send the **same** key request line again; still no request.
- After storing, **do not** ask again for later calls to the endpoints in the table above within the same session.

#### After a request with key completes

- Regardless of outcome, **only** output per [response-format.md](response-format.md) shell + body; **zero** explanation outside the shell.
- `wallet` requires a usable extracted `identity`, encoded into the path.

#### Other

- **Do not** add `x-api-key` to endpoints not listed above; even if the user provided a key, calls to `credential`, `profile/...`, `ns/...`, `platform/`, etc. **omit** this header.

## Path and encoding

- Paths are `{Base URL}/{path}`.
- `identity` and every path segment must be **`encodeURIComponent`**’d.

## Tooling source of truth

- Shapes and the routing table depend on [regex-patterns.md](regex-patterns.md). When extending, keep [platform-routing.md](platform-routing.md) in sync.
