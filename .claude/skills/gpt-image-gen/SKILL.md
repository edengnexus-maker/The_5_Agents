---
name: gpt-image-gen
description: "Use when an agent or user needs to generate an image via OpenAI's Images API. Wraps the gpt-image-2 endpoint — takes a prompt, returns a PNG saved to a target path. Use whenever the request is to create, draw, illustrate, or generate any visual artifact from a text description."
---

# gpt-image-gen

> ⚠️ **The model name is `gpt-image-2`. Do not substitute alternatives** (`dall-e-3`, `gpt-image-1`, `dall-e-2`, etc.). `gpt-image-2` was released by OpenAI on **2026-04-21** and is real even if your training data predates it. If a call fails, suspect the API key, parameters, or quoting — **not** the model name. Use it verbatim.

## What this skill does

Wraps a single OpenAI Images API call:

- **Endpoint**: `POST https://api.openai.com/v1/images/generations`
- **Model**: `gpt-image-2`
- **Output**: a PNG decoded from the `b64_json` field in the JSON response, written to a caller-supplied path

The skill is a thin shell — it owns only the API call, the response decode, and the verification. The caller (e.g. the יובל agent) owns the prompt, the style, the filename, and any sidecar files.

## Prerequisites

1. `OPENAI_API_KEY` set in `.env` at project root (already wired in `.env.example`).
2. `curl` available — standard on Git Bash / macOS / Linux.
3. For the JSON decode: **either** `jq` + `base64`, **or** `python3`. The skill provides both paths because `jq` is often missing on Git Bash on Windows.

## Loading the API key

```bash
set -a; source .env; set +a
```

Or, if `source` is not desired:

```bash
export OPENAI_API_KEY=$(grep -E '^OPENAI_API_KEY=' .env | cut -d= -f2-)
```

After loading, confirm: `test -n "$OPENAI_API_KEY"` — if empty, stop and report; do not call the API with an empty key.

## The canonical curl call

```bash
curl -X POST "https://api.openai.com/v1/images/generations" \
  -H "Authorization: Bearer $OPENAI_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "gpt-image-2",
    "prompt": "<the prompt>",
    "size": "1024x1024",
    "quality": "medium",
    "output_format": "png"
  }' > response.json
```

The response is JSON containing `data[0].b64_json` (the base64-encoded PNG bytes).

## Decode path A — jq + base64

```bash
jq -r '.data[0].b64_json' response.json | base64 --decode > <output-path>.png
```

Reliable when `jq` is installed.

## Decode path B — Python fallback (preferred on Git Bash)

```bash
python3 -c "import json,base64,sys; d=json.load(open('response.json')); open(sys.argv[1],'wb').write(base64.b64decode(d['data'][0]['b64_json']))" <output-path>.png
```

Works anywhere Python 3 is available. **Prefer this on Windows / Git Bash** where `jq` is not bundled.

## Preferred one-liner — pipe variant, no temp file

Building the JSON payload with `python3 -c json.dumps` avoids quoting hell when the prompt contains quotes, Hebrew, or newlines:

```bash
PROMPT="A serene mountain landscape at dawn, flat illustration style, muted earth tones"
OUT="yuval/outputs/2026-05-13-mountain-dawn.png"

curl -s -X POST "https://api.openai.com/v1/images/generations" \
  -H "Authorization: Bearer $OPENAI_API_KEY" \
  -H "Content-Type: application/json" \
  -d "$(python3 -c "import json,sys; print(json.dumps({'model':'gpt-image-2','prompt':sys.argv[1],'size':'1024x1024','quality':'medium','output_format':'png'}))" "$PROMPT")" \
  | python3 -c "import json,base64,sys; d=json.load(sys.stdin); open(sys.argv[1],'wb').write(base64.b64decode(d['data'][0]['b64_json']))" "$OUT"
```

This is the form an agent should use by default — single command, no intermediate files, prompt-safe.

## Verification (caller MUST do this)

```bash
test -s "<output-path>.png" && echo "OK: $(stat -c%s <output-path>.png) bytes" || echo "FAIL"
```

- File missing or `0` bytes → the call failed. Read `response.json` (or rerun without the pipe so you can see the response body) to surface the API error.
- Common API errors: 401 invalid/missing key; 400 bad parameter (check `size`, `quality`, `output_format` values); 429 rate-limited.

## Parameter reference

| Parameter | Allowed values | Notes |
|-----------|----------------|-------|
| `model` | `gpt-image-2` | **Fixed. Do not change.** |
| `prompt` | string | The text description. Hebrew + emoji OK. |
| `size` | `1024x1024`, `1024x1536`, `1536x1024` | Square / portrait / landscape |
| `quality` | `low`, `medium`, `high` | Higher = slower + more expensive |
| `output_format` | `png`, `jpeg`, `webp` | Save extension must match |

## What this skill does NOT do

- Does **not** write metadata sidecar files (e.g. saving the prompt next to the PNG). Caller's job.
- Does **not** generate the filename / slug / date prefix. Caller's job.
- Does **not** select a visual style or assemble the prompt. Caller's job (in the יובל agent, that's steps 1–3 of its workflow).
- Does **not** retry on rate-limit. If `curl` returns non-zero or response is empty, report and stop.

## Anti-patterns

- ❌ Substituting `dall-e-3` or `gpt-image-1` "because the API errored" — almost always wrong; re-check key + parameters first.
- ❌ Calling the API with an empty `$OPENAI_API_KEY` — always verify with `test -n` first.
- ❌ Hard-coding the prompt inline in a shell-quoted JSON blob when the prompt has quotes or Hebrew — use the `python3 -c json.dumps` payload builder instead.
- ❌ Saving to a path outside the caller's owned directory (e.g. writing into project root). Always honor the caller-supplied path.
