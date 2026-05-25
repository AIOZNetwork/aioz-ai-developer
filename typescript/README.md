# @aioz-network/aiozai-sdk

TypeScript SDK for the [AIOZ AI](https://aiozai.network) API. Auto-generated from the OpenAPI specification with full type safety.

## Features

- Full TypeScript types for all 218 API endpoints and 578 models
- Automatic retry with exponential backoff for transient failures
- Tree-shakeable ESM and CJS builds
- Zero runtime dependencies beyond the fetch API

## Installation

```bash
npm install @aioz-network/aiozai-sdk
```

## Quick Start

```typescript
import { createAiozClient, services } from '@aioz-network/aiozai-sdk'

const { rawClient } = createAiozClient({ apiKey: process.env.AIOZ_API_KEY })

// List models
const models = await services.models.postApiKeyModelList({
  client: rawClient,
  body: { page: 1, limit: 10 },
})

// Get a specific model
const model = await services.models.getApiKeyModelById({
  client: rawClient,
  path: { id: 'your-model-id' },
})
```

## Error Handling

```typescript
import { AiozApiError } from '@aioz-network/aiozai-sdk'

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

## Configuration

```typescript
const { rawClient } = createAiozClient({
  apiKey: process.env.AIOZ_API_KEY,
  baseUrl: 'https://custom-api.example.com/api/v1',
  timeout: 60_000,
  retryConfig: { maxRetries: 5, baseDelay: 2000 },
})
```

## Service Groups

| Service | Description | Reference |
| --- | --- | --- |
| `services.models` | AI model management | [docs/models.md](docs/models.md) |
| `services.datasets` | Dataset management | [docs/datasets.md](docs/datasets.md) |
| `services.competitions` | Competitions & submissions | [docs/competitions.md](docs/competitions.md) |
| `services.collections` | Curated collections | [docs/collections.md](docs/collections.md) |
| `services.discussions` | Discussions & comments | [docs/discussions.md](docs/discussions.md) |
| `services.notifications` | Notification system | [docs/notifications.md](docs/notifications.md) |
| `services.organizations` | Organization management | [docs/organizations.md](docs/organizations.md) |
| `services.repositories` | Repository operations | [docs/repositories.md](docs/repositories.md) |
| `services.storage` | Storage & uploads | [docs/storage.md](docs/storage.md) |
| `services.users` | User management | [docs/users.md](docs/users.md) |
| `services.core` | Core endpoints, search, offers | [docs/core.md](docs/core.md) |
| `services.public_` | Public endpoints (no auth) | [docs/public.md](docs/public.md) |

## Requirements

Node.js >= 18

## License

Apache-2.0

<!-- SDK_GUIDE_START -->

---

## SDK Usage Guide

> Auto-generated from `swagger/sdk.json` — do not edit this section manually.
> Re-generate with `make guide` from the repo root.

### Authentication Setup

Initialize the client once with your API key and reuse it across all calls:

```typescript
import { createAiozClient } from '@aioz-network/aiozai-sdk'

const { rawClient } = createAiozClient({ apiKey: process.env.AIOZ_API_KEY })

// Pass rawClient to every service call:
// services.models.postApiKeyModel({ client: rawClient, body: { ... } })
```

Obtain your API key from the [AIOZ AI dashboard](https://aiozai.network).

### Common Response Types

These types appear in error responses across all endpoints.

**`FailResponse`** (400 Bad Request)

| Field | Type | Description |
| --- | --- | --- |
| `message` | `string` | Human-readable error message |
| `errors` | `array[string]` | Field-level validation errors |

**`ErrorResponse`** (500 Internal Server Error)

| Field | Type | Description |
| --- | --- | --- |
| `message` | `string` | Internal error message |

<!-- SDK_GUIDE_END -->
