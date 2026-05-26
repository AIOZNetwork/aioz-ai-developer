# Competitions — TypeScript SDK

> Competition management — create, join, and manage AI competitions. Requires: `x-api-key` header.

Reference: [SDK Usage Guide](../README.md#sdk-usage-guide) | [Package README](../README.md)

---

### `postApiKeyCompetition`

**`POST /api-key/competition`** — Create a new competition By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.CreateCompetitionRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `author_id` | `string` | No |  |
| `category` | `string` | No | featured,research,getting-started,playground,community,analytics,simulations |
| `code` | `string` | No |  |
| `cover` | `string` | No |  |
| `data` | `string` | No |  |
| `description` | `string` | No |  |
| `end_date` | `string` | No | 2025-01-01 12:00:00 |
| `final_result_mode` | `string` | No | auto,manual |
| `max_daily_private_submissions` | `integer` | No |  |
| `overview` | `string` | No |  |
| `private_leaderboard_release_date` | `string` | No | 2025-01-01 12:00:00 |
| `prize_distribution_method` | `string` | No | manual,smart_contract. One of: `manual`, `smart_contract` |
| `registration_deadline` | `string` | No | 2025-01-01 12:00:00 |
| `reward_type` | `string` | No | monetary,knowledge,swag,kudos |
| `rules` | `string` | No |  |
| `start_date` | `string` | No | 2025-01-01 12:00:00 |
| `submission_deadline` | `string` | No | 2025-01-01 12:00:00 |
| `tags` | `array[string]` | No |  |
| `thumbnail` | `string` | No |  |
| `time_zone_config` | `map[string]any` | No |  |
| `title` | `string` | Yes |  |
| `total_prize_pool` | `number` | No |  |
| `visibility` | `string` | No |  |

**Responses**

**200 OK** — `response.CompetitionResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.Competition` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.Competition`**

| Field | Type | Description |
| --- | --- | --- |
| `author_id` | `string` |  |
| `category` | `string` |  |
| `code` | `string` |  |
| `cover` | `string` |  |
| `created_at` | `string` |  |
| `data` | `string` |  |
| `description` | `string` |  |
| `end_date` | `string` |  |
| `final_result_mode` | `string` |  |
| `id` | `string` |  |
| `joined` | `boolean` |  |
| `launched` | `boolean` |  |
| `max_daily_private_submissions` | `integer` |  |
| `overview` | `string` |  |
| `owner` | `models.Owner` |  |
| `participants` | `integer` |  |
| `path` | `string` |  |
| `permission` | `map[string]any` |  |
| `private_leaderboard_release_date` | `string` |  |
| `private_submissions_remaining` | `integer` |  |
| `prize_distribution_method` | `string` |  |
| `registration_deadline` | `string` |  |
| `reward_type` | `string` |  |
| `rules` | `string` |  |
| `start_date` | `string` |  |
| `submission_deadline` | `string` |  |
| `submissions` | `integer` |  |
| `tags` | `array[string]` |  |
| `thumbnail` | `string` |  |
| `time_zone_config` | `map[string]any` |  |
| `title` | `string` |  |
| `total_prize_pool` | `number` |  |
| `updated_at` | `string` |  |
| `user_id` | `string` |  |
| `visibility` | `string` |  |

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
import { postApiKeyCompetition } from '@aiozai/nodejs-client';

const response = await postApiKeyCompetition({
    body: {
        author_id: '...',  // string
    category: '...',  // string
    code: '...',  // string
    cover: '...',  // string
    data: '...',  // string
    },
});
console.log(response.data);
```

---

### `postApiKeyCompetitionList`

**`POST /api-key/competition/list`** — List competitions By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.GetCompetitionListRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `category` | `string` | No | featured,research,getting-started,playground,community,analytics,simulations |
| `following` | `boolean` | No |  |
| `limit` | `integer` | No |  |
| `offset` | `integer` | No |  |
| `reward_type` | `string` | No | monetary,knowledge,swag,kudos |
| `role` | `string` | No | host,participant |
| `search` | `string` | No |  |
| `sort_by` | `string` | No | reward,created_at,created_oldest,hotness,total_team,closing_soon,recently_completed. One of: `reward`, `created_at`, `created_oldest`, `hotness`, `total_team`, `closing_soon`, `recently_completed` |
| `status` | `string` | No | active,completed,entered,spotlight |
| `tags` | `array[string]` | No |  |

**Responses**

**200 OK** — `response.CompetitionListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.CompetitionListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.CompetitionListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Competition]` |  |
| `total` | `integer` |  |

**`models.Competition`**

| Field | Type | Description |
| --- | --- | --- |
| `author_id` | `string` |  |
| `category` | `string` |  |
| `code` | `string` |  |
| `cover` | `string` |  |
| `created_at` | `string` |  |
| `data` | `string` |  |
| `description` | `string` |  |
| `end_date` | `string` |  |
| `final_result_mode` | `string` |  |
| `id` | `string` |  |
| `joined` | `boolean` |  |
| `launched` | `boolean` |  |
| `max_daily_private_submissions` | `integer` |  |
| `overview` | `string` |  |
| `owner` | `models.Owner` |  |
| `participants` | `integer` |  |
| `path` | `string` |  |
| `permission` | `map[string]any` |  |
| `private_leaderboard_release_date` | `string` |  |
| `private_submissions_remaining` | `integer` |  |
| `prize_distribution_method` | `string` |  |
| `registration_deadline` | `string` |  |
| `reward_type` | `string` |  |
| `rules` | `string` |  |
| `start_date` | `string` |  |
| `submission_deadline` | `string` |  |
| `submissions` | `integer` |  |
| `tags` | `array[string]` |  |
| `thumbnail` | `string` |  |
| `time_zone_config` | `map[string]any` |  |
| `title` | `string` |  |
| `total_prize_pool` | `number` |  |
| `updated_at` | `string` |  |
| `user_id` | `string` |  |
| `visibility` | `string` |  |

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
import { postApiKeyCompetitionList } from '@aiozai/nodejs-client';

const response = await postApiKeyCompetitionList({
    body: {
        category: '...',  // string
    following: '...',  // boolean
    limit: '...',  // integer
    offset: '...',  // integer
    reward_type: '...',  // string
    },
});
console.log(response.data);
```

---

### `getApiKeyCompetitionPathByPath`

**`GET /api-key/competition/path/{path}`** — Get competition details by path By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `path` | path | `string` | Yes | Competition Path |

**Responses**

**200 OK** — `response.CompetitionResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.Competition` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.Competition`**

| Field | Type | Description |
| --- | --- | --- |
| `author_id` | `string` |  |
| `category` | `string` |  |
| `code` | `string` |  |
| `cover` | `string` |  |
| `created_at` | `string` |  |
| `data` | `string` |  |
| `description` | `string` |  |
| `end_date` | `string` |  |
| `final_result_mode` | `string` |  |
| `id` | `string` |  |
| `joined` | `boolean` |  |
| `launched` | `boolean` |  |
| `max_daily_private_submissions` | `integer` |  |
| `overview` | `string` |  |
| `owner` | `models.Owner` |  |
| `participants` | `integer` |  |
| `path` | `string` |  |
| `permission` | `map[string]any` |  |
| `private_leaderboard_release_date` | `string` |  |
| `private_submissions_remaining` | `integer` |  |
| `prize_distribution_method` | `string` |  |
| `registration_deadline` | `string` |  |
| `reward_type` | `string` |  |
| `rules` | `string` |  |
| `start_date` | `string` |  |
| `submission_deadline` | `string` |  |
| `submissions` | `integer` |  |
| `tags` | `array[string]` |  |
| `thumbnail` | `string` |  |
| `time_zone_config` | `map[string]any` |  |
| `title` | `string` |  |
| `total_prize_pool` | `number` |  |
| `updated_at` | `string` |  |
| `user_id` | `string` |  |
| `visibility` | `string` |  |

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
import { getApiKeyCompetitionPathByPath } from '@aiozai/nodejs-client';

const response = await getApiKeyCompetitionPathByPath({ path: { path: '...' } });
console.log(response.data);
```

---

### `postApiKeyCompetitionPreSubmit`

**`POST /api-key/competition/pre-submit`** — Check valid repo to submit data By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.CheckValidRepoToEvaluateModelRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `commit_hash` | `string` | No |  |
| `model_id` | `string` | Yes |  |

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
import { postApiKeyCompetitionPreSubmit } from '@aiozai/nodejs-client';

const response = await postApiKeyCompetitionPreSubmit({
    body: {
        commit_hash: '...',  // string
    model_id: '...',  // string  // required
    },
});
console.log(response.data);
```

---

### `postApiKeyCompetitionSubmit`

**`POST /api-key/competition/submit`** — Submit competition data By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `competition_id` | formData | `string` | Yes | Competition ID |
| `model_id` | formData | `string` | No | Model ID |
| `submission_type` | formData | `string` | Yes | Submission Type (public/private) |
| `description` | formData | `string` | No | Description |
| `commit_hash` | formData | `string` | No | Commit Hash |
| `file` | formData | `file` | No | CSV File |

**Responses**

**200 OK** — `response.SubmitHistoryResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.SubmitHistory` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.SubmitHistory`**

| Field | Type | Description |
| --- | --- | --- |
| `code_size` | `number` |  |
| `commit_hash` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` | CompetitionId uuid.UUID `json:"competition_id"`
UserId      uuid.UUID `json:"user_id"` |
| `file_name` | `string` |  |
| `file_size` | `number` |  |
| `id` | `string` |  |
| `logs` | `map[string]any` |  |
| `model_id` | `string` | FileUrl        string    `json:"file_url"`
ModelWeightUrl string    `json:"model_weight_url"`
SourceCodeUrl  string    `json:"source_code_url"` |
| `model_size` | `number` |  |
| `score` | `number` |  |
| `status` | `string` |  |
| `submission_type` | `string` |  |
| `time` | `number` |  |
| `updated_at` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { postApiKeyCompetitionSubmit } from '@aiozai/nodejs-client';

const response = await postApiKeyCompetitionSubmit();
console.log(response.data);
```

---

### `postApiKeyCompetitionSubmitCost`

**`POST /api-key/competition/submit/cost`** — Estimate cost to submit data By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.EstimateCostToEvaluateModelRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `commit_hash` | `string` | No |  |
| `competition_id` | `string` | Yes |  |
| `model_id` | `string` | Yes |  |

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
import { postApiKeyCompetitionSubmitCost } from '@aiozai/nodejs-client';

const response = await postApiKeyCompetitionSubmitCost({
    body: {
        commit_hash: '...',  // string
    competition_id: '...',  // string  // required
    model_id: '...',  // string  // required
    },
});
console.log(response.data);
```

---

### `getApiKeyCompetitionSubmitHistoryById`

**`GET /api-key/competition/submit/history/{id}`** — Get submission history By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Competition Id |

**Responses**

**200 OK** — `response.SubmitHistoryListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.SubmitHistoryListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.SubmitHistoryListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.SubmitHistory]` |  |
| `total` | `integer` |  |

**`models.SubmitHistory`**

| Field | Type | Description |
| --- | --- | --- |
| `code_size` | `number` |  |
| `commit_hash` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` | CompetitionId uuid.UUID `json:"competition_id"`
UserId      uuid.UUID `json:"user_id"` |
| `file_name` | `string` |  |
| `file_size` | `number` |  |
| `id` | `string` |  |
| `logs` | `map[string]any` |  |
| `model_id` | `string` | FileUrl        string    `json:"file_url"`
ModelWeightUrl string    `json:"model_weight_url"`
SourceCodeUrl  string    `json:"source_code_url"` |
| `model_size` | `number` |  |
| `score` | `number` |  |
| `status` | `string` |  |
| `submission_type` | `string` |  |
| `time` | `number` |  |
| `updated_at` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getApiKeyCompetitionSubmitHistoryById } from '@aiozai/nodejs-client';

const response = await getApiKeyCompetitionSubmitHistoryById({ path: { id: '...' } });
console.log(response.data);
```

---

### `getApiKeyCompetitionById`

**`GET /api-key/competition/{id}`** — Get competition details By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Competition Id |

**Responses**

**200 OK** — `response.CompetitionResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.Competition` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.Competition`**

| Field | Type | Description |
| --- | --- | --- |
| `author_id` | `string` |  |
| `category` | `string` |  |
| `code` | `string` |  |
| `cover` | `string` |  |
| `created_at` | `string` |  |
| `data` | `string` |  |
| `description` | `string` |  |
| `end_date` | `string` |  |
| `final_result_mode` | `string` |  |
| `id` | `string` |  |
| `joined` | `boolean` |  |
| `launched` | `boolean` |  |
| `max_daily_private_submissions` | `integer` |  |
| `overview` | `string` |  |
| `owner` | `models.Owner` |  |
| `participants` | `integer` |  |
| `path` | `string` |  |
| `permission` | `map[string]any` |  |
| `private_leaderboard_release_date` | `string` |  |
| `private_submissions_remaining` | `integer` |  |
| `prize_distribution_method` | `string` |  |
| `registration_deadline` | `string` |  |
| `reward_type` | `string` |  |
| `rules` | `string` |  |
| `start_date` | `string` |  |
| `submission_deadline` | `string` |  |
| `submissions` | `integer` |  |
| `tags` | `array[string]` |  |
| `thumbnail` | `string` |  |
| `time_zone_config` | `map[string]any` |  |
| `title` | `string` |  |
| `total_prize_pool` | `number` |  |
| `updated_at` | `string` |  |
| `user_id` | `string` |  |
| `visibility` | `string` |  |

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
import { getApiKeyCompetitionById } from '@aiozai/nodejs-client';

const response = await getApiKeyCompetitionById({ path: { id: '...' } });
console.log(response.data);
```

---

### `putApiKeyCompetitionById`

**`PUT /api-key/competition/{id}`** — Update a competition By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Competition Id |

**Request Body** — `request.UpdateCompetitionRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `category` | `string` | No | featured,research,getting-started,playground,community,analytics,simulations |
| `code` | `string` | No |  |
| `cover` | `string` | No |  |
| `data` | `string` | No |  |
| `description` | `string` | No |  |
| `end_date` | `string` | No | 2025-01-01 12:00:00 |
| `final_result_mode` | `string` | No | auto,manual |
| `max_daily_private_submissions` | `integer` | No |  |
| `overview` | `string` | No |  |
| `private_leaderboard_release_date` | `string` | No | 2025-01-01 12:00:00 |
| `prize_distribution_method` | `string` | No | manual,smart_contract. One of: `manual`, `smart_contract` |
| `registration_deadline` | `string` | No | 2025-01-01 12:00:00 |
| `reward_type` | `string` | No | monetary,knowledge,swag,kudos |
| `rules` | `string` | No |  |
| `start_date` | `string` | No | 2025-01-01 12:00:00 |
| `submission_deadline` | `string` | No | 2025-01-01 12:00:00 |
| `tags` | `array[string]` | No |  |
| `thumbnail` | `string` | No |  |
| `time_zone_config` | `map[string]any` | No |  |
| `title` | `string` | No |  |
| `total_prize_pool` | `number` | No |  |
| `visibility` | `string` | No |  |

**Responses**

**200 OK** — `response.CompetitionResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.Competition` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.Competition`**

| Field | Type | Description |
| --- | --- | --- |
| `author_id` | `string` |  |
| `category` | `string` |  |
| `code` | `string` |  |
| `cover` | `string` |  |
| `created_at` | `string` |  |
| `data` | `string` |  |
| `description` | `string` |  |
| `end_date` | `string` |  |
| `final_result_mode` | `string` |  |
| `id` | `string` |  |
| `joined` | `boolean` |  |
| `launched` | `boolean` |  |
| `max_daily_private_submissions` | `integer` |  |
| `overview` | `string` |  |
| `owner` | `models.Owner` |  |
| `participants` | `integer` |  |
| `path` | `string` |  |
| `permission` | `map[string]any` |  |
| `private_leaderboard_release_date` | `string` |  |
| `private_submissions_remaining` | `integer` |  |
| `prize_distribution_method` | `string` |  |
| `registration_deadline` | `string` |  |
| `reward_type` | `string` |  |
| `rules` | `string` |  |
| `start_date` | `string` |  |
| `submission_deadline` | `string` |  |
| `submissions` | `integer` |  |
| `tags` | `array[string]` |  |
| `thumbnail` | `string` |  |
| `time_zone_config` | `map[string]any` |  |
| `title` | `string` |  |
| `total_prize_pool` | `number` |  |
| `updated_at` | `string` |  |
| `user_id` | `string` |  |
| `visibility` | `string` |  |

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
import { putApiKeyCompetitionById } from '@aiozai/nodejs-client';

const response = await putApiKeyCompetitionById({
    body: {
        category: '...',  // string
    code: '...',  // string
    cover: '...',  // string
    data: '...',  // string
    description: '...',  // string
    },
});
console.log(response.data);
```

---

### `deleteApiKeyCompetitionById`

**`DELETE /api-key/competition/{id}`** — Delete a competition By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Competition Id |

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
import { deleteApiKeyCompetitionById } from '@aiozai/nodejs-client';

const response = await deleteApiKeyCompetitionById({ path: { id: '...' } });
console.log(response.data);
```

---

### `postApiKeyCompetitionByIdJoin`

**`POST /api-key/competition/{id}/join`** — Join a competition By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Competition Id |

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
import { postApiKeyCompetitionByIdJoin } from '@aiozai/nodejs-client';

const response = await postApiKeyCompetitionByIdJoin({ path: { id: '...' } });
console.log(response.data);
```

---

### `postApiKeyCompetitionByIdLaunch`

**`POST /api-key/competition/{id}/launch`** — Launch a competition By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Competition Id |

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
import { postApiKeyCompetitionByIdLaunch } from '@aiozai/nodejs-client';

const response = await postApiKeyCompetitionByIdLaunch({ path: { id: '...' } });
console.log(response.data);
```

---

### `getApiKeyCompetitionByIdLeaderboard`

**`GET /api-key/competition/{id}/leaderboard`** — Get competition leaderboard By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Competition Id |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |
| `search` | query | `string` | No |  |
| `sort` | query | `string` | No |  |
| `type` | query | `string` | No |  |

**Responses**

**200 OK** — `response.LeaderboardListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.LeaderboardListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.LeaderboardListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Leaderboard]` |  |
| `total` | `integer` |  |

**`models.Leaderboard`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `string` |  |
| `current_rank` | `integer` |  |
| `entries` | `integer` |  |
| `id` | `string` |  |
| `is_violated` | `boolean` |  |
| `medal_name` | `string` |  |
| `owner` | `object` | CompetitionId uuid.UUID `json:"competition_id"` |
| `prize_amount` | `number` |  |
| `rank_change` | `integer` |  |
| `score` | `number` |  |
| `updated_at` | `string` |  |
| `user_info` | `models.UserInfoData` |  |

**`models.UserInfoData`**

| Field | Type | Description |
| --- | --- | --- |
| `email` | `string` |  |
| `username` | `string` |  |
| `wallet_address` | `string` |  |
| `wallet_connection` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getApiKeyCompetitionByIdLeaderboard } from '@aiozai/nodejs-client';

