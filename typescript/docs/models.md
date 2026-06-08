# Models — TypeScript SDK

> AI model management — create, train, deploy, and version models. Requires: `x-api-key` header.

Reference: [SDK Usage Guide](../README.md#sdk-usage-guide) | [Package README](../README.md)

---

### `postModel`

**`POST /api-key/model`** — Create Model

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.CreateModelRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `author_id` | `string` | No |  |
| `cover` | `string` | No |  |
| `dependency_id` | `string` | No |  |
| `description` | `string` | No |  |
| `language` | `array[string]` | No | en, vi |
| `library` | `array[string]` | No | tf |
| `license` | `string` | Yes |  |
| `name` | `string` | Yes |  |
| `pretty_name` | `string` | No |  |
| `price` | `number` | No |  |
| `task` | `string` | No |  |
| `thumbnail` | `string` | No |  |
| `visibility` | `string` | Yes | One of: `public`, `private` |

**Responses**

**200 OK** — `response.ModelResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.ModelData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.ModelData`**

| Field | Type | Description |
| --- | --- | --- |
| `author` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `downloads` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `likes` | `integer` |  |
| `name` | `string` |  |
| `updated_at` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { postModel } from '@aiozai/nodejs-client';

const response = await postModel({
    body: {
        author_id: '...',  // string
    cover: '...',  // string
    dependency_id: '...',  // string
    description: '...',  // string
    language: '...',  // array[string]
    },
});
console.log(response.data);
```

---

### `postModelList`

**`POST /api-key/model/list`** — Get Model List

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.GetModelListRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `filter_by` | `string` | No | One of: `public`, `community`, `author`, `official`, `permission`, `playground` |
| `language` | `array[string]` | No |  |
| `library` | `array[string]` | No |  |
| `license` | `string` | No |  |
| `limit` | `integer` | No |  |
| `offset` | `integer` | No |  |
| `order` | `string` | No | One of: `asc`, `desc` |
| `search` | `string` | No |  |
| `sort` | `string` | No | One of: `trending`, `likes`, `downloads`, `created`, `created_oldest`, `modified`, `name`, `size` |
| `tag_type` | `string` | No |  |
| `task` | `string` | No |  |

**Responses**

**200 OK** — `response.ModelListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.ModelListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.ModelListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Model]` |  |
| `total` | `integer` |  |

**`models.Model`**

| Field | Type | Description |
| --- | --- | --- |
| `author_avatar` | `string` |  |
| `author_id` | `string` |  |
| `commit_hash` | `string` |  |
| `cover` | `string` |  |
| `create_by` | `string` |  |
| `created_at` | `string` |  |
| `dependency_id` | `string` |  |
| `description` | `string` |  |
| `discussions_count` | `integer` |  |
| `downloads_count` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `is_official` | `boolean` |  |
| `is_released` | `boolean` |  |
| `is_verified` | `boolean` |  |
| `likes_count` | `integer` |  |
| `model_metadata` | `models.ModelMetadata` |  |
| `name` | `string` |  |
| `playground_count` | `integer` |  |
| `price` | `number` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `task_reviews_count` | `integer` |  |
| `task_reviews_point` | `number` |  |
| `thumbnail` | `string` |  |
| `updated_at` | `string` |  |
| `username` | `string` |  |
| `visibility` | `string` |  |

**`models.ModelMetadata`**

| Field | Type | Description |
| --- | --- | --- |
| `id` | `string` |  |
| `license` | `string` |  |
| `model_id` | `string` |  |
| `pretty_name` | `string` |  |
| `task` | `string` |  |

**`models.Reaction`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `string` |  |
| `name` | `string` |  |
| `owner` | `models.Owner` |  |
| `updated_at` | `string` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

**`models.ReactionStats`**

| Field | Type | Description |
| --- | --- | --- |
| `count` | `integer` |  |
| `name` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { postModelList } from '@aiozai/nodejs-client';

const response = await postModelList({
    body: {
        filter_by: '...',  // string
    language: '...',  // array[string]
    library: '...',  // array[string]
    license: '...',  // string
    limit: '...',  // integer
    },
});
console.log(response.data);
```

---

### `postModelListByAuthorByUsername`

**`POST /api-key/model/list-by-author/{username}`** — Get Model List By User

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `username` | path | `string` | Yes | User's username |

**Request Body** — `request.GetModelListByAuthorRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `language` | `array[string]` | No |  |
| `library` | `array[string]` | No |  |
| `license` | `string` | No |  |
| `limit` | `integer` | No |  |
| `offset` | `integer` | No |  |
| `order` | `string` | No | One of: `asc`, `desc` |
| `search` | `string` | No |  |
| `sort` | `string` | No | One of: `trending`, `likes`, `downloads`, `created`, `created_oldest`, `modified`, `name`, `size` |
| `tag_type` | `string` | No |  |
| `task` | `string` | No |  |

**Responses**

**200 OK** — `response.ModelListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.ModelListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.ModelListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Model]` |  |
| `total` | `integer` |  |

**`models.Model`**

| Field | Type | Description |
| --- | --- | --- |
| `author_avatar` | `string` |  |
| `author_id` | `string` |  |
| `commit_hash` | `string` |  |
| `cover` | `string` |  |
| `create_by` | `string` |  |
| `created_at` | `string` |  |
| `dependency_id` | `string` |  |
| `description` | `string` |  |
| `discussions_count` | `integer` |  |
| `downloads_count` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `is_official` | `boolean` |  |
| `is_released` | `boolean` |  |
| `is_verified` | `boolean` |  |
| `likes_count` | `integer` |  |
| `model_metadata` | `models.ModelMetadata` |  |
| `name` | `string` |  |
| `playground_count` | `integer` |  |
| `price` | `number` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `task_reviews_count` | `integer` |  |
| `task_reviews_point` | `number` |  |
| `thumbnail` | `string` |  |
| `updated_at` | `string` |  |
| `username` | `string` |  |
| `visibility` | `string` |  |

**`models.ModelMetadata`**

| Field | Type | Description |
| --- | --- | --- |
| `id` | `string` |  |
| `license` | `string` |  |
| `model_id` | `string` |  |
| `pretty_name` | `string` |  |
| `task` | `string` |  |

**`models.Reaction`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `string` |  |
| `name` | `string` |  |
| `owner` | `models.Owner` |  |
| `updated_at` | `string` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

**`models.ReactionStats`**

| Field | Type | Description |
| --- | --- | --- |
| `count` | `integer` |  |
| `name` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { postModelListByAuthorByUsername } from '@aiozai/nodejs-client';

const response = await postModelListByAuthorByUsername({
    body: {
        language: '...',  // array[string]
    library: '...',  // array[string]
    license: '...',  // string
    limit: '...',  // integer
    offset: '...',  // integer
    },
});
console.log(response.data);
```

---

### `postModelMatchingTags`

**`POST /api-key/model/matching-tags`** — MatchingModels Tags

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.MatchingModelsTagsRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `language` | `array[string]` | No |  |
| `library` | `array[string]` | No |  |
| `license` | `string` | No |  |
| `tag_type` | `string` | No |  |
| `task` | `string` | No |  |

**Responses**

**200 OK** — `response.ListDataResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `array[string]` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { postModelMatchingTags } from '@aiozai/nodejs-client';

const response = await postModelMatchingTags({
    body: {
        language: '...',  // array[string]
    library: '...',  // array[string]
    license: '...',  // string
    tag_type: '...',  // string
    task: '...',  // string
    },
});
console.log(response.data);
```

---

### `getModelOrganizationByOrg`

