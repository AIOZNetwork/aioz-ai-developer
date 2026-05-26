# AIOZ AI SDK

Official client SDKs for the [AIOZ AI](https://aiozai.network) API — auto-generated from the OpenAPI specification with full type safety across three languages.

## Available SDKs

| Language | Package | Minimum Runtime | Documentation |
| --- | --- | --- | --- |
| Go | `https://github.com/AIOZNetwork/aioz-ai-go-client` | Go 1.22+ | [go/](go/) |
| Python | `aiozai-sdk` (PyPI) | Python 3.9+ | [python/](python/) |
| TypeScript | `@aiozai/nodejs-client` (npm) | Node.js 18+ | [typescript/](typescript/) |

## Features

All SDKs share the same design:

- **218+ API endpoints** and **578+ typed models**, generated from the same OpenAPI source
- API key configured once at client creation — no per-request plumbing
- Automatic retry with exponential backoff for transient failures
- Configurable timeouts for standard and upload operations
- Domain-grouped service access (Models, Datasets, Competitions, …)

## Service Groups

Every SDK exposes the same twelve service groups:

| Service | Description |
| --- | --- |
| Models | AI model management |
| Datasets | Dataset management |
| Competitions | Competitions & submissions |
| Collections | Curated collections |
| Discussions | Discussions & comments |
| Notifications | Notification system |
| Organizations | Organization management |
| Repositories | Repository operations |
| Storage | Storage & file uploads |
| Users | User management |
| Core | Search, offers, and core endpoints |
| Public | Public endpoints (no authentication required) |

## Go SDK

Install with `go get https://github.com/AIOZNetwork/aioz-ai-go-client@latest` (requires Go 1.22+).

**Quick start** — initialize a client and call a service:

```go
package main

import (
    "context"
    "fmt"
    "log"
    "os"

    aiozai "https://github.com/AIOZNetwork/aioz-ai-go-client"
)

func main() {
    client, err := aiozai.NewClient(
        aiozai.WithAPIKey(os.Getenv("AIOZ_AI_API_KEY")),
    )
    if err != nil {
        log.Fatal(err)
    }

    ctx := context.Background()
    _ = ctx
    fmt.Println("client ready — use client.Models(), client.Datasets(), etc.")
}
```

**Configuration** — override the base URL, timeout, and retry policy:

```go
import "time"

client, err := aiozai.NewClient(
    aiozai.WithAPIKey(os.Getenv("AIOZ_AI_API_KEY")),
    aiozai.WithBaseURL("https://api.aiozai.network/api/v1"),
    aiozai.WithTimeout(60 * time.Second),
    aiozai.WithRetryConfig(&aiozai.RetryConfig{
        MaxRetries: 5,
        BaseDelay:  2 * time.Second,
        MaxDelay:   60 * time.Second,
    }),
)
```

**Error handling** — use `errors.As` to inspect typed errors:

```go
import "errors"

var apiErr *aiozai.AiozAPIError
if errors.As(err, &apiErr) {
    fmt.Printf("[%d] %s — %s %s\n", apiErr.StatusCode, apiErr.Message, apiErr.Method, apiErr.Endpoint)
}
```

Full API reference: [go/README.md](go/README.md)

## Python SDK

Install with `pip install aiozai-sdk` (requires Python 3.9+, pydantic >= 2.0).

**Quick start** — initialize a client and call a service:

```python
import os
from aiozai_sdk import AiozClient

client = AiozClient(api_key=os.environ["AIOZ_AI_API_KEY"])

# List models
result = client.models.model.api_key_model_list(body={})
```

**Configuration** — override the base URL, timeout, and retry policy:

```python
from aiozai_sdk import AiozClient, RetryConfig

client = AiozClient(
    api_key=os.environ["AIOZ_AI_API_KEY"],
    base_url="https://api.aiozai.network/api/v1",
    timeout=60.0,
    retry_config=RetryConfig(max_retries=5, base_delay=2.0, max_delay=60.0),
)
```

**Error handling** — catch `AiozAPIError` to inspect status code and message:

```python
from aiozai_sdk import AiozAPIError

try:
    result = client.models.model.api_key_model_id_get(id="model-id")
except AiozAPIError as e:
    print(f"[{e.status_code}] {e.message} — {e.method} {e.endpoint}")
```

Full API reference: [python/README.md](python/README.md)

## TypeScript SDK

Install with `npm install @aiozai/nodejs-client` (requires Node.js 18+).

**Quick start** — create a client and call a service:

```typescript
import { createAiozClient, services } from '@aiozai/nodejs-client'

const { rawClient } = createAiozClient({ apiKey: process.env.AIOZ_AI_API_KEY })

// List models
const models = await services.models.postApiKeyModelList({
  client: rawClient,
  body: { page: 1, limit: 10 },
})
```

**Configuration** — override the base URL, timeout, and retry policy:

```typescript
const { rawClient } = createAiozClient({
  apiKey: process.env.AIOZ_AI_API_KEY,
  baseUrl: 'https://api.aiozai.network/api/v1',
  timeout: 60_000,
  retryConfig: { maxRetries: 5, baseDelay: 2000 },
})
```

**Error handling** — catch `AiozApiError` to inspect status code and message:

```typescript
import { AiozApiError } from '@aiozai/nodejs-client'

try {
  const result = await services.models.getApiKeyModelById({
    client: rawClient,
    path: { id: 'nonexistent' },
  })
} catch (error) {
  if (error instanceof AiozApiError) {
    console.error(`[${error.statusCode}] ${error.message} — ${error.method} ${error.endpoint}`)
  }
}
```

Full API reference: [typescript/README.md](typescript/README.md)

## Authentication

All SDKs authenticate via an API key. Obtain your key from the [AIOZ AI dashboard](https://aiozai.network) and expose it as an environment variable:

```bash
export AIOZ_AI_API_KEY="your-api-key"
```

## Repository Structure

```text
aiozai-sdk-docs/
├── go/               # Go SDK documentation
│   ├── README.md
│   └── docs/         # Per-service API reference
├── python/           # Python SDK documentation
│   ├── README.md
│   └── docs/
└── typescript/       # TypeScript SDK documentation
    ├── README.md
    └── docs/
```

## License

Apache-2.0
