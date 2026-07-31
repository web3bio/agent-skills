# `GET ns/{identity}` (Universal · NS)

| | |
|--|--|
| **Logical name** | `get-universal-ns` |
| **When to use** | Universal + NS. Path has **only** `ns` and `identity`. |
| **Path** | `ns/{identity}` |

**Display `platform：`**: same as [profile-identity.md](profile-identity.md) (routing-table match, not a URL segment).

**Request / response**: [request-conventions.md](request-conventions.md) · [response-format.md](response-format.md) · [platform-routing.md](platform-routing.md)

```bash
curl -sS "https://api.web3.bio/ns/sujiyan.eth"
```