**`GET /api-key/model/organization/{org}`** — Get List Model By Org Username

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `org` | path | `string` | Yes | Org's username |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |
| `sort` | query | `string` | No |  |

**Responses**

**200 OK** — `response.ModelListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.ModelListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.ModelListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Model]` |  |
| `total` | `integer` |  |

**`models.Model`**

| Field | Type | Description |
| --- | --- | --- |
| `author_avatar` | `string` |  |
| `author_id` | `string` |  |
| `commit_hash` | `string` |  |
| `cover` | `string` |  |
| `create_by` | `string` |  |
| `created_at` | `string` |  |
| `dependency_id` | `string` |  |
| `description` | `string` |  |
| `discussions_count` | `integer` |  |
| `downloads_count` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `is_official` | `boolean` |  |
| `is_released` | `boolean` |  |
| `is_verified` | `boolean` |  |
| `likes_count` | `integer` |  |
| `model_metadata` | `models.ModelMetadata` |  |
| `name` | `string` |  |
| `playground_count` | `integer` |  |
| `price` | `number` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `task_reviews_count` | `integer` |  |
| `task_reviews_point` | `number` |  |
| `thumbnail` | `string` |  |
| `updated_at` | `string` |  |
| `username` | `string` |  |
| `visibility` | `string` |  |

**`models.ModelMetadata`**

| Field | Type | Description |
| --- | --- | --- |
| `id` | `string` |  |
| `license` | `string` |  |
| `model_id` | `string` |  |
| `pretty_name` | `string` |  |
| `task` | `string` |  |

**`models.Reaction`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `string` |  |
| `name` | `string` |  |
| `owner` | `models.Owner` |  |
| `updated_at` | `string` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

**`models.ReactionStats`**

| Field | Type | Description |
| --- | --- | --- |
| `count` | `integer` |  |
| `name` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getModelOrganizationByOrg } from '@aiozai/nodejs-client';

const response = await getModelOrganizationByOrg({ path: { org: '...' } });
console.log(response.data);
```

---

### `deleteModelTaskReviewsById`

**`DELETE /api-key/model/task/reviews/{id}`** — Delete Task Reviews By Id

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Task Review's id |

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
import { deleteModelTaskReviewsById } from '@aiozai/nodejs-client';

const response = await deleteModelTaskReviewsById({ path: { id: '...' } });
console.log(response.data);
```

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

**Request Body** — `request.GetTaskReviewByTaskIdRequest`

_No fields defined._

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
import { getModelTaskByIdReviews } from '@aiozai/nodejs-client';

const response = await getModelTaskByIdReviews({
    body: {
        
    },
});
console.log(response.data);
```

---

### `postModelTrainingCost`

**`POST /api-key/model/training/cost`** — Calculate Cost To Training Ai Model

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.CalculateCostToTrainingAiModelRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `dataset_id` | `string` | No |  |
| `training_task_id` | `string` | No |  |

**Responses**

**200 OK** — `response.EstimateCostResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.EstimateCostData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.EstimateCostData`**

| Field | Type | Description |
| --- | --- | --- |
| `cost` | `number` |  |
| `symbol` | `string` |  |
| `unit` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { postModelTrainingCost } from '@aiozai/nodejs-client';

const response = await postModelTrainingCost({
    body: {
        dataset_id: '...',  // string
    training_task_id: '...',  // string
    },
});
console.log(response.data);
```

---

### `getModelTrainingTask`

**`GET /api-key/model/training/task`** — Get List User Training Task

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.GetListUserTrainingTaskRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `limit` | `integer` | No |  |
| `offset` | `integer` | No |  |

**Responses**

**200 OK** — `response.UserTrainingTaskListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.UserTrainingTaskListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.UserTrainingTaskListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.UserTrainingTask]` |  |
| `total` | `integer` |  |

**`models.UserTrainingTask`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `string` |  |
| `dataset_id` | `string` |  |
| `dataset_repo_size` | `number` |  |
| `dataset_repo_url` | `string` |  |
| `dataset_sha` | `string` |  |
| `id` | `string` |  |
| `task_id` | `string` |  |
| `training_data` | `map[string]any` |  |
| `training_metadata` | `map[string]any` |  |
| `updated_at` | `string` |  |
| `user_id` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getModelTrainingTask } from '@aiozai/nodejs-client';

const response = await getModelTrainingTask({
    body: {
        limit: '...',  // integer
    offset: '...',  // integer
    },
});
console.log(response.data);
```

---

### `deleteModelTrainingTaskById`

**`DELETE /api-key/model/training/task/{id}`** — Delete User Training Task By Task Id

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Training Task's id |

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
import { deleteModelTrainingTaskById } from '@aiozai/nodejs-client';

const response = await deleteModelTrainingTaskById({ path: { id: '...' } });
console.log(response.data);
```

---

### `getModelVerifyHubTaskById`

**`GET /api-key/model/verify/hub/task/{id}`** — Get Model Versioning By Hub Task Id

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Hub Task's id |

**Responses**

**200 OK** — `response.ModelVersioningResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.ModelVersioning` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.ModelVersioning`**

| Field | Type | Description |
| --- | --- | --- |
| `commit_hash` | `string` |  |
| `commit_message` | `string` |  |
| `created_at` | `string` |  |
| `dependency` | `map[string]any` |  |
| `id` | `string` |  |
| `input_format` | `map[string]any` |  |
| `model_id` | `string` |  |
| `node_reward` | `number` |  |
| `output_format` | `map[string]any` |  |
| `platform` | `string` |  |
| `sys_require` | `map[string]any` |  |
| `test_result` | `map[string]any` |  |
| `updated_at` | `string` |  |
| `verify_status` | `string` |  |
| `verify_task_id` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getModelVerifyHubTaskById } from '@aiozai/nodejs-client';

const response = await getModelVerifyHubTaskById({ path: { id: '...' } });
console.log(response.data);
```

---

### `getModelVerifySupportPlatforms`

**`GET /api-key/model/verify/support/platforms`** — Get List Platforms Support

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Responses**

**200 OK** — `response.GetListPlatformSupportResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `array[string]` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getModelVerifySupportPlatforms } from '@aiozai/nodejs-client';

const response = await getModelVerifySupportPlatforms();
console.log(response.data);
```

---

### `getModelById`

**`GET /api-key/model/{id}`** — Get Model

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |

**Responses**

**200 OK** — `response.ModelResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.ModelData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.ModelData`**

| Field | Type | Description |
| --- | --- | --- |
| `author` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `downloads` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `likes` | `integer` |  |
| `name` | `string` |  |
| `updated_at` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getModelById } from '@aiozai/nodejs-client';

const response = await getModelById({ path: { id: '...' } });
console.log(response.data);
```

---

### `putModelById`

**`PUT /api-key/model/{id}`** — Update Model

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |

**Request Body** — `request.UpdateModelRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `cover` | `string` | No |  |
| `dependency_id` | `string` | No |  |
| `description` | `string` | No |  |
| `price` | `number` | No |  |
| `thumbnail` | `string` | No |  |
| `visibility` | `string` | No |  |

**Responses**

**200 OK** — `response.ModelResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.ModelData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.ModelData`**

| Field | Type | Description |
| --- | --- | --- |
| `author` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `downloads` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `likes` | `integer` |  |
| `name` | `string` |  |
| `updated_at` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { putModelById } from '@aiozai/nodejs-client';

const response = await putModelById({
    body: {
        cover: '...',  // string
    dependency_id: '...',  // string
    description: '...',  // string
    price: '...',  // number
    thumbnail: '...',  // string
    },
});
console.log(response.data);
```

---

### `deleteModelById`

**`DELETE /api-key/model/{id}`** — Delete Model

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |

**Request Body** — `request.DeleteModelRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `name` | `string` | Yes |  |

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
import { deleteModelById } from '@aiozai/nodejs-client';