const response = await getApiKeyCompetitionByIdLeaderboard({ path: { id: '...' } });
console.log(response.data);
```

---

### `postApiKeyCompetitionByIdLeave`

**`POST /api-key/competition/{id}/leave`** — Leave competition By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Competition Id |

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
import { postApiKeyCompetitionByIdLeave } from '@aiozai/nodejs-client';

const response = await postApiKeyCompetitionByIdLeave({ path: { id: '...' } });
console.log(response.data);
```

---

### `getApiKeyCompetitionByIdPublicLeaderboard`

**`GET /api-key/competition/{id}/public/leaderboard`** — GetLeaderboardByCompetitionIdAndPhase By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Competition Id |
| `phase` | path | `string` | Yes | Competition Phase |

**Responses**

**200 OK** — `response.LeaderboardListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.LeaderboardListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.LeaderboardListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Leaderboard]` |  |
| `total` | `integer` |  |

**`models.Leaderboard`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `string` |  |
| `current_rank` | `integer` |  |
| `entries` | `integer` |  |
| `id` | `string` |  |
| `is_violated` | `boolean` |  |
| `medal_name` | `string` |  |
| `owner` | `object` | CompetitionId uuid.UUID `json:"competition_id"` |
| `prize_amount` | `number` |  |
| `rank_change` | `integer` |  |
| `score` | `number` |  |
| `updated_at` | `string` |  |
| `user_info` | `models.UserInfoData` |  |

