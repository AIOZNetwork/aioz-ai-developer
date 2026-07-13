---
name: aioz-ai-run-inference
description: Use when the user wants to run an AIOZ AI model on some input and get the result. Covers finding a model, reading its input/output schema and cost, checking balance before submitting, submitting an inference task, waiting for it, and reading the output. Handles the async task lifecycle correctly.
---

# Run inference on an AIOZ AI model

Inference is asynchronous: create a task, poll until it reaches a terminal state, then
read the result. Do the steps in order.

**Auth.** Authenticated tools take an `x_api_key` argument, but it is optional and you
normally **omit it**: a server configured with `AIOZ_AI_API_KEY` in its environment uses
that key automatically. The key lives in the user's client config, not in your context, so
don't go looking for one and never invent one. If a call returns **401**, the server has no
key configured — ask the user for one and pass it as `x_api_key`.

## Steps

### 1. Find the model (`get_model_list`)

Optional filters: `search` (keyword), `task`, `filter_by`, `sort`, `limit`, `offset`.
Take the model `id` from the results.

### 2. Pre-flight (do all three before submitting)

This is what makes a run succeed instead of failing on a malformed body or an empty
balance. Submitting blind wastes a round-trip and the body is usually wrong.

**2a. Schema — `get_current_model_versioning_by_model_id_by_api_key`** `{ id }`. The
current versioning record carries the input/output contract:

- `input_format` — the keys the model expects, each with a `type` (model-declared, e.g.
  `file`, `int`, `text`) and constraints (e.g. `mime_type: ["image/*"]` on a file slot).
  You build the request body from this in step 3.
- `output_format` — the keys and types the result will contain, so you know what to read
  back in step 6.

```json
{ "input_format":  { "input": { "type": "file", "mime_type": ["image/*"] } },
  "output_format": { "output_file": { "type": "file", "mime_type": ["image/*"] } } }
```

**2b. Cost — `get_cost_to_compute_task_by_model_api_key`** `{ id }` → `data.cost` (a JSON
number). This is the authoritative per-inference price.

**2c. Balance — `get_api_key_balance`** → `data.balance` (a decimal string; compare as a
decimal, not a float). **If the balance is below the cost, stop and tell the user to top
up.** Don't submit a task the account can't pay for.

**2d. Serving — `check_model_is_serving`** `{ id }`. If the model isn't live, the task
queues indefinitely or fails; surface that instead of submitting.

### 3. Build the body from `input_format`

A JSON object whose keys match `input_format`:

- scalar slots (`text`, `int`, …): the value directly under that key.
- `file` slots: run the **`aioz-ai-upload-file`** skill to get a `download_url`, then put
  the **URL** (not the bytes) under that key. Check the file's MIME against the slot's
  `mime_type` first.

Keys that don't match the declared schema fail the task with a 400.

### 4. Submit (`distribute_task_v2`)

```json
{ "id": "<model_id>", "body": { "input": "<download_url or value, per input_format>" } }
```

- `id` is the **model id** (not `model_id`).
- `body` is the model input object **directly** — a JSON object, not a JSON-encoded
  string. File URLs go inside `body` under their slot key; there is no `files` argument.
- The response nests the new task id one level deeper than other endpoints: `data.data`.

### 5. Poll until terminal (`get_api_key_log_by_task_id`)

Call `get_api_key_log_by_task_id` `{ id: <task_id> }` and read `status`.

| | Statuses |
|---|---|
| Non-terminal — keep polling | `in_queue`, `computing` |
| Terminal — stop | `success`, `failed`, `canceled` |

Note the spelling: **`canceled`**, one `l`. Matching on `cancelled` never fires and the
poll loop runs until it times out.

**Wait about 5 seconds between polls.** The API allows about 60 requests/minute per key;
a tight loop hits 429. On a 429, back off further before retrying.

### 6. Report the result honestly

- `success` → read and report the result payload.
- `failed` → report the failure and its error field.
- `canceled` → report that it was canceled.

**Never fabricate an inference result.** If the task is still `in_queue`/`computing`, keep
polling; if it `failed`, say so. A made-up result is worse than reporting failure, and
claiming success on a task that never finished is the worst outcome of all.

To cancel a running task: `cancel_task` `{ id: <task_id> }`.

## Related

- `aioz-ai-upload-file` — get a `download_url` for file inputs before step 3.