const response = await deleteModelById({
    body: {
        name: '...',  // string  // required
    },
});
console.log(response.data);
```

---

### `getModelByIdApiKey`

**`GET /api-key/model/{id}/api-key`** — Get List Model ApiKey

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |

**Responses**

**200 OK** — `response.ListApiKeyResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.ListApiKeyData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.ListApiKeyData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.LiteApiKey]` |  |
| `total` | `integer` |  |

**`models.LiteApiKey`**

| Field | Type | Description |
| --- | --- | --- |
| `active` | `boolean` |  |
| `api_key` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `id` | `string` |  |
| `model_id` | `string` |  |
| `name` | `string` |  |
| `updated_at` | `string` |  |
| `user_id` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getModelByIdApiKey } from '@aiozai/nodejs-client';

const response = await getModelByIdApiKey({ path: { id: '...' } });
console.log(response.data);
```

---

### `postModelByIdApiKey`

**`POST /api-key/model/{id}/api-key`** — Create Model ApiKey

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |

**Request Body** — `request.CreateApiKeyRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `active` | `boolean` | No |  |
| `description` | `string` | No |  |
| `name` | `string` | Yes |  |
| `org_username` | `string` | No |  |

**Responses**

**200 OK** — `response.ApiKeyResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.ApiKey` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.ApiKey`**

| Field | Type | Description |
| --- | --- | --- |
| `active` | `boolean` |  |
| `api_key` | `string` |  |
| `api_price` | `number` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `id` | `string` |  |
| `input_format` | `map[string]any` |  |
| `model_id` | `string` |  |
| `name` | `string` |  |
| `output_format` | `map[string]any` |  |
| `total_cost` | `number` |  |
| `total_failed` | `integer` |  |
| `total_request` | `integer` |  |
| `total_success` | `integer` |  |
| `updated_at` | `string` |  |
| `user` | `models.User` |  |
| `user_id` | `string` |  |

**`models.User`**

| Field | Type | Description |
| --- | --- | --- |
| `allow_request_to_join` | `boolean` |  |
| `avatar_url` | `string` |  |
| `bio` | `string` |  |
| `blocked` | `boolean` |  |
| `blocked_at` | `string` |  |
| `email` | `string` |  |
| `followers` | `array[models.Follow]` |  |
| `followers_count` | `integer` |  |
| `followings` | `array[models.Follow]` |  |
| `followings_count` | `integer` |  |
| `github_link` | `string` |  |
| `github_name` | `string` |  |
| `home_page_name` | `string` |  |
| `id` | `string` |  |
| `interests` | `string` |  |
| `invite_offers` | `array[models.Offer]` |  |
| `invite_offers_count` | `integer` |  |
| `is_following` | `boolean` |  |
| `join_id` | `string` |  |
| `join_offers` | `array[models.Offer]` |  |
| `join_offers_count` | `integer` |  |
| `members` | `array[models.Member]` |  |
| `members_count` | `integer` |  |
| `name` | `string` |  |
| `role` | `string` |  |
| `token` | `string` |  |
| `twitter_link` | `string` |  |
| `twitter_name` | `string` |  |
| `type` | `string` |  |
| `username` | `string` |  |
| `verified` | `boolean` |  |
| `visibility` | `string` |  |
| `wallet` | `models.Wallet` |  |
| `wallet_address` | `string` |  |
| `wallet_connection` | `string` |  |

**`models.Follow`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `name` | `string` |  |
| `username` | `string` |  |

**`models.Follow`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `name` | `string` |  |
| `username` | `string` |  |

**`models.Offer`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `integer` |  |
| `created_by` | `string` |  |
| `exp_at` | `integer` |  |
| `id` | `string` |  |
| `org_username` | `string` |  |
| `role` | `string` |  |
| `type` | `string` |  |
| `username` | `string` |  |

**`models.Offer`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `integer` |  |
| `created_by` | `string` |  |
| `exp_at` | `integer` |  |
| `id` | `string` |  |
| `org_username` | `string` |  |
| `role` | `string` |  |
| `type` | `string` |  |
| `username` | `string` |  |

**`models.Member`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar_url` | `string` |  |
| `full_name` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

**`models.Wallet`**

| Field | Type | Description |
| --- | --- | --- |
| `balance` | `string` |  |
| `debt` | `string` |  |
| `earnings` | `string` |  |
| `free_balance` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { postModelByIdApiKey } from '@aiozai/nodejs-client';

const response = await postModelByIdApiKey({
    body: {
        active: '...',  // boolean
    description: '...',  // string
    name: '...',  // string  // required
    org_username: '...',  // string
    },
});
console.log(response.data);
```

---

### `getModelByIdDownload`

**`GET /api-key/model/{id}/download`** — Get List Model Download

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |

**Responses**

**200 OK** — `response.DownloadModelListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.DownloadModelListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.DownloadModelListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.LiteDownloadModel]` |  |
| `total` | `integer` |  |

**`models.LiteDownloadModel`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `owner` | `models.Owner` |  |

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
import { getModelByIdDownload } from '@aiozai/nodejs-client';

const response = await getModelByIdDownload({ path: { id: '...' } });
console.log(response.data);
```

---

### `getModelByIdInfo`

**`GET /api-key/model/{id}/info`** — Get Api Key Model Info

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |

**Responses**

**200 OK** — `response.ApiKeyInfoResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.ApiKeyInfo` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.ApiKeyInfo`**

| Field | Type | Description |
| --- | --- | --- |
| `api_price` | `number` |  |
| `commit_hash` | `string` |  |
| `input_format` | `map[string]any` |  |
| `model_description` | `string` |  |
| `model_id` | `string` |  |
| `output_format` | `map[string]any` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getModelByIdInfo } from '@aiozai/nodejs-client';

const response = await getModelByIdInfo({ path: { id: '...' } });
console.log(response.data);
```

---

### `getModelByIdLike`

**`GET /api-key/model/{id}/like`** — Get List Model Like

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |

**Responses**

**200 OK** — `response.LikeModelListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.LikeModelListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.LikeModelListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.LiteLikeModel]` |  |
| `total` | `integer` |  |

**`models.LiteLikeModel`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `owner` | `models.Owner` |  |

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
import { getModelByIdLike } from '@aiozai/nodejs-client';

const response = await getModelByIdLike({ path: { id: '...' } });
console.log(response.data);
```

---

### `putModelByIdMetadata`

**`PUT /api-key/model/{id}/metadata`** — Update Model Metadata

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |

**Request Body** — `request.UpdateModelMetadataRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `language` | `array[string]` | No | en, vi |
| `library` | `array[string]` | No | tf, jax |
| `license` | `string` | No |  |
| `pretty_name` | `string` | No |  |
| `task` | `string` | No |  |

**Responses**

**200 OK** — `response.ModelResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.ModelData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.ModelData`**

| Field | Type | Description |
| --- | --- | --- |
| `author` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `downloads` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `likes` | `integer` |  |
| `name` | `string` |  |
| `updated_at` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { putModelByIdMetadata } from '@aiozai/nodejs-client';

const response = await putModelByIdMetadata({
    body: {
        language: '...',  // array[string]
    library: '...',  // array[string]
    license: '...',  // string
    pretty_name: '...',  // string
    task: '...',  // string
    },
});
console.log(response.data);
```

---

### `postModelByIdPreVerify`

**`POST /api-key/model/{id}/pre-verify`** — Check Valid Source code To Verify Ai Model

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |

