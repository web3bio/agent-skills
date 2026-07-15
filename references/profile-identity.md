# `GET profile/{identity}` (Universal)

| | |
|--|--|
| **Logical name** | `get-universal-profile` |
| **When to use** | Universal and not NS; path has **only** `profile` and `identity`, **no** `platform` segment. |
| **Path** | `profile/{identity}` |

**Display `platform：`**: not in URL; fill from routing-table match → [response-format.md](response-format.md) + [platform-routing.md](platform-routing.md).  
**Request**: [request-conventions.md](request-conventions.md)

```bash
curl -sS "https://api.web3.bio/profile/sujiyan.eth"
```
