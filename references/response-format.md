# User-facing output (response shell)

For every HTTP call started under this skill, user-facing output **must** follow this structure (fixed order and punctuation):

1. `identity：` — identity for this request; if none, `none`.  
2. `platform：` — **for display** (see below); for calls unrelated to platform such as `credential/{identity}` or `platform/`, use `none`.  
3. `Request result：` (fullwidth colon after the label)  
4. One blank line + **one** Markdown code block: valid JSON uses `json` with 2-space indent; otherwise `text` with the raw body.

**`platform：` rules**

- **Single-platform** (URL contains `…/{platform}/{identity}`): matches the `platform` segment in the URL.  
- **Universal** (URL is `profile/{identity}` or `ns/{identity}`): URL has **no** platform segment, but this line must be the **first** match in [platform-routing.md](platform-routing.md) for the identity; if none match but you still request, use `none`.  
- **Credential** (URL `credential/{identity}`): **do not** infer platform; this line is always `none`.

**Forbidden**: long duplicated JSON outside the shell.

**Endpoint that needs `x-api-key` (Wallet)**: after the user provided a key and you issued the request, **whether** HTTP succeeds or fails, **only** output this shell + the code block under `Request result：` (body as-is, including error JSON or non-JSON text); **forbidden** to add any text before or after the shell—no success summary, error interpretation, retry advice, apologies, etc.

**Cannot build the request** (e.g. missing identity / single-platform but platform unknown): do not output this shell; reply with one line clarifying what is missing; after the user supplies it, output per this page.
