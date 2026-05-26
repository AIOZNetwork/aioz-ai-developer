# @aiozai/nodejs-client

TypeScript SDK for the [AIOZ AI](https://aiozai.network) API. Auto-generated from the OpenAPI specification with full type safety.

## Features

- Full TypeScript types for all 218 API endpoints and 578 models
- Automatic retry with exponential backoff for transient failures
- Tree-shakeable ESM and CJS builds
- Zero runtime dependencies beyond the fetch API

## Installation

```bash
npm install @aiozai/nodejs-client
```

## Quick Start

```typescript
import { createAiozAIClient, services } from '@aiozai/nodejs-client'

const { rawClient } = createAiozAIClient({ apiKey: process.env.AIOZ_AI_API_KEY })

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

## Configuration

```typescript
const { rawClient } = createAiozAIClient({
  apiKey: process.env.AIOZ_AI_API_KEY,
  baseUrl: 'https://api.aiozai.network/api/v1',
  timeout: 60_000,
  retryConfig: { maxRetries: 5, baseDelay: 2000 },
})
```

## Service Groups

| Service | Access | Description | Reference |
| --- | --- | --- | --- |
| Models | `client.models` | AI model management | [docs/models.md](https://github.com/AIOZNetwork/aioz-ai-sdk/blob/main/typescript/docs/models.md) |
| Datasets | `client.datasets` | Dataset management | [docs/datasets.md](https://github.com/AIOZNetwork/aioz-ai-sdk/blob/main/typescript/docs/datasets.md) |
| Competitions | `client.competitions` | Competitions & submissions | [docs/competitions.md](https://github.com/AIOZNetwork/aioz-ai-sdk/blob/main/typescript/docs/competitions.md) |
| Collections | `client.collections` | Curated collections | [docs/collections.md](https://github.com/AIOZNetwork/aioz-ai-sdk/blob/main/typescript/docs/collections.md) |
| Discussions | `client.discussions` | Discussions & comments | [docs/discussions.md](https://github.com/AIOZNetwork/aioz-ai-sdk/blob/main/typescript/docs/discussions.md) |
| Notifications | `client.notifications` | Notification system | [docs/notifications.md](https://github.com/AIOZNetwork/aioz-ai-sdk/blob/main/typescript/docs/notifications.md) |
| Organizations | `client.organizations` | Organization management | [docs/organizations.md](https://github.com/AIOZNetwork/aioz-ai-sdk/blob/main/typescript/docs/organizations.md) |
| Repositories | `client.repositories` | Repository operations | [docs/repositories.md](https://github.com/AIOZNetwork/aioz-ai-sdk/blob/main/typescript/docs/repositories.md) |
| Storage | `client.storage` | Storage & uploads | [docs/storage.md](https://github.com/AIOZNetwork/aioz-ai-sdk/blob/main/typescript/docs/storage.md) |
| Users | `client.users` | User management | [docs/users.md](https://github.com/AIOZNetwork/aioz-ai-sdk/blob/main/typescript/docs/users.md) |
| Core | `client.core` | Core endpoints, search, offers | [docs/core.md](https://github.com/AIOZNetwork/aioz-ai-sdk/blob/main/typescript/docs/core.md) |
| Public | `client.public` | Public endpoints (no auth) | [docs/public.md](https://github.com/AIOZNetwork/aioz-ai-sdk/blob/main/typescript/docs/public.md) |

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
import { createAiozAIClient } from '@aiozai/nodejs-client'

const { rawClient } = createAiozAIClient({ apiKey: process.env.AIOZ_AI_API_KEY })

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