**Request Body** — `request.CheckValidToVerifyAiModelRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `commit_hash` | `string` | Yes |  |
| `platforms` | `array[string]` | Yes |  |

**Responses**

**200 OK** — `response.CheckValidToVerifyAiModelResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.CheckValidToVerifyAiModelData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.CheckValidToVerifyAiModelData`**

| Field | Type | Description |
| --- | --- | --- |
| `valid` | `boolean` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { postModelByIdPreVerify } from '@aiozai/nodejs-client';

const response = await postModelByIdPreVerify({
    body: {
        commit_hash: '...',  // string  // required
    platforms: '...',  // array[string]  // required
    },
});
console.log(response.data);
```

---

### `getModelByIdServing`

**`GET /api-key/model/{id}/serving`** — Check Model Is Serving

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |

**Responses**

**200 OK** — `response.CheckModelIsServingResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.CheckModelIsServingData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.CheckModelIsServingData`**

| Field | Type | Description |
| --- | --- | --- |
| `consumers` | `integer` |  |
| `serving` | `boolean` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getModelByIdServing } from '@aiozai/nodejs-client';

const response = await getModelByIdServing({ path: { id: '...' } });
console.log(response.data);
```

---

### `getModelByIdSetting`

**`GET /api-key/model/{id}/setting`** — Get Model Setting By Model Id

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |

**Responses**

**200 OK** — `response.ModelSettingResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.ModelSetting` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.ModelSetting`**

| Field | Type | Description |
| --- | --- | --- |
| `api_price` | `number` |  |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `input_format` | `map[string]any` |  |
| `model_id` | `string` |  |
| `output_format` | `map[string]any` |  |
| `sys_req_cpu_cores` | `integer` |  |
| `sys_req_gpu_memory` | `integer` |  |
| `sys_req_ram` | `integer` |  |
| `updated_at` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getModelByIdSetting } from '@aiozai/nodejs-client';

const response = await getModelByIdSetting({ path: { id: '...' } });
console.log(response.data);
```

---

### `putModelByIdSetting`

**`PUT /api-key/model/{id}/setting`** — Update Model Setting

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |

**Request Body** — `request.UpdateModelSettingRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `api_price` | `number` | No |  |
| `sys_req_cpu_cores` | `integer` | No |  |
| `sys_req_gpu_memory` | `integer` | No |  |
| `sys_req_ram` | `integer` | No |  |

**Responses**

**200 OK** — `response.ModelSettingResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.ModelSetting` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.ModelSetting`**

| Field | Type | Description |
| --- | --- | --- |
| `api_price` | `number` |  |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `input_format` | `map[string]any` |  |
| `model_id` | `string` |  |
| `output_format` | `map[string]any` |  |
| `sys_req_cpu_cores` | `integer` |  |
| `sys_req_gpu_memory` | `integer` |  |
| `sys_req_ram` | `integer` |  |
| `updated_at` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { putModelByIdSetting } from '@aiozai/nodejs-client';

const response = await putModelByIdSetting({
    body: {
        api_price: '...',  // number
    sys_req_cpu_cores: '...',  // integer
    sys_req_gpu_memory: '...',  // integer
    sys_req_ram: '...',  // integer
    },
});
console.log(response.data);
```

---

### `postModelByIdStatistics`

**`POST /api-key/model/{id}/statistics`** — Get Model Statistics

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |

**Request Body** — `request.GetApiKeyStatisticsByModelIdRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `from` | `string` | No | 2023-05-07 15:04:05 |
| `to` | `string` | No | 2023-05-07 15:04:05 |

**Responses**

**200 OK** — `response.GetTaskStatisticsResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.GetTaskStatisticsData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.GetTaskStatisticsData`**

| Field | Type | Description |
| --- | --- | --- |
| `total_cost` | `integer` |  |
| `total_failed` | `integer` |  |
| `total_request` | `integer` |  |
| `total_success` | `integer` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { postModelByIdStatistics } from '@aiozai/nodejs-client';

const response = await postModelByIdStatistics({
    body: {
        from: '...',  // string
    to: '...',  // string
    },
});
console.log(response.data);
```

---

### `getModelByIdTaskCost`

**`GET /api-key/model/{id}/task/cost`** — Get cost to compute task by model api key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |

**Responses**

**200 OK** — `response.EstimateCostResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.EstimateCostData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.EstimateCostData`**

| Field | Type | Description |
| --- | --- | --- |
| `cost` | `number` |  |
| `symbol` | `string` |  |
| `unit` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getModelByIdTaskCost } from '@aiozai/nodejs-client';

const response = await getModelByIdTaskCost({ path: { id: '...' } });
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
| `point` | `integer` | No |  |
| `task_id` | `string` | No |  |

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
import { postModelByIdTaskReviews } from '@aiozai/nodejs-client';

const response = await postModelByIdTaskReviews({
    body: {
        description: '...',  // string
    point: '...',  // integer
    task_id: '...',  // string
    },
});
console.log(response.data);
```

---

### `postModelByIdVerify`

**`POST /api-key/model/{id}/verify`** — Verify Ai Model

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |

**Request Body** — `request.VerifyAiModelRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `commit_hash` | `string` | No |  |
| `platforms` | `array[string]` | Yes |  |

**Responses**

**200 OK** — `response.VerifyAiModelResponse`

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
import { postModelByIdVerify } from '@aiozai/nodejs-client';

const response = await postModelByIdVerify({
    body: {
        commit_hash: '...',  // string
    platforms: '...',  // array[string]  // required
    },
});
console.log(response.data);
```

---

### `postModelByIdVerifyCost`

**`POST /api-key/model/{id}/verify/cost`** — Calculate Cost To Verify Ai Model

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |

**Request Body** — `request.CalculateCostToVerifyAiModelRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `commit_hash` | `string` | Yes |  |
| `platforms` | `array[string]` | Yes |  |

**Responses**

**200 OK** — `response.EstimateCostResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.EstimateCostData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.EstimateCostData`**

| Field | Type | Description |
| --- | --- | --- |
| `cost` | `number` |  |
| `symbol` | `string` |  |
| `unit` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { postModelByIdVerifyCost } from '@aiozai/nodejs-client';

const response = await postModelByIdVerifyCost({
    body: {
        commit_hash: '...',  // string  // required
    platforms: '...',  // array[string]  // required
    },
});
console.log(response.data);
```

---

### `getModelByIdVerifyPending`

**`GET /api-key/model/{id}/verify/pending`** — Check Model Pending State

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |

**Request Body** — `request.CheckModelPendingStateRequest`

_No fields defined._

**Responses**

**200 OK** — `response.CheckModelPendingStateResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.CheckModelPendingStateData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.CheckModelPendingStateData`**

| Field | Type | Description |
| --- | --- | --- |
| `pending_state` | `boolean` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getModelByIdVerifyPending } from '@aiozai/nodejs-client';

const response = await getModelByIdVerifyPending({
    body: {
        
    },
});
console.log(response.data);
```

---

### `getModelByIdVerifyTask`

**`GET /api-key/model/{id}/verify/task`** — Get List Verify Model Task By Commit Hash And Status

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |
| `commitHash` | query | `string` | Yes |  |
| `verifyStatus` | query | `string` | No |  |

**Responses**

**200 OK** — `response.ModelVersioningGroupLiteListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.ModelVersioningGroupLiteListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.ModelVersioningGroupLiteListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.ModelVersioningGroupLite]` |  |
| `total` | `integer` |  |

**`models.ModelVersioningGroupLite`**