**`models.UserInfoData`**

| Field | Type | Description |
| --- | --- | --- |
| `email` | `string` |  |
| `username` | `string` |  |
| `wallet_address` | `string` |  |
| `wallet_connection` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getApiKeyCompetitionByIdPublicLeaderboard } from '@aiozai/nodejs-client';

const response = await getApiKeyCompetitionByIdPublicLeaderboard({ path: { id: '...', phase: '...' } });
console.log(response.data);
```

---

### `postPublicCompetitionList`

**`POST /public/competition/list`** — List competitions

**Request Body** — `request.GetCompetitionListRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `category` | `string` | No | featured,research,getting-started,playground,community,analytics,simulations |
| `following` | `boolean` | No |  |
| `limit` | `integer` | No |  |
| `offset` | `integer` | No |  |
| `reward_type` | `string` | No | monetary,knowledge,swag,kudos |
| `role` | `string` | No | host,participant |
| `search` | `string` | No |  |
| `sort_by` | `string` | No | reward,created_at,created_oldest,hotness,total_team,closing_soon,recently_completed. One of: `reward`, `created_at`, `created_oldest`, `hotness`, `total_team`, `closing_soon`, `recently_completed` |
| `status` | `string` | No | active,completed,entered,spotlight |
| `tags` | `array[string]` | No |  |

