# Regression cases (minimal set)

Quick smoke tests after changing triggers, routing, or auth. Each line checks one thing.

## Intent routing

1. `Look up credentials for sujiyan.eth` → `credential/{identity}`
2. `Profile for sujiyan.eth` → single-platform or universal (per wording and routing)
3. `Linked Web2 and Web3 socials for sujiyan.eth` universal branch
4. `Domain info for sujiyan.eth` → `domain/{identity}`

## Anti-triggers

1. `I want to transfer money` must not trigger wallet identity
2. `Give me a Twitter username` (no clear profile / multi-platform intent) should not be forced into a special route; clarify or use profile branch per SKILL

## Authentication

1. Wallet without key: only output `Please provide x-api-key (wallet endpoint only).`
2. After Wallet has a key, do not ask again before calling
3. Non-wallet requests do not send `x-api-key`

## Response shell

1. Shell order fixed: `identity：` → `platform：` → `Request result：` → code block
2. After Wallet requests, no text outside the shell
3. Invalid JSON responses go in a `text` code block as-is
