# Competitions — TypeScript SDK

> Competition management — create, join, and manage AI competitions. Requires: `x-api-key` header.

Reference: [SDK Usage Guide](../README.md#sdk-usage-guide) | [Package README](../README.md)

---

### `postCompetitionList`

**`POST /api-key/competition/list`** — List competitions

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
| `order` | `string` | No | One of: `desc`, `asc` |
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
import { createAiozAIClient, services } from '@aiozai/nodejs-client';

const { rawClient } = createAiozAIClient({ apiKey: process.env.AIOZ_AI_API_KEY });

const response = await services.competitions.postCompetitionList({
    client: rawClient,
    body: {
        category: '...',  // string
        following: '...',  // boolean
        limit: '...',  // integer
        offset: '...',  // integer
        order: '...',  // string
    },
});
console.log(response.data);
```

---

### `getCompetitionPathByPath`

**`GET /api-key/competition/path/{path}`** — Get competition details by path

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
import { createAiozAIClient, services } from '@aiozai/nodejs-client';

const { rawClient } = createAiozAIClient({ apiKey: process.env.AIOZ_AI_API_KEY });

const response = await services.competitions.getCompetitionPathByPath({
    client: rawClient,
    path: { path: '...' },
});
console.log(response.data);
```

---

### `postCompetitionPreSubmit`

**`POST /api-key/competition/pre-submit`** — Check valid repo to submit data

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
import { createAiozAIClient, services } from '@aiozai/nodejs-client';

const { rawClient } = createAiozAIClient({ apiKey: process.env.AIOZ_AI_API_KEY });

const response = await services.competitions.postCompetitionPreSubmit({
    client: rawClient,
    body: {
        commit_hash: '...',  // string
        model_id: '...',  // string  // required
    },
});
console.log(response.data);
```

---

### `postCompetitionSubmit`

**`POST /api-key/competition/submit`** — Submit competition data

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

**200 OK** — `response.EvaluateModelResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.EvaluateModelData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.EvaluateModelData`**

| Field | Type | Description |
| --- | --- | --- |
| `task_id` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { createAiozAIClient, services } from '@aiozai/nodejs-client';

const { rawClient } = createAiozAIClient({ apiKey: process.env.AIOZ_AI_API_KEY });

const response = await services.competitions.postCompetitionSubmit({ client: rawClient });
console.log(response.data);
```

---

### `postCompetitionSubmitCost`

**`POST /api-key/competition/submit/cost`** — Estimate cost to submit data

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
import { createAiozAIClient, services } from '@aiozai/nodejs-client';

const { rawClient } = createAiozAIClient({ apiKey: process.env.AIOZ_AI_API_KEY });

const response = await services.competitions.postCompetitionSubmitCost({
    client: rawClient,
    body: {
        commit_hash: '...',  // string
        competition_id: '...',  // string  // required
        model_id: '...',  // string  // required
    },
});
console.log(response.data);
```

---

### `getCompetitionSubmitHistoryById`

**`GET /api-key/competition/submit/history/{id}`** — Get submission history

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
import { createAiozAIClient, services } from '@aiozai/nodejs-client';

const { rawClient } = createAiozAIClient({ apiKey: process.env.AIOZ_AI_API_KEY });

const response = await services.competitions.getCompetitionSubmitHistoryById({
    client: rawClient,
    path: { id: '...' },
});
console.log(response.data);
```

---

### `getCompetitionById`

**`GET /api-key/competition/{id}`** — Get competition details

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
import { createAiozAIClient, services } from '@aiozai/nodejs-client';

const { rawClient } = createAiozAIClient({ apiKey: process.env.AIOZ_AI_API_KEY });

const response = await services.competitions.getCompetitionById({
    client: rawClient,
    path: { id: '...' },
});
console.log(response.data);
```

---

### `postCompetitionByIdJoin`

**`POST /api-key/competition/{id}/join`** — Join a competition

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
import { createAiozAIClient, services } from '@aiozai/nodejs-client';

const { rawClient } = createAiozAIClient({ apiKey: process.env.AIOZ_AI_API_KEY });

const response = await services.competitions.postCompetitionByIdJoin({
    client: rawClient,
    path: { id: '...' },
});
console.log(response.data);
```

---

### `getCompetitionByIdLeaderboard`

**`GET /api-key/competition/{id}/leaderboard`** — Get competition leaderboard

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
import { createAiozAIClient, services } from '@aiozai/nodejs-client';

const { rawClient } = createAiozAIClient({ apiKey: process.env.AIOZ_AI_API_KEY });

const response = await services.competitions.getCompetitionByIdLeaderboard({
    client: rawClient,
    path: { id: '...' },
});
console.log(response.data);
```

---

### `getCompetitionByIdPublicLeaderboard`

**`GET /api-key/competition/{id}/public/leaderboard`** — GetLeaderboardByCompetitionIdAndPhase

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Competition Id |
| `phaseName` | query | `string` | Yes | Competition Phase |

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
import { createAiozAIClient, services } from '@aiozai/nodejs-client';

const { rawClient } = createAiozAIClient({ apiKey: process.env.AIOZ_AI_API_KEY });

const response = await services.competitions.getCompetitionByIdPublicLeaderboard({
    client: rawClient,
    path: { id: '...' },
});
console.log(response.data);
```

---