**Responses**

**200 OK** — `response.CompetitionListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.CompetitionListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.CompetitionListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Competition]` |  |
| `total` | `integer` |  |

**`models.Competition`**

| Field | Type | Description |
| --- | --- | --- |
| `author_id` | `string` |  |
| `category` | `string` |  |
| `code` | `string` |  |
| `cover` | `string` |  |
| `created_at` | `string` |  |
| `data` | `string` |  |
| `description` | `string` |  |
| `end_date` | `string` |  |
| `final_result_mode` | `string` |  |
| `id` | `string` |  |
| `joined` | `boolean` |  |
| `launched` | `boolean` |  |
| `max_daily_private_submissions` | `integer` |  |
| `overview` | `string` |  |
| `owner` | `models.Owner` |  |
| `participants` | `integer` |  |
| `path` | `string` |  |
| `permission` | `map[string]any` |  |
| `private_leaderboard_release_date` | `string` |  |
| `private_submissions_remaining` | `integer` |  |
| `prize_distribution_method` | `string` |  |
| `registration_deadline` | `string` |  |
| `reward_type` | `string` |  |
| `rules` | `string` |  |
| `start_date` | `string` |  |
| `submission_deadline` | `string` |  |
| `submissions` | `integer` |  |
| `tags` | `array[string]` |  |
| `thumbnail` | `string` |  |
| `time_zone_config` | `map[string]any` |  |
| `title` | `string` |  |
| `total_prize_pool` | `number` |  |
| `updated_at` | `string` |  |
| `user_id` | `string` |  |
| `visibility` | `string` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { postPublicCompetitionList } from '@aiozai/nodejs-client';

