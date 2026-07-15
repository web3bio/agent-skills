# Regression cases (minimal set)

Quick smoke tests after changing triggers, routing, or auth. Each line checks one thing.

## Intent routing

1. `Look up credentials for sujiyan.eth` → `credential/{identity}`
2. `Wallet identity for sujiyan.eth` → `wallet/{identity}` (key required)
3. `Avatar for sujiyan.eth` → `avatar/{identity}` (report `Location` URL only)
4. `Domain info for sujiyan.eth` → `domain/{identity}`
5. `Batch profiles for ens,vitalik.eth and lens,stani.lens` → `profile/batch/{ids}`
6. `NS summaries for vitalik.eth and stani.lens` → `ns/batch/{ids}` (with resolved platforms)
7. `Profile for sujiyan.eth` → single-platform or universal (per wording and routing)
8. `Linked Web2 and Web3 socials for sujiyan.eth` → universal branch

## Anti-triggers

1. `I want to transfer money` must not trigger wallet identity
2. `Give me a Twitter username` (no clear profile / multi-platform intent) should not be forced into a special route; clarify or use profile branch per SKILL
3. Single identity + “profiles” generically → not batch
4. Avatar ask must not download or paste image binary into the reply

## Authentication

1. Wallet without key: only output `Please provide x-api-key (wallet endpoint only).`
2. After Wallet has a key, do not ask again before calling
3. Non-wallet requests do not send `x-api-key`

## Response shell

1. Shell order fixed: `identity：` → `platform：` → `Request result：` → code block
2. After Wallet requests, no text outside the shell
3. Invalid JSON responses go in a `text` code block as-is
4. Avatar success body is a URL in a `text` fence (`platform：` = `none`)
5. Batch `platform：` = `none`; `identity：` lists the query ids