| Field | Type | Description |
| --- | --- | --- |
| `commit_hash` | `string` | Dependency        map[string]interface{} `json:"dependency"` |
| `commit_message` | `string` | TestResult        map[string]interface{} `json:"test_result"`
InputFormat       map[string]interface{} `json:"input_format"`
OutputFormat      map[string]interface{} `json:"output_format"`
SysRequired       map[string]interface{} `json:"sys_require"` |
| `is_active` | `boolean` |  |
| `last_checked_at` | `string` |  |
| `model_id` | `string` |  |
| `pending_platforms` | `array[models.PlatformTask]` |  |
| `rejected_platforms` | `array[models.PlatformTask]` |  |
| `verified_platforms` | `array[models.PlatformTask]` |  |
| `verify_status` | `string` |  |

**`models.PlatformTask`**

| Field | Type | Description |
| --- | --- | --- |
| `platform` | `string` |  |
| `test_result` | `map[string]any` |  |
| `updated_at` | `string` |  |
| `verify_task_id` | `string` |  |

**`models.PlatformTask`**

| Field | Type | Description |
| --- | --- | --- |
| `platform` | `string` |  |
| `test_result` | `map[string]any` |  |
| `updated_at` | `string` |  |
| `verify_task_id` | `string` |  |

**`models.PlatformTask`**

| Field | Type | Description |
| --- | --- | --- |
| `platform` | `string` |  |
| `test_result` | `map[string]any` |  |
| `updated_at` | `string` |  |
| `verify_task_id` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getModelByIdVerifyTask } from '@aiozai/nodejs-client';

const response = await getModelByIdVerifyTask({ path: { id: '...' } });
console.log(response.data);
```

---

### `getModelByIdVersioning`

**`GET /api-key/model/{id}/versioning`** — Get Current Model Versioning By Model Id By ApiKey

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |

**Responses**

**200 OK** — `response.ModelVersioningGroupLiteResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.ModelVersioningGroupLite` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.ModelVersioningGroupLite`**

| Field | Type | Description |
| --- | --- | --- |
| `commit_hash` | `string` | Dependency        map[string]interface{} `json:"dependency"` |
| `commit_message` | `string` | TestResult        map[string]interface{} `json:"test_result"`
InputFormat       map[string]interface{} `json:"input_format"`
OutputFormat      map[string]interface{} `json:"output_format"`
SysRequired       map[string]interface{} `json:"sys_require"` |
| `is_active` | `boolean` |  |
| `last_checked_at` | `string` |  |
| `model_id` | `string` |  |
| `pending_platforms` | `array[models.PlatformTask]` |  |
| `rejected_platforms` | `array[models.PlatformTask]` |  |
| `verified_platforms` | `array[models.PlatformTask]` |  |
| `verify_status` | `string` |  |

**`models.PlatformTask`**

| Field | Type | Description |
| --- | --- | --- |
| `platform` | `string` |  |
| `test_result` | `map[string]any` |  |
| `updated_at` | `string` |  |
| `verify_task_id` | `string` |  |

**`models.PlatformTask`**

| Field | Type | Description |
| --- | --- | --- |
| `platform` | `string` |  |
| `test_result` | `map[string]any` |  |
| `updated_at` | `string` |  |
| `verify_task_id` | `string` |  |

**`models.PlatformTask`**

| Field | Type | Description |
| --- | --- | --- |
| `platform` | `string` |  |
| `test_result` | `map[string]any` |  |
| `updated_at` | `string` |  |
| `verify_task_id` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getModelByIdVersioning } from '@aiozai/nodejs-client';

const response = await getModelByIdVersioning({ path: { id: '...' } });
console.log(response.data);
```

---

### `putModelByIdVersioning`

**`PUT /api-key/model/{id}/versioning`** — Change Model Versioning By Commit Hash

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |
| `commitHash` | query | `string` | Yes |  |

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
import { putModelByIdVersioning } from '@aiozai/nodejs-client';

const response = await putModelByIdVersioning({ path: { id: '...' } });
console.log(response.data);
```

---

### `deleteModelByIdVersioning`

**`DELETE /api-key/model/{id}/versioning`** — Delete Model Versioning By Commit Hash

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |
| `commitHash` | query | `string` | Yes |  |

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
import { deleteModelByIdVersioning } from '@aiozai/nodejs-client';

const response = await deleteModelByIdVersioning({ path: { id: '...' } });
console.log(response.data);
```

---

### `getModelByIdVersioningList`

**`GET /api-key/model/{id}/versioning/list`** — Get Verified List Model Versioning

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |
| `verifyStatus` | query | `string` | No |  |

**Responses**

**200 OK** — `response.GetListModelVersioningLiteResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.GetListModelVersioningsLiteData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.GetListModelVersioningsLiteData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.ModelVersioningGroupLite]` |  |
| `total` | `integer` |  |

**`models.ModelVersioningGroupLite`**

| Field | Type | Description |
| --- | --- | --- |
| `commit_hash` | `string` | Dependency        map[string]interface{} `json:"dependency"` |
| `commit_message` | `string` | TestResult        map[string]interface{} `json:"test_result"`
InputFormat       map[string]interface{} `json:"input_format"`
OutputFormat      map[string]interface{} `json:"output_format"`
SysRequired       map[string]interface{} `json:"sys_require"` |
| `is_active` | `boolean` |  |
| `last_checked_at` | `string` |  |
| `model_id` | `string` |  |
| `pending_platforms` | `array[models.PlatformTask]` |  |
| `rejected_platforms` | `array[models.PlatformTask]` |  |
| `verified_platforms` | `array[models.PlatformTask]` |  |
| `verify_status` | `string` |  |

**`models.PlatformTask`**

| Field | Type | Description |
| --- | --- | --- |
| `platform` | `string` |  |
| `test_result` | `map[string]any` |  |
| `updated_at` | `string` |  |
| `verify_task_id` | `string` |  |

**`models.PlatformTask`**

| Field | Type | Description |
| --- | --- | --- |
| `platform` | `string` |  |
| `test_result` | `map[string]any` |  |
| `updated_at` | `string` |  |
| `verify_task_id` | `string` |  |

**`models.PlatformTask`**

| Field | Type | Description |
| --- | --- | --- |
| `platform` | `string` |  |
| `test_result` | `map[string]any` |  |
| `updated_at` | `string` |  |
| `verify_task_id` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getModelByIdVersioningList } from '@aiozai/nodejs-client';

const response = await getModelByIdVersioningList({ path: { id: '...' } });
console.log(response.data);
```

---

### `getModelByUsernameByName`

**`GET /api-key/model/{username}/{name}`** — Get Model By Name

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `username` | path | `string` | Yes | Model's username |
| `name` | path | `string` | Yes | Model's name |

**Responses**

**200 OK** — `response.ModelResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.ModelData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.ModelData`**

| Field | Type | Description |
| --- | --- | --- |
| `author` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `downloads` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `likes` | `integer` |  |
| `name` | `string` |  |
| `updated_at` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getModelByUsernameByName } from '@aiozai/nodejs-client';

const response = await getModelByUsernameByName({ path: { username: '...', name: '...' } });
console.log(response.data);
```

---

### `postPackageList`

**`POST /api-key/package/list`** — Get Api Package List

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.GetApiPackageListRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `limit` | `integer` | No |  |
| `offset` | `integer` | No |  |

**Responses**

**200 OK** — `response.ApiPackageListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.ApiPackageListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.ApiPackageListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.ApiPackage]` |  |
| `total` | `integer` |  |

**`models.ApiPackage`**

| Field | Type | Description |
| --- | --- | --- |
| `active` | `boolean` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `discount` | `number` |  |
| `id` | `string` |  |
| `name` | `string` |  |
| `quantity_uses` | `integer` |  |
| `updated_at` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { postPackageList } from '@aiozai/nodejs-client';

const response = await postPackageList({
    body: {
        limit: '...',  // integer
    offset: '...',  // integer
    },
});
console.log(response.data);
```

