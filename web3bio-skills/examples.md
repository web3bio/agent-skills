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

## Response shell (abbreviated)

```text
identity：sujiyan.eth
platform：ens
Request result：

{ JSON or text body in a fenced code block }
```

Avatar success: `platform：` is `none`; body is a `text` fence with the URL only.

## Curl smoke (optional human check)

```bash
curl -sS "https://api.web3.bio/profile/sujiyan.eth" | head -c 200
curl -sS -D - -o /dev/null "https://api.web3.bio/avatar/sujiyan.eth" | grep -i '^location:'
```