const response = await postPublicCompetitionList({
    body: {
        category: '...',  // string
    following: '...',  // boolean
    limit: '...',  // integer
    offset: '...',  // integer
    reward_type: '...',  // string
    },
});
console.log(response.data);
```

---

### `getPublicCompetitionMetadata`

**`GET /public/competition/metadata`** — Get Competition Metadata

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
import { getPublicCompetitionMetadata } from '@aiozai/nodejs-client';

const response = await getPublicCompetitionMetadata();
console.log(response.data);
```

---

### `getPublicCompetitionPathByPath`

**`GET /public/competition/path/{path}`** — Get competition details by path

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `path` | path | `string` | Yes | Competition Path |

**Responses**

**200 OK** — `response.CompetitionResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.Competition` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.Competition`**

| Field | Type | Description |
| --- | --- | --- |
| `author_id` | `string` |  |
| `category` | `string` |  |
| `code` | `string` |  |
| `cover` | `string` |  |
| `created_at` | `string` |  |
| `data` | `string` |  |
| `description` | `string` |  |
| `end_date` | `string` |  |
| `final_result_mode` | `string` |  |
| `id` | `string` |  |
| `joined` | `boolean` |  |
| `launched` | `boolean` |  |
| `max_daily_private_submissions` | `integer` |  |
| `overview` | `string` |  |
| `owner` | `models.Owner` |  |
| `participants` | `integer` |  |
| `path` | `string` |  |
| `permission` | `map[string]any` |  |
| `private_leaderboard_release_date` | `string` |  |
| `private_submissions_remaining` | `integer` |  |
| `prize_distribution_method` | `string` |  |
| `registration_deadline` | `string` |  |
| `reward_type` | `string` |  |
| `rules` | `string` |  |
| `start_date` | `string` |  |
| `submission_deadline` | `string` |  |
| `submissions` | `integer` |  |
| `tags` | `array[string]` |  |
| `thumbnail` | `string` |  |
| `time_zone_config` | `map[string]any` |  |
| `title` | `string` |  |
| `total_prize_pool` | `number` |  |
| `updated_at` | `string` |  |
| `user_id` | `string` |  |
| `visibility` | `string` |  |

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
import { getPublicCompetitionPathByPath } from '@aiozai/nodejs-client';

const response = await getPublicCompetitionPathByPath({ path: { path: '...' } });
console.log(response.data);
```

