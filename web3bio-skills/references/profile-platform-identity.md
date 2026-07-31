# `GET profile/{platform}/{identity}`

| | |
|--|--|
| **Logical name** | `get-profile` |
| **When to use** | Not universal, not NS; user wants single-platform full profile. |
| **Path** | `profile/{platform}/{identity}` (relative to base) |

**`platform` / `identity`**: [platform-routing.md](platform-routing.md); requests: [request-conventions.md](request-conventions.md); response: [response-format.md](response-format.md).

```bash
curl -sS "https://api.web3.bio/profile/ens/sujiyan.eth"
```