---

### `getUserApiKeyById`

**`GET /api-key/user/api-key/{id}`** — Get Api Key Detail By Id

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Api Key's id |

**Responses**

**200 OK** — `response.LiteApiKeyResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.LiteApiKey` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.LiteApiKey`**

| Field | Type | Description |
| --- | --- | --- |
| `active` | `boolean` |  |
| `api_key` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `id` | `string` |  |
| `model_id` | `string` |  |
| `name` | `string` |  |
| `updated_at` | `string` |  |
| `user_id` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getUserApiKeyById } from '@aiozai/nodejs-client';

const response = await getUserApiKeyById({ path: { id: '...' } });
console.log(response.data);
```

---

### `putUserApiKeyById`

**`PUT /api-key/user/api-key/{id}`** — Update Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Api Key's id |

**Request Body** — `request.UpdateApiKeyRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `active` | `boolean` | No |  |
| `description` | `string` | No |  |
| `name` | `string` | No |  |
| `org_username` | `string` | No |  |

**Responses**

**200 OK** — `response.ApiKeyResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.ApiKey` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.ApiKey`**

| Field | Type | Description |
| --- | --- | --- |
| `active` | `boolean` |  |
| `api_key` | `string` |  |
| `api_price` | `number` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `id` | `string` |  |
| `input_format` | `map[string]any` |  |
| `model_id` | `string` |  |
| `name` | `string` |  |
| `output_format` | `map[string]any` |  |
| `total_cost` | `number` |  |
| `total_failed` | `integer` |  |
| `total_request` | `integer` |  |
| `total_success` | `integer` |  |
| `updated_at` | `string` |  |
| `user` | `models.User` |  |
| `user_id` | `string` |  |

**`models.User`**

| Field | Type | Description |
| --- | --- | --- |
| `allow_request_to_join` | `boolean` |  |
| `avatar_url` | `string` |  |
| `bio` | `string` |  |
| `blocked` | `boolean` |  |
| `blocked_at` | `string` |  |
| `email` | `string` |  |
| `followers` | `array[models.Follow]` |  |
| `followers_count` | `integer` |  |
| `followings` | `array[models.Follow]` |  |
| `followings_count` | `integer` |  |
| `github_link` | `string` |  |
| `github_name` | `string` |  |
| `home_page_name` | `string` |  |
| `id` | `string` |  |
| `interests` | `string` |  |
| `invite_offers` | `array[models.Offer]` |  |
| `invite_offers_count` | `integer` |  |
| `is_following` | `boolean` |  |
| `join_id` | `string` |  |
| `join_offers` | `array[models.Offer]` |  |
| `join_offers_count` | `integer` |  |
| `members` | `array[models.Member]` |  |
| `members_count` | `integer` |  |
| `name` | `string` |  |
| `role` | `string` |  |
| `token` | `string` |  |
| `twitter_link` | `string` |  |
| `twitter_name` | `string` |  |
| `type` | `string` |  |
| `username` | `string` |  |
| `verified` | `boolean` |  |
| `visibility` | `string` |  |
| `wallet` | `models.Wallet` |  |
| `wallet_address` | `string` |  |
| `wallet_connection` | `string` |  |

**`models.Follow`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `name` | `string` |  |
| `username` | `string` |  |

**`models.Follow`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `name` | `string` |  |
| `username` | `string` |  |

**`models.Offer`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `integer` |  |
| `created_by` | `string` |  |
| `exp_at` | `integer` |  |
| `id` | `string` |  |
| `org_username` | `string` |  |
| `role` | `string` |  |
| `type` | `string` |  |
| `username` | `string` |  |

**`models.Offer`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `integer` |  |
| `created_by` | `string` |  |
| `exp_at` | `integer` |  |
| `id` | `string` |  |
| `org_username` | `string` |  |
| `role` | `string` |  |
| `type` | `string` |  |
| `username` | `string` |  |

**`models.Member`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar_url` | `string` |  |
| `full_name` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

**`models.Wallet`**

| Field | Type | Description |
| --- | --- | --- |
| `balance` | `string` |  |
| `debt` | `string` |  |
| `earnings` | `string` |  |
| `free_balance` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { putUserApiKeyById } from '@aiozai/nodejs-client';

const response = await putUserApiKeyById({
    body: {
        active: '...',  // boolean
    description: '...',  // string
    name: '...',  // string
    org_username: '...',  // string
    },
});
console.log(response.data);
```

---

### `postUserApiKeyByIdStatistics`

**`POST /api-key/user/api-key/{id}/statistics`** — Get Api Key By Id

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Api Key's id |

**Request Body** — `request.GetApiKeyByIdRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `from` | `string` | No | 2023-05-07 15:04:05 |
| `org_username` | `string` | No |  |
| `to` | `string` | No | 2023-05-07 15:04:05 |

**Responses**

**200 OK** — `response.ApiKeyResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.ApiKey` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.ApiKey`**

| Field | Type | Description |
| --- | --- | --- |
| `active` | `boolean` |  |
| `api_key` | `string` |  |
| `api_price` | `number` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `id` | `string` |  |
| `input_format` | `map[string]any` |  |
| `model_id` | `string` |  |
| `name` | `string` |  |
| `output_format` | `map[string]any` |  |
| `total_cost` | `number` |  |
| `total_failed` | `integer` |  |
| `total_request` | `integer` |  |
| `total_success` | `integer` |  |
| `updated_at` | `string` |  |
| `user` | `models.User` |  |
| `user_id` | `string` |  |

**`models.User`**

| Field | Type | Description |
| --- | --- | --- |
| `allow_request_to_join` | `boolean` |  |
| `avatar_url` | `string` |  |
| `bio` | `string` |  |
| `blocked` | `boolean` |  |
| `blocked_at` | `string` |  |
| `email` | `string` |  |
| `followers` | `array[models.Follow]` |  |
| `followers_count` | `integer` |  |
| `followings` | `array[models.Follow]` |  |
| `followings_count` | `integer` |  |
| `github_link` | `string` |  |
| `github_name` | `string` |  |
| `home_page_name` | `string` |  |
| `id` | `string` |  |
| `interests` | `string` |  |
| `invite_offers` | `array[models.Offer]` |  |
| `invite_offers_count` | `integer` |  |
| `is_following` | `boolean` |  |
| `join_id` | `string` |  |
| `join_offers` | `array[models.Offer]` |  |
| `join_offers_count` | `integer` |  |
| `members` | `array[models.Member]` |  |
| `members_count` | `integer` |  |
| `name` | `string` |  |
| `role` | `string` |  |
| `token` | `string` |  |
| `twitter_link` | `string` |  |
| `twitter_name` | `string` |  |
| `type` | `string` |  |
| `username` | `string` |  |
| `verified` | `boolean` |  |
| `visibility` | `string` |  |
| `wallet` | `models.Wallet` |  |
| `wallet_address` | `string` |  |
| `wallet_connection` | `string` |  |

**`models.Follow`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `name` | `string` |  |
| `username` | `string` |  |

**`models.Follow`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `name` | `string` |  |
| `username` | `string` |  |

**`models.Offer`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `integer` |  |
| `created_by` | `string` |  |
| `exp_at` | `integer` |  |
| `id` | `string` |  |
| `org_username` | `string` |  |
| `role` | `string` |  |
| `type` | `string` |  |
| `username` | `string` |  |