---

### `getPublicCompetitionTimelineById`

**`GET /public/competition/timeline/{id}`** — Get timeline by ID

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Timeline ID |

**Responses**

**200 OK** — `response.TimelineResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.Timeline` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.Timeline`**

| Field | Type | Description |
| --- | --- | --- |
| `competition_id` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `end_date` | `string` |  |
| `id` | `string` |  |
| `name` | `string` |  |
| `start_date` | `string` |  |
| `updated_at` | `string` |  |
| `weight` | `number` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getPublicCompetitionTimelineById } from '@aiozai/nodejs-client';

const response = await getPublicCompetitionTimelineById({ path: { id: '...' } });
console.log(response.data);
```

---

### `getPublicCompetitionById`

**`GET /public/competition/{id}`** — Get competition details

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Competition Id |

**Responses**

**200 OK** — `response.CompetitionResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.Competition` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.Competition`**

| Field | Type | Description |
| --- | --- | --- |
| `author_id` | `string` |  |
| `category` | `string` |  |
| `code` | `string` |  |
| `cover` | `string` |  |
| `created_at` | `string` |  |
| `data` | `string` |  |
| `description` | `string` |  |
| `end_date` | `string` |  |
| `final_result_mode` | `string` |  |
| `id` | `string` |  |
| `joined` | `boolean` |  |
| `launched` | `boolean` |  |
| `max_daily_private_submissions` | `integer` |  |
| `overview` | `string` |  |
| `owner` | `models.Owner` |  |
| `participants` | `integer` |  |
| `path` | `string` |  |
| `permission` | `map[string]any` |  |
| `private_leaderboard_release_date` | `string` |  |
| `private_submissions_remaining` | `integer` |  |
| `prize_distribution_method` | `string` |  |
| `registration_deadline` | `string` |  |
| `reward_type` | `string` |  |
| `rules` | `string` |  |
| `start_date` | `string` |  |
| `submission_deadline` | `string` |  |
| `submissions` | `integer` |  |
| `tags` | `array[string]` |  |
| `thumbnail` | `string` |  |
| `time_zone_config` | `map[string]any` |  |
| `title` | `string` |  |
| `total_prize_pool` | `number` |  |
| `updated_at` | `string` |  |
| `user_id` | `string` |  |
| `visibility` | `string` |  |

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
import { getPublicCompetitionById } from '@aiozai/nodejs-client';

const response = await getPublicCompetitionById({ path: { id: '...' } });
console.log(response.data);
```

