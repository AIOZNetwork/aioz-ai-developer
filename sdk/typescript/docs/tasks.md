# Tasks — TypeScript SDK

> Tasks management — submit, track, and review AI tasks. Requires: `x-api-key` header.

Reference: [SDK Usage Guide](../README.md#sdk-usage-guide) | [Package README](../README.md)

---

### `getModelTaskByIdReviews`

**`GET /api-key/model/task/{id}/reviews`** — Get Task Review By Task Id

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Task's id |

**Responses**

**200 OK** — `response.TaskReviewsResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.TaskReviews` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.TaskReviews`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `id` | `string` |  |
| `model_id` | `string` |  |
| `owner` | `models.Owner` |  |
| `point` | `integer` |  |
| `result` | `map[string]any` |  |
| `task_id` | `string` |  |
| `updated_at` | `string` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { createAiozAIClient, services } from '@aiozai/nodejs-client';

const { rawClient } = createAiozAIClient({ apiKey: process.env.AIOZ_AI_API_KEY });

const response = await services.tasks.getModelTaskByIdReviews({
    client: rawClient,
    path: { id: '...' },
});
console.log(response.data);
```

---

### `postModelByIdTask`

**`POST /api-key/model/{id}/task`** — Distribute Task v2

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |

**Request Body** — `request.DistributeTaskWithApiKeyRequest`

_No fields defined._

**Responses**

**200 OK** — `response.DistributeTaskResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `string` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { createAiozAIClient, services } from '@aiozai/nodejs-client';

const { rawClient } = createAiozAIClient({ apiKey: process.env.AIOZ_AI_API_KEY });

const response = await services.tasks.postModelByIdTask({
    client: rawClient,
    body: {
        
    },
});
console.log(response.data);
```

---

### `postModelByIdTaskReviews`

**`POST /api-key/model/{id}/task/reviews`** — Create Task Reviews

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |

**Request Body** — `request.CreateTaskReviewsRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `description` | `string` | No |  |
| `point` | `integer` | Yes |  |
| `task_id` | `string` | Yes |  |

**Responses**

**200 OK** — `response.TaskReviewsResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.TaskReviews` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.TaskReviews`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `id` | `string` |  |
| `model_id` | `string` |  |
| `owner` | `models.Owner` |  |
| `point` | `integer` |  |
| `result` | `map[string]any` |  |
| `task_id` | `string` |  |
| `updated_at` | `string` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { createAiozAIClient, services } from '@aiozai/nodejs-client';

const { rawClient } = createAiozAIClient({ apiKey: process.env.AIOZ_AI_API_KEY });

const response = await services.tasks.postModelByIdTaskReviews({
    client: rawClient,
    body: {
        description: '...',  // string
        point: '...',  // integer  // required
        task_id: '...',  // string  // required
    },
});
console.log(response.data);
```

---

### `getPlatformTaskById`

**`GET /api-key/platform/task/{id}`** — Get Platform Task By Id

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Task's Id |

**Responses**

**200 OK** — `response.QueueTaskResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.QueueTask` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.QueueTask`**

| Field | Type | Description |
| --- | --- | --- |
| `action` | `string` |  |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `object_id` | `string` |  |
| `object_name` | `string` |  |
| `result` | `map[string]any` |  |
| `state` | `string` |  |
| `updated_at` | `string` |  |
| `user_id` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { createAiozAIClient, services } from '@aiozai/nodejs-client';

const { rawClient } = createAiozAIClient({ apiKey: process.env.AIOZ_AI_API_KEY });

const response = await services.tasks.getPlatformTaskById({
    client: rawClient,
    path: { id: '...' },
});
console.log(response.data);
```

---

### `postTask`

**`POST /api-key/task`** — Distribute Task

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.DistributeTaskRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `files` | `array[object]` | No |  |
| `input_params` | `map[string]any` | No |  |
| `model_id` | `string` | No |  |

**Responses**

**200 OK** — `response.DistributeTaskResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `string` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { createAiozAIClient, services } from '@aiozai/nodejs-client';

const { rawClient } = createAiozAIClient({ apiKey: process.env.AIOZ_AI_API_KEY });

const response = await services.tasks.postTask({
    client: rawClient,
    body: {
        files: '...',  // array[object]
        input_params: '...',  // map[string]any
        model_id: '...',  // string
    },
});
console.log(response.data);
```

---

### `getTaskHistories`

**`GET /api-key/task/histories`** — Get Tasks Histories

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |

**Responses**

**200 OK** — `response.ApiKeyHistoryListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.ApiKeyHistoryListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.ApiKeyHistoryListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.ApiKeyHistories]` |  |
| `total` | `integer` |  |

**`models.ApiKeyHistories`**

| Field | Type | Description |
| --- | --- | --- |
| `cost` | `number` |  |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `input_data` | `map[string]any` |  |
| `input_format` | `map[string]any` |  |
| `message` | `string` |  |
| `output_format` | `map[string]any` |  |
| `result` | `models.InferenceResult` |  |
| `status` | `string` |  |
| `task_id` | `string` |  |
| `updated_at` | `string` |  |

**`models.InferenceResult`**

| Field | Type | Description |
| --- | --- | --- |
| `error` | `map[string]any` |  |
| `result` | `map[string]any` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { createAiozAIClient, services } from '@aiozai/nodejs-client';

const { rawClient } = createAiozAIClient({ apiKey: process.env.AIOZ_AI_API_KEY });

const response = await services.tasks.getTaskHistories({ client: rawClient });
console.log(response.data);
```

---

### `deleteTaskByIdCancel`

**`DELETE /api-key/task/{id}/cancel`** — Cancel Task

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Task's id |

**Responses**

**200 OK** — `response.SuccessResponse`

| Field | Type | Description |
| --- | --- | --- |
| `message` | `string` |  |
| `status` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { createAiozAIClient, services } from '@aiozai/nodejs-client';

const { rawClient } = createAiozAIClient({ apiKey: process.env.AIOZ_AI_API_KEY });

const response = await services.tasks.deleteTaskByIdCancel({
    client: rawClient,
    path: { id: '...' },
});
console.log(response.data);
```

---

### `getTaskByIdDetail`

**`GET /api-key/task/{id}/detail`** — Get Api Key Log By TaskId

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Task's id |

**Responses**

**200 OK** — `response.ApiKeyHistoryResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.ApiKeyHistories` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.ApiKeyHistories`**

| Field | Type | Description |
| --- | --- | --- |
| `cost` | `number` |  |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `input_data` | `map[string]any` |  |
| `input_format` | `map[string]any` |  |
| `message` | `string` |  |
| `output_format` | `map[string]any` |  |
| `result` | `models.InferenceResult` |  |
| `status` | `string` |  |
| `task_id` | `string` |  |
| `updated_at` | `string` |  |

**`models.InferenceResult`**

| Field | Type | Description |
| --- | --- | --- |
| `error` | `map[string]any` |  |
| `result` | `map[string]any` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { createAiozAIClient, services } from '@aiozai/nodejs-client';

const { rawClient } = createAiozAIClient({ apiKey: process.env.AIOZ_AI_API_KEY });

const response = await services.tasks.getTaskByIdDetail({
    client: rawClient,
    path: { id: '...' },
});
console.log(response.data);
```

---
