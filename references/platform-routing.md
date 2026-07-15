# Identity → `platform` (routing table)

For an **extracted identity**, run `.test(identity)` with each `REGEX.*` in [regex-patterns.md](regex-patterns.md); the **first true row top to bottom** yields `platform`.  
When maintaining, align `ROUTING_MATCH_ORDER` (documented in the same file) with this table.

| Order | `REGEX.*` | URL / display `platform` |
|-------|-----------|---------------------------|
| 1 | `BASENAMES` | `basenames` |
| 2 | `LINEA` | `linea` |
| 3 | `LENS` | `lens` |
| 4 | `SNS` | `sns` |
| 5 | `ENS` | `ens` |
| 6 | `UNSTOPPABLE_DOMAINS` | `unstoppabledomains` |
| 7 | `ETH_ADDRESS` | `ethereum` |
| 8 | `SOLANA_ADDRESS` | `solana` |
| 9 | `FARCASTER` | `farcaster` |

- **Single-platform URL**: user’s explicit platform (allow list) **wins** for the path; otherwise this table. If nothing matches → **do not** invent a single-platform URL.  
- **Universal**: not in URL; display `platform：` still uses this table (see [response-format.md](response-format.md)).  
- **Explicit platforms allowed** (lowercase): `ens`, `lens`, `farcaster`, `basenames`, `linea`, `ethereum`, `unstoppabledomains`, `sns`, `solana`.
