# Examples

Concrete install-to-use paths. Paths are relative to `https://api.web3.bio`.

## After install — try these prompts

| User says | Route |
|-----------|--------|
| `Profile for vitalik.eth` | `GET /profile/vitalik.eth` (or ens single-platform if they name ENS) |
| `Credentials for sujiyan.eth` | `GET /credential/sujiyan.eth` |
| `Avatar URL for sujiyan.eth` | `GET /avatar/sujiyan.eth` → report `Location` |
| `Domain owner / expiry for sujiyan.eth` | `GET /domain/sujiyan.eth` |
| `Batch: vitalik.eth and stani.lens` | `GET /profile/batch/{ids}` with `["ens,vitalik.eth","lens,stani.lens"]` |
| `Wallet identity for sujiyan.eth` | Ask for key line, then `GET /wallet/sujiyan.eth` |

## Result card (abbreviated)

Actual output must include the complete, unabridged API body; this example shows the presentation order only.

~~~markdown
## sujiyan.eth

| Field | Value |
|---|---|
| Identity | `sujiyan.eth` |
| Platform | `ens` |
| Address | `0x1234…abcd` |
| Avatar | [Open avatar](https://example.com/avatar.png) |

### Linked identities

| Identity | Platform | Display name | Profile |
|---|---|---|---|
| `sujiyan.eth` | `ens` | sujiyan.eth | [View profile](https://web3.bio/sujiyan.eth) |

### Complete JSON

```json
{
  "identity": "sujiyan.eth",
  "address": "0x1234567890abcdef"
}
```
~~~

Do not use the example values as API facts. Show only returned fields, and never abbreviate the complete JSON.

Avatar success uses the same heading style, omits inferred platform, and ends with `### Avatar URL` plus a `text` fence containing the URL.

## Curl smoke (optional human check)

```bash
curl -sS "https://api.web3.bio/profile/sujiyan.eth" | head -c 200
curl -sS -D - -o /dev/null "https://api.web3.bio/avatar/sujiyan.eth" | grep -i '^location:'
```