---

### `getPublicCompetitionByIdLeaderboard`

**`GET /public/competition/{id}/leaderboard`** — Get competition leaderboard

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Competition Id |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |
| `search` | query | `string` | No |  |
| `sort` | query | `string` | No |  |
| `type` | query | `string` | No |  |

**Responses**

**200 OK** — `response.LeaderboardListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.LeaderboardListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.LeaderboardListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Leaderboard]` |  |
| `total` | `integer` |  |

**`models.Leaderboard`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `string` |  |
| `current_rank` | `integer` |  |
| `entries` | `integer` |  |
| `id` | `string` |  |
| `is_violated` | `boolean` |  |
| `medal_name` | `string` |  |
| `owner` | `object` | CompetitionId uuid.UUID `json:"competition_id"` |
| `prize_amount` | `number` |  |
| `rank_change` | `integer` |  |
| `score` | `number` |  |
| `updated_at` | `string` |  |
| `user_info` | `models.UserInfoData` |  |

**`models.UserInfoData`**

| Field | Type | Description |
| --- | --- | --- |
| `email` | `string` |  |
| `username` | `string` |  |
| `wallet_address` | `string` |  |
| `wallet_connection` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getPublicCompetitionByIdLeaderboard } from '@aiozai/nodejs-client';

const response = await getPublicCompetitionByIdLeaderboard({ path: { id: '...' } });
console.log(response.data);
```

---

### `getPublicCompetitionByIdPublicLeaderboard`

**`GET /public/competition/{id}/public/leaderboard`** — GetLeaderboardByCompetitionIdAndPhase

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Competition Id |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |
| `phaseName` | query | `string` | No |  |
| `search` | query | `string` | No |  |
| `sort` | query | `string` | No |  |

**Responses**

**200 OK** — `response.LeaderboardListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.LeaderboardListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.LeaderboardListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Leaderboard]` |  |
| `total` | `integer` |  |

**`models.Leaderboard`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `string` |  |
| `current_rank` | `integer` |  |
| `entries` | `integer` |  |
| `id` | `string` |  |
| `is_violated` | `boolean` |  |
| `medal_name` | `string` |  |
| `owner` | `object` | CompetitionId uuid.UUID `json:"competition_id"` |
| `prize_amount` | `number` |  |
| `rank_change` | `integer` |  |
| `score` | `number` |  |
| `updated_at` | `string` |  |
| `user_info` | `models.UserInfoData` |  |

**`models.UserInfoData`**

| Field | Type | Description |
| --- | --- | --- |
| `email` | `string` |  |
| `username` | `string` |  |
| `wallet_address` | `string` |  |
| `wallet_connection` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getPublicCompetitionByIdPublicLeaderboard } from '@aiozai/nodejs-client';

const response = await getPublicCompetitionByIdPublicLeaderboard({ path: { id: '...' } });
console.log(response.data);
```

---

### `getPublicCompetitionByIdTimelines`

**`GET /public/competition/{id}/timelines`** — Get public list of timelines by competition ID

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Competition ID |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |

**Responses**

**200 OK** — `response.ListTimelinesResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `array[models.Timeline]` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.Timeline`**

| Field | Type | Description |
| --- | --- | --- |
| `competition_id` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `end_date` | `string` |  |
| `id` | `string` |  |
| `name` | `string` |  |
| `start_date` | `string` |  |
| `updated_at` | `string` |  |
| `weight` | `number` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getPublicCompetitionByIdTimelines } from '@aiozai/nodejs-client';

const response = await getPublicCompetitionByIdTimelines({ path: { id: '...' } });
console.log(response.data);
```

---
