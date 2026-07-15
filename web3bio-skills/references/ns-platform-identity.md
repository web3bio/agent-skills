# `GET ns/{platform}/{identity}`

| | |
|--|--|
| **Logical name** | `get-profile-ns` |
| **When to use** | Not universal + user wants brief / ns (see [SKILL.md](../SKILL.md), [intent-cues.md](intent-cues.md)). |
| **Path** | `ns/{platform}/{identity}` |

**`platform` / `identity`**: [platform-routing.md](platform-routing.md) · [request-conventions.md](request-conventions.md) · [response-format.md](response-format.md)

```bash
curl -sS "https://api.web3.bio/ns/ens/sujiyan.eth"
```
