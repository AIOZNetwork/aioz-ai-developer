# AIOZ AI SDK for Python

Python client library for the [AIOZ AI](https://aiozai.network) API. Auto-generated from the Swagger 2.0 specification with typed Pydantic v2 models.

## Installation

```bash
pip install aiozai-sdk
```

## Quick Start

```python
from aiozai_sdk import AiozClient

client = AiozClient(api_key="your-api-key")

# Access services
result = client.models.model.api_key_model_list(body={...})
```

## Error Handling

```python
from aiozai_sdk import AiozAPIError

try:
    result = client.models.model.api_key_model_id_get(id="model-id")
except AiozAPIError as e:
    print(f"[{e.status_code}] {e.message} — {e.method} {e.endpoint}")
```

## Configuration

```python
from aiozai_sdk import AiozClient, RetryConfig

client = AiozClient(
    api_key="your-api-key",
    base_url="https://api.aiozai.network/api/v1",
    timeout=60.0,
    retry_config=RetryConfig(max_retries=5, base_delay=2.0, max_delay=60.0),
)
```

## Service Groups

| Service | Access | Description | Reference |
| --- | --- | --- | --- |
| Models | `client.models` | AI model management | [docs/models.md](docs/models.md) |
| Datasets | `client.datasets` | Dataset management | [docs/datasets.md](docs/datasets.md) |
| Competitions | `client.competitions` | Competitions & submissions | [docs/competitions.md](docs/competitions.md) |
| Collections | `client.collections` | Curated collections | [docs/collections.md](docs/collections.md) |
| Discussions | `client.discussions` | Discussions & comments | [docs/discussions.md](docs/discussions.md) |
| Notifications | `client.notifications` | Notification system | [docs/notifications.md](docs/notifications.md) |
| Organizations | `client.organizations` | Organization management | [docs/organizations.md](docs/organizations.md) |
| Repositories | `client.repositories` | Repository operations | [docs/repositories.md](docs/repositories.md) |
| Storage | `client.storage` | Storage & uploads | [docs/storage.md](docs/storage.md) |
| Users | `client.users` | User management | [docs/users.md](docs/users.md) |
| Core | `client.core` | Core endpoints, search, offers | [docs/core.md](docs/core.md) |
| Public | `client.public` | Public endpoints (no auth) | [docs/public.md](docs/public.md) |

## Requirements

- Python 3.9+
- pydantic >= 2.0
- urllib3 >= 2.0
- tenacity >= 8.0

## License

Apache 2.0

<!-- SDK_GUIDE_START -->

---

## SDK Usage Guide

> Auto-generated from `swagger/sdk.json` — do not edit this section manually.
> Re-generate with `make guide` from the repo root.

### Authentication Setup

Initialize the client once with your API key and reuse it across all calls:

```python
import os
from aiozai_sdk import AiozClient

client = AiozClient(api_key=os.environ["AIOZ_API_KEY"])

# Use client.models, client.datasets, etc.
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