**`models.Offer`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `integer` |  |
| `created_by` | `string` |  |
| `exp_at` | `integer` |  |
| `id` | `string` |  |
| `org_username` | `string` |  |
| `role` | `string` |  |
| `type` | `string` |  |
| `username` | `string` |  |

**`models.Member`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar_url` | `string` |  |
| `full_name` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

**`models.Wallet`**

| Field | Type | Description |
| --- | --- | --- |
| `balance` | `string` |  |
| `debt` | `string` |  |
| `earnings` | `string` |  |
| `free_balance` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { postUserApiKeyByIdStatistics } from '@aiozai/nodejs-client';

const response = await postUserApiKeyByIdStatistics({
    body: {
        from: '...',  // string
    org_username: '...',  // string
    to: '...',  // string
    },
});
console.log(response.data);
```

---

### `getUserPlaygroundRemaining`

**`GET /api-key/user/playground/remaining`** — Get Playground Uses Remaining By User

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Responses**

**200 OK** — `response.PlaygroundPackageListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.PlaygroundPackageListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.PlaygroundPackageListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.PlaygroundPackage]` |  |
| `total` | `integer` |  |

**`models.PlaygroundPackage`**

| Field | Type | Description |
| --- | --- | --- |
| `model_id` | `string` |  |
| `uses_remaining` | `integer` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getUserPlaygroundRemaining } from '@aiozai/nodejs-client';

const response = await getUserPlaygroundRemaining();
console.log(response.data);
```

---

### `postPublicModelList`

**`POST /public/model/list`** — Get Public Model List

**Request Body** — `request.GetModelListRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `filter_by` | `string` | No | One of: `public`, `community`, `author`, `official`, `permission`, `playground` |
| `language` | `array[string]` | No |  |
| `library` | `array[string]` | No |  |
| `license` | `string` | No |  |
| `limit` | `integer` | No |  |
| `offset` | `integer` | No |  |
| `order` | `string` | No | One of: `asc`, `desc` |
| `search` | `string` | No |  |
| `sort` | `string` | No | One of: `trending`, `likes`, `downloads`, `created`, `created_oldest`, `modified`, `name`, `size` |
| `tag_type` | `string` | No |  |
| `task` | `string` | No |  |

**Responses**

**200 OK** — `response.ModelListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.ModelListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.ModelListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Model]` |  |
| `total` | `integer` |  |

**`models.Model`**

| Field | Type | Description |
| --- | --- | --- |
| `author_avatar` | `string` |  |
| `author_id` | `string` |  |
| `commit_hash` | `string` |  |
| `cover` | `string` |  |
| `create_by` | `string` |  |
| `created_at` | `string` |  |
| `dependency_id` | `string` |  |
| `description` | `string` |  |
| `discussions_count` | `integer` |  |
| `downloads_count` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `is_official` | `boolean` |  |
| `is_released` | `boolean` |  |
| `is_verified` | `boolean` |  |
| `likes_count` | `integer` |  |
| `model_metadata` | `models.ModelMetadata` |  |
| `name` | `string` |  |
| `playground_count` | `integer` |  |
| `price` | `number` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `task_reviews_count` | `integer` |  |
| `task_reviews_point` | `number` |  |
| `thumbnail` | `string` |  |
| `updated_at` | `string` |  |
| `username` | `string` |  |
| `visibility` | `string` |  |

**`models.ModelMetadata`**

| Field | Type | Description |
| --- | --- | --- |
| `id` | `string` |  |
| `license` | `string` |  |
| `model_id` | `string` |  |
| `pretty_name` | `string` |  |
| `task` | `string` |  |

**`models.Reaction`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `string` |  |
| `name` | `string` |  |
| `owner` | `models.Owner` |  |
| `updated_at` | `string` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

**`models.ReactionStats`**

| Field | Type | Description |
| --- | --- | --- |
| `count` | `integer` |  |
| `name` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { postPublicModelList } from '@aiozai/nodejs-client';

const response = await postPublicModelList({
    body: {
        filter_by: '...',  // string
    language: '...',  // array[string]
    library: '...',  // array[string]
    license: '...',  // string
    limit: '...',  // integer
    },
});
console.log(response.data);
```

---

### `postPublicModelListByAuthorByUsername`

**`POST /public/model/list-by-author/{username}`** — Get Public Model List By User

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `username` | path | `string` | Yes | Username |

**Request Body** — `request.GetModelListByAuthorRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `language` | `array[string]` | No |  |
| `library` | `array[string]` | No |  |
| `license` | `string` | No |  |
| `limit` | `integer` | No |  |
| `offset` | `integer` | No |  |
| `order` | `string` | No | One of: `asc`, `desc` |
| `search` | `string` | No |  |
| `sort` | `string` | No | One of: `trending`, `likes`, `downloads`, `created`, `created_oldest`, `modified`, `name`, `size` |
| `tag_type` | `string` | No |  |
| `task` | `string` | No |  |

**Responses**

**200 OK** — `response.ModelListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.ModelListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.ModelListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Model]` |  |
| `total` | `integer` |  |

**`models.Model`**

| Field | Type | Description |
| --- | --- | --- |
| `author_avatar` | `string` |  |
| `author_id` | `string` |  |
| `commit_hash` | `string` |  |
| `cover` | `string` |  |
| `create_by` | `string` |  |
| `created_at` | `string` |  |
| `dependency_id` | `string` |  |
| `description` | `string` |  |
| `discussions_count` | `integer` |  |
| `downloads_count` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `is_official` | `boolean` |  |
| `is_released` | `boolean` |  |
| `is_verified` | `boolean` |  |
| `likes_count` | `integer` |  |
| `model_metadata` | `models.ModelMetadata` |  |
| `name` | `string` |  |
| `playground_count` | `integer` |  |
| `price` | `number` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `task_reviews_count` | `integer` |  |
| `task_reviews_point` | `number` |  |
| `thumbnail` | `string` |  |
| `updated_at` | `string` |  |
| `username` | `string` |  |
| `visibility` | `string` |  |

**`models.ModelMetadata`**

| Field | Type | Description |
| --- | --- | --- |
| `id` | `string` |  |
| `license` | `string` |  |
| `model_id` | `string` |  |
| `pretty_name` | `string` |  |
| `task` | `string` |  |

**`models.Reaction`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `string` |  |
| `name` | `string` |  |
| `owner` | `models.Owner` |  |
| `updated_at` | `string` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

**`models.ReactionStats`**

| Field | Type | Description |
| --- | --- | --- |
| `count` | `integer` |  |
| `name` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { postPublicModelListByAuthorByUsername } from '@aiozai/nodejs-client';

const response = await postPublicModelListByAuthorByUsername({
    body: {
        language: '...',  // array[string]
    library: '...',  // array[string]
    license: '...',  // string
    limit: '...',  // integer
    offset: '...',  // integer
    },
});
console.log(response.data);
```

---

### `postPublicModelMatchingTags`

**`POST /public/model/matching-tags`** — Matching Public Models Tags

**Request Body** — `request.MatchingModelsTagsRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `language` | `array[string]` | No |  |
| `library` | `array[string]` | No |  |
| `license` | `string` | No |  |
| `tag_type` | `string` | No |  |
| `task` | `string` | No |  |

**Responses**

**200 OK** — `response.ListDataResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `array[string]` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { postPublicModelMatchingTags } from '@aiozai/nodejs-client';

const response = await postPublicModelMatchingTags({
    body: {
        language: '...',  // array[string]
    library: '...',  // array[string]
    license: '...',  // string
    tag_type: '...',  // string
    task: '...',  // string
    },
});
console.log(response.data);
```

