---
name: aioz-ai-upload-file
description: Use when you need to upload a local file to AIOZ AI storage to get a public URL, typically because a model you want to run takes a file input (image, audio, video, document). Produces a download_url you can pass to inference.
---

# Upload a file to AIOZ AI storage

Uploading is a two-step presigned-S3 flow. The MCP server only does the first step (it
proxies the AIOZ AI API). **You perform the byte upload yourself** with a direct HTTP
request to S3 — the presigned form alone uploads nothing, and without step 2 the
`download_url` 404s.

## Prerequisites — check this first

**Step 2 is not an MCP tool.** The server hands you a signed form; *you* upload the bytes.
That means you must be able to **execute an HTTP request yourself** — a shell with `curl`,
or any other way to run code that makes a network call.

- **You can** (Claude Code, Cursor, VS Code, any client with shell or code execution) →
  proceed.
- **You cannot** (Claude Desktop, or any client without code execution) → **stop and say so
  plainly.** Tell the user that uploading needs a client that can run commands, that text
  and parameter based inference still works fine here, and that a file-input model needs a
  code-capable client. **Do not attempt the upload. Never report a file as uploaded when it
  was not, and never hand back a `download_url` you did not successfully upload to** — the
  URL is returned by step 1 and looks valid even when nothing was ever stored at it.

**Auth.** `x_api_key` is optional and you normally **omit it**: a server configured with
`AIOZ_AI_API_KEY` in its environment uses that key automatically. The key lives in the
user's client config, not in your context, so don't go looking for one and never invent one.
If a call returns **401**, the server has no key configured — ask the user for one and pass
it as `x_api_key`.

## 1. Get a presigned upload form (`create_presigned_url`)

| Arg | Value |
|-----|-------|
| `folder` | One of `avatars`, `thumbnails`, `covers`, `samples`, `documents`. Use `samples` for inference inputs, or `documents` for text/PDF-style files. The image-only folders (`avatars`/`thumbnails`/`covers`) reject non-image MIME types. |
| `mime` | The file's MIME type, e.g. `image/png`, `audio/wav`, `application/pdf`. |
| `name` | A filename, e.g. `input.png`. |
| `size` | The real byte length. Must be > 0 and ≤ 104,857,600 (100 MiB), or the presign call fails. |
| `org_username` | Optional. Routes the upload into an organization's namespace. |

The payload is under `data`:

```json
{ "endpoint": "https://<s3-host>", "fields": "<JSON string of signed fields>", "download_url": "https://.../uploads/<folder>/<namespace>/<name>" }
```

## 2. Upload the bytes to S3 (you do this, NOT an MCP tool)

The backend picks one of two mechanisms from the `size` you declared, and the presign
response differs between them. **Detect the tier from `endpoint`:** if it contains
`X-Amz-Algorithm` it is the PUT tier, otherwise the form-POST tier. Using the wrong one
fails the upload.

| Declared `size` | `endpoint` | `fields` | How to upload |
|-----------------|------------|----------|---------------|
| ≤ 5 MiB (5,242,880 bytes) | Bucket root URL (no `X-Amz-*` query params) | Full S3 form policy (`key`, `policy`, `x-amz-*`, `Content-Type`, …) | `POST` multipart/form-data: add **every** `fields` entry as a form field, unchanged, then the file last as field `file` |
| > 5 MiB, ≤ 100 MiB | Pre-signed object URL with `X-Amz-*` query params | `{"Content-Type": "<mime>"}` only | `PUT` the raw bytes; set `Content-Type` from `fields` |

```bash
# $ENDPOINT and $FIELDS come from the presign response (data.endpoint / data.fields).
if echo "$ENDPOINT" | grep -q "X-Amz-Algorithm"; then
  # PUT tier (> 5 MiB): raw binary body, Content-Type from fields
  CONTENT_TYPE=$(echo "$FIELDS" | jq -r '.["Content-Type"]')
  curl -sS -X PUT "$ENDPOINT" \
    -H "Content-Type: $CONTENT_TYPE" \
    --data-binary "@/path/to/your/file"
else
  # Form-POST tier (≤ 5 MiB): spread fields into -F flags, file last
  curl -sS -X POST "$ENDPOINT" \
    $(echo "$FIELDS" | jq -r 'to_entries[] | "-F \(.key)=\(.value|@sh)"') \
    -F "file=@/path/to/your/file"
fi
```

Expect a 2xx. The body is usually empty; the status code is the signal.

## 3. Use the download_url

The `download_url` from step 1 is now live. Pass it to inference under the model's file
input slot from its `input_format` (e.g. `{ "input": "<download_url>" }`) — see
`aioz-ai-run-inference` steps 3–4.

To remove it later: `delete_url` `{ url: "<download_url>" }`.