---

### `getPublicModelMetadata`

**`GET /public/model/metadata`** — Get Model Metadata

**Responses**

**200 OK** — `response.MetadataListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.MetadataListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.MetadataListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Metadata]` |  |

**`models.Metadata`**

| Field | Type | Description |
| --- | --- | --- |
| `category` | `string` |  |
| `id` | `string` |  |
| `label` | `string` |  |
| `type` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getPublicModelMetadata } from '@aiozai/nodejs-client';

const response = await getPublicModelMetadata();
console.log(response.data);
```

---

### `getPublicModelOrganizationByOrg`

**`GET /public/model/organization/{org}`** — Get List Model By Org Username

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `org` | path | `string` | Yes | Org's username |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |
| `sort` | query | `string` | No |  |

**Responses**

**200 OK** — `response.ModelListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.ModelListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.ModelListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Model]` |  |
| `total` | `integer` |  |

**`models.Model`**

| Field | Type | Description |
| --- | --- | --- |
| `author_avatar` | `string` |  |
| `author_id` | `string` |  |
| `commit_hash` | `string` |  |
| `cover` | `string` |  |
| `create_by` | `string` |  |
| `created_at` | `string` |  |
| `dependency_id` | `string` |  |
| `description` | `string` |  |
| `discussions_count` | `integer` |  |
| `downloads_count` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `is_official` | `boolean` |  |
| `is_released` | `boolean` |  |
| `is_verified` | `boolean` |  |
| `likes_count` | `integer` |  |
| `model_metadata` | `models.ModelMetadata` |  |
| `name` | `string` |  |
| `playground_count` | `integer` |  |
| `price` | `number` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `task_reviews_count` | `integer` |  |
| `task_reviews_point` | `number` |  |
| `thumbnail` | `string` |  |
| `updated_at` | `string` |  |
| `username` | `string` |  |
| `visibility` | `string` |  |

**`models.ModelMetadata`**

| Field | Type | Description |
| --- | --- | --- |
| `id` | `string` |  |
| `license` | `string` |  |
| `model_id` | `string` |  |
| `pretty_name` | `string` |  |
| `task` | `string` |  |

**`models.Reaction`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `string` |  |
| `name` | `string` |  |
| `owner` | `models.Owner` |  |
| `updated_at` | `string` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

**`models.ReactionStats`**

| Field | Type | Description |
| --- | --- | --- |
| `count` | `integer` |  |
| `name` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getPublicModelOrganizationByOrg } from '@aiozai/nodejs-client';

const response = await getPublicModelOrganizationByOrg({ path: { org: '...' } });
console.log(response.data);
```

---

### `getPublicModelTrending`

**`GET /public/model/trending`** — Get List Models Trending

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |

**Responses**

**200 OK** — `response.ModelListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.ModelListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.ModelListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Model]` |  |
| `total` | `integer` |  |

**`models.Model`**

| Field | Type | Description |
| --- | --- | --- |
| `author_avatar` | `string` |  |
| `author_id` | `string` |  |
| `commit_hash` | `string` |  |
| `cover` | `string` |  |
| `create_by` | `string` |  |
| `created_at` | `string` |  |
| `dependency_id` | `string` |  |
| `description` | `string` |  |
| `discussions_count` | `integer` |  |
| `downloads_count` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `is_official` | `boolean` |  |
| `is_released` | `boolean` |  |
| `is_verified` | `boolean` |  |
| `likes_count` | `integer` |  |
| `model_metadata` | `models.ModelMetadata` |  |
| `name` | `string` |  |
| `playground_count` | `integer` |  |
| `price` | `number` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `task_reviews_count` | `integer` |  |
| `task_reviews_point` | `number` |  |
| `thumbnail` | `string` |  |
| `updated_at` | `string` |  |
| `username` | `string` |  |
| `visibility` | `string` |  |

**`models.ModelMetadata`**

| Field | Type | Description |
| --- | --- | --- |
| `id` | `string` |  |
| `license` | `string` |  |
| `model_id` | `string` |  |
| `pretty_name` | `string` |  |
| `task` | `string` |  |

**`models.Reaction`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `string` |  |
| `name` | `string` |  |
| `owner` | `models.Owner` |  |
| `updated_at` | `string` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

**`models.ReactionStats`**

| Field | Type | Description |
| --- | --- | --- |
| `count` | `integer` |  |
| `name` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getPublicModelTrending } from '@aiozai/nodejs-client';

const response = await getPublicModelTrending();
console.log(response.data);
```

---

### `getPublicModelById`

**`GET /public/model/{id}`** — Get public model by id

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |

**Responses**

**200 OK** — `response.ModelResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.ModelData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.ModelData`**

| Field | Type | Description |
| --- | --- | --- |
| `author` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `downloads` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `likes` | `integer` |  |
| `name` | `string` |  |
| `updated_at` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getPublicModelById } from '@aiozai/nodejs-client';

const response = await getPublicModelById({ path: { id: '...' } });
console.log(response.data);
```

---

### `getPublicModelByIdVersioning`

**`GET /public/model/{id}/versioning`** — Get Current Model Versioning By Model Id

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |

**Responses**

**200 OK** — `response.ModelVersioningGroupLiteResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.ModelVersioningGroupLite` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.ModelVersioningGroupLite`**

| Field | Type | Description |
| --- | --- | --- |
| `commit_hash` | `string` | Dependency        map[string]interface{} `json:"dependency"` |
| `commit_message` | `string` | TestResult        map[string]interface{} `json:"test_result"`
InputFormat       map[string]interface{} `json:"input_format"`
OutputFormat      map[string]interface{} `json:"output_format"`
SysRequired       map[string]interface{} `json:"sys_require"` |
| `is_active` | `boolean` |  |
| `last_checked_at` | `string` |  |
| `model_id` | `string` |  |
| `pending_platforms` | `array[models.PlatformTask]` |  |
| `rejected_platforms` | `array[models.PlatformTask]` |  |
| `verified_platforms` | `array[models.PlatformTask]` |  |
| `verify_status` | `string` |  |

**`models.PlatformTask`**

| Field | Type | Description |
| --- | --- | --- |
| `platform` | `string` |  |
| `test_result` | `map[string]any` |  |
| `updated_at` | `string` |  |
| `verify_task_id` | `string` |  |

**`models.PlatformTask`**

| Field | Type | Description |
| --- | --- | --- |
| `platform` | `string` |  |
| `test_result` | `map[string]any` |  |
| `updated_at` | `string` |  |
| `verify_task_id` | `string` |  |

**`models.PlatformTask`**

| Field | Type | Description |
| --- | --- | --- |
| `platform` | `string` |  |
| `test_result` | `map[string]any` |  |
| `updated_at` | `string` |  |
| `verify_task_id` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getPublicModelByIdVersioning } from '@aiozai/nodejs-client';

const response = await getPublicModelByIdVersioning({ path: { id: '...' } });
console.log(response.data);
```

---

### `getPublicModelByUsernameByName`

**`GET /public/model/{username}/{name}`** — Get Public Model By Name

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `username` | path | `string` | Yes | Username |
| `name` | path | `string` | Yes | Model's name |

**Responses**

**200 OK** — `response.ModelResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.ModelData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.ModelData`**

| Field | Type | Description |
| --- | --- | --- |
| `author` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `downloads` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `likes` | `integer` |  |
| `name` | `string` |  |
| `updated_at` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getPublicModelByUsernameByName } from '@aiozai/nodejs-client';

const response = await getPublicModelByUsernameByName({ path: { username: '...', name: '...' } });
console.log(response.data);
```

---
