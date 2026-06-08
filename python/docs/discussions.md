# Discussions — Python SDK

> Discussion forums — create and manage discussions. Requires: `x-api-key` header.

Reference: [SDK Usage Guide](../README.md#sdk-usage-guide) | [Package README](../README.md)

---

### `post_collection_by_id_report`

**`POST /api-key/collection/{id}/report`** — Report Collection

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Collection's id |

**Request Body** — `request.ReportCollectionRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `reason` | `string` | Yes |  |
| `url` | `string` | Yes |  |

**Responses**

**200 OK** — `response.DiscussionResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.LiteDiscussion` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.LiteDiscussion`**

| Field | Type | Description |
| --- | --- | --- |
| `comments_count` | `integer` |  |
| `content` | `string` |  |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `is_closed` | `boolean` |  |
| `owner` | `models.Owner` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `reacts_count` | `integer` |  |
| `title` | `string` |  |
| `updated_at` | `string` |  |
| `violated` | `boolean` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

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

```python
from aiozai_sdk.generated.models import ReportCollectionRequest

request = ReportCollectionRequest(
    reason="...",  # string  # required
    url="...",  # string  # required
)
resp = client.discussions.discussion.post_collection_by_id_report(input=request)
print(resp)
```

---

### `post_comments_by_id_report`

**`POST /api-key/comments/{id}/report`** — Report Comment

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Comment's id |

**Request Body** — `request.ReportCommentRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `reason` | `string` | Yes |  |
| `url` | `string` | Yes |  |

**Responses**

**200 OK** — `response.DiscussionResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.LiteDiscussion` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.LiteDiscussion`**

| Field | Type | Description |
| --- | --- | --- |
| `comments_count` | `integer` |  |
| `content` | `string` |  |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `is_closed` | `boolean` |  |
| `owner` | `models.Owner` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `reacts_count` | `integer` |  |
| `title` | `string` |  |
| `updated_at` | `string` |  |
| `violated` | `boolean` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

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

```python
from aiozai_sdk.generated.models import ReportCommentRequest

request = ReportCommentRequest(
    reason="...",  # string  # required
    url="...",  # string  # required
)
resp = client.discussions.discussion.post_comments_by_id_report(input=request)
print(resp)
```

---

### `get_discussion_competition_by_id`

**`GET /api-key/discussion/competition/{id}`** — Get competition discussion list

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Competition's id |
| `filter` | query | `string` | No |  |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |
| `search` | query | `string` | No |  |
| `sort` | query | `string` | No |  |

**Responses**

**200 OK** — `response.DiscussionListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.DiscussionListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.DiscussionListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.LiteDiscussion]` |  |
| `total` | `integer` |  |

**`models.LiteDiscussion`**

| Field | Type | Description |
| --- | --- | --- |
| `comments_count` | `integer` |  |
| `content` | `string` |  |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `is_closed` | `boolean` |  |
| `owner` | `models.Owner` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `reacts_count` | `integer` |  |
| `title` | `string` |  |
| `updated_at` | `string` |  |
| `violated` | `boolean` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

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

```python
resp = client.discussions.discussion.get_discussion_competition_by_id(id="<id>")
print(resp)
```

---

### `post_discussion_competition_by_id`

**`POST /api-key/discussion/competition/{id}`** — Create competition discussion

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Competition's id |

**Request Body** — `request.CreateCompetitionDiscussionRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `content` | `string` | Yes |  |
| `title` | `string` | Yes |  |

**Responses**

**200 OK** — `response.DiscussionResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.LiteDiscussion` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.LiteDiscussion`**

| Field | Type | Description |
| --- | --- | --- |
| `comments_count` | `integer` |  |
| `content` | `string` |  |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `is_closed` | `boolean` |  |
| `owner` | `models.Owner` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `reacts_count` | `integer` |  |
| `title` | `string` |  |
| `updated_at` | `string` |  |
| `violated` | `boolean` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

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

```python
from aiozai_sdk.generated.models import CreateCompetitionDiscussionRequest

request = CreateCompetitionDiscussionRequest(
    content="...",  # string  # required
    title="...",  # string  # required
)
resp = client.discussions.discussion.post_discussion_competition_by_id(input=request)
print(resp)
```

---

### `get_discussion_dataset_by_id`

**`GET /api-key/discussion/dataset/{id}`** — Get dataset discussion list

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Dataset's id |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |
| `sort` | query | `string` | No |  |

**Responses**

**200 OK** — `response.DiscussionListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.DiscussionListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.DiscussionListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.LiteDiscussion]` |  |
| `total` | `integer` |  |

**`models.LiteDiscussion`**

| Field | Type | Description |
| --- | --- | --- |
| `comments_count` | `integer` |  |
| `content` | `string` |  |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `is_closed` | `boolean` |  |
| `owner` | `models.Owner` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `reacts_count` | `integer` |  |
| `title` | `string` |  |
| `updated_at` | `string` |  |
| `violated` | `boolean` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

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

```python
resp = client.discussions.discussion.get_discussion_dataset_by_id(id="<id>")
print(resp)
```

---

### `post_discussion_dataset_by_id`

**`POST /api-key/discussion/dataset/{id}`** — Create dataset discussion

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Dataset's id |

**Request Body** — `request.CreateDatasetDiscussionRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `content` | `string` | Yes |  |
| `title` | `string` | Yes |  |

**Responses**

**200 OK** — `response.DiscussionResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.LiteDiscussion` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.LiteDiscussion`**

| Field | Type | Description |
| --- | --- | --- |
| `comments_count` | `integer` |  |
| `content` | `string` |  |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `is_closed` | `boolean` |  |
| `owner` | `models.Owner` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `reacts_count` | `integer` |  |
| `title` | `string` |  |
| `updated_at` | `string` |  |
| `violated` | `boolean` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

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

```python
from aiozai_sdk.generated.models import CreateDatasetDiscussionRequest

request = CreateDatasetDiscussionRequest(
    content="...",  # string  # required
    title="...",  # string  # required
)
resp = client.discussions.discussion.post_discussion_dataset_by_id(input=request)
print(resp)
```

---

### `get_discussion_model_by_id`

**`GET /api-key/discussion/model/{id}`** — Get model discussion list

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
| `sort` | query | `string` | No |  |

**Responses**

**200 OK** — `response.DiscussionListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.DiscussionListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.DiscussionListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.LiteDiscussion]` |  |
| `total` | `integer` |  |

**`models.LiteDiscussion`**

| Field | Type | Description |
| --- | --- | --- |
| `comments_count` | `integer` |  |
| `content` | `string` |  |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `is_closed` | `boolean` |  |
| `owner` | `models.Owner` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `reacts_count` | `integer` |  |
| `title` | `string` |  |
| `updated_at` | `string` |  |
| `violated` | `boolean` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

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

```python
resp = client.discussions.discussion.get_discussion_model_by_id(id="<id>")
print(resp)
```

---

### `post_discussion_model_by_id`

**`POST /api-key/discussion/model/{id}`** — Create model discussion

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |

**Request Body** — `request.CreateModelDiscussionRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `content` | `string` | Yes |  |
| `title` | `string` | Yes |  |

**Responses**

**200 OK** — `response.DiscussionResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.LiteDiscussion` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.LiteDiscussion`**

| Field | Type | Description |
| --- | --- | --- |
| `comments_count` | `integer` |  |
| `content` | `string` |  |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `is_closed` | `boolean` |  |
| `owner` | `models.Owner` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `reacts_count` | `integer` |  |
| `title` | `string` |  |
| `updated_at` | `string` |  |
| `violated` | `boolean` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

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

```python
from aiozai_sdk.generated.models import CreateModelDiscussionRequest

request = CreateModelDiscussionRequest(
    content="...",  # string  # required
    title="...",  # string  # required
)
resp = client.discussions.discussion.post_discussion_model_by_id(input=request)
print(resp)
```

---

### `put_discussion_by_id`

**`PUT /api-key/discussion/{id}`** — Update discussion

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Discussion's id |

**Request Body** — `request.UpdateDiscussionRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `content` | `string` | No |  |
| `is_closed` | `boolean` | No |  |
| `title` | `string` | No |  |

**Responses**

**200 OK** — `response.DiscussionResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.LiteDiscussion` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.LiteDiscussion`**

| Field | Type | Description |
| --- | --- | --- |
| `comments_count` | `integer` |  |
| `content` | `string` |  |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `is_closed` | `boolean` |  |
| `owner` | `models.Owner` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `reacts_count` | `integer` |  |
| `title` | `string` |  |
| `updated_at` | `string` |  |
| `violated` | `boolean` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

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

```python
from aiozai_sdk.generated.models import UpdateDiscussionRequest

request = UpdateDiscussionRequest(
    content="...",  # string
    is_closed="...",  # boolean
    title="...",  # string
)
resp = client.discussions.discussion.put_discussion_by_id(input=request)
print(resp)
```

---

### `delete_discussion_by_id`

**`DELETE /api-key/discussion/{id}`** — Delete discussion

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Discussion's id |

**Responses**

**200 OK** — `response.DiscussionResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.LiteDiscussion` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.LiteDiscussion`**

| Field | Type | Description |
| --- | --- | --- |
| `comments_count` | `integer` |  |
| `content` | `string` |  |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `is_closed` | `boolean` |  |
| `owner` | `models.Owner` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `reacts_count` | `integer` |  |
| `title` | `string` |  |
| `updated_at` | `string` |  |
| `violated` | `boolean` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

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

```python
resp = client.discussions.discussion.delete_discussion_by_id(id="<id>")
print(resp)
```

---

### `post_discussion_by_id_report`

**`POST /api-key/discussion/{id}/report`** — Report Discussion

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Discussion's id |

**Request Body** — `request.ReportDiscussionRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `reason` | `string` | Yes |  |
| `url` | `string` | Yes |  |

**Responses**

**200 OK** — `response.DiscussionResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.LiteDiscussion` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.LiteDiscussion`**

| Field | Type | Description |
| --- | --- | --- |
| `comments_count` | `integer` |  |
| `content` | `string` |  |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `is_closed` | `boolean` |  |
| `owner` | `models.Owner` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `reacts_count` | `integer` |  |
| `title` | `string` |  |
| `updated_at` | `string` |  |
| `violated` | `boolean` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

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

```python
from aiozai_sdk.generated.models import ReportDiscussionRequest

request = ReportDiscussionRequest(
    reason="...",  # string  # required
    url="...",  # string  # required
)
resp = client.discussions.discussion.post_discussion_by_id_report(input=request)
print(resp)
```

---

### `get_public_discussion_competition_by_id`

**`GET /public/discussion/competition/{id}`** — Get public competition discussion list

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Competition's id |
| `filter` | query | `string` | No |  |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |
| `search` | query | `string` | No |  |
| `sort` | query | `string` | No |  |

**Responses**

**200 OK** — `response.DiscussionListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.DiscussionListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.DiscussionListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.LiteDiscussion]` |  |
| `total` | `integer` |  |

**`models.LiteDiscussion`**

| Field | Type | Description |
| --- | --- | --- |
| `comments_count` | `integer` |  |
| `content` | `string` |  |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `is_closed` | `boolean` |  |
| `owner` | `models.Owner` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `reacts_count` | `integer` |  |
| `title` | `string` |  |
| `updated_at` | `string` |  |
| `violated` | `boolean` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

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

```python
resp = client.discussions.discussion.get_public_discussion_competition_by_id(id="<id>")
print(resp)
```

---

### `get_public_discussion_dataset_by_id`

**`GET /public/discussion/dataset/{id}`** — Get dataset discussion list

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Dataset's id |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |
| `sort` | query | `string` | No |  |

**Responses**

**200 OK** — `response.DiscussionListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.DiscussionListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.DiscussionListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.LiteDiscussion]` |  |
| `total` | `integer` |  |

**`models.LiteDiscussion`**

| Field | Type | Description |
| --- | --- | --- |
| `comments_count` | `integer` |  |
| `content` | `string` |  |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `is_closed` | `boolean` |  |
| `owner` | `models.Owner` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `reacts_count` | `integer` |  |
| `title` | `string` |  |
| `updated_at` | `string` |  |
| `violated` | `boolean` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

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

```python
resp = client.discussions.discussion.get_public_discussion_dataset_by_id(id="<id>")
print(resp)
```

---

### `get_public_discussion_model_by_id`

**`GET /public/discussion/model/{id}`** — Get model discussion list

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |
| `sort` | query | `string` | No |  |

**Responses**

**200 OK** — `response.DiscussionListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.DiscussionListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.DiscussionListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.LiteDiscussion]` |  |
| `total` | `integer` |  |

**`models.LiteDiscussion`**

| Field | Type | Description |
| --- | --- | --- |
| `comments_count` | `integer` |  |
| `content` | `string` |  |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `is_closed` | `boolean` |  |
| `owner` | `models.Owner` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `reacts_count` | `integer` |  |
| `title` | `string` |  |
| `updated_at` | `string` |  |
| `violated` | `boolean` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

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

```python
resp = client.discussions.discussion.get_public_discussion_model_by_id(id="<id>")
print(resp)
```

---

### `get_public_discussion_by_id`

**`GET /public/discussion/{id}`** — Get discussion detail

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Discussion's id |

**Responses**

**200 OK** — `response.DiscussionResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.LiteDiscussion` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.LiteDiscussion`**

| Field | Type | Description |
| --- | --- | --- |
| `comments_count` | `integer` |  |
| `content` | `string` |  |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `is_closed` | `boolean` |  |
| `owner` | `models.Owner` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `reacts_count` | `integer` |  |
| `title` | `string` |  |
| `updated_at` | `string` |  |
| `violated` | `boolean` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

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

```python
resp = client.discussions.discussion.get_public_discussion_by_id(id="<id>")
print(resp)
```

---

### `get_public_discussion_by_id_comments`

**`GET /public/discussion/{id}/comments`** — Get a list of comments

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Discussion's id |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |
| `sort` | query | `string` | No |  |

**Responses**

**200 OK** — `response.CommentListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.CommentListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.CommentListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Comment]` |  |
| `total` | `integer` |  |

**`models.Comment`**

| Field | Type | Description |
| --- | --- | --- |
| `content` | `string` |  |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `owner` | `models.Owner` |  |
| `reacted` | `models.Reaction` |  |
| `reactions` | `array[models.Reaction]` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `reacts_count` | `integer` |  |
| `tag_usernames` | `array[string]` |  |
| `updated_at` | `string` |  |
| `violated` | `boolean` |  |

**`models.Owner`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

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

```python
resp = client.discussions.discussion.get_public_discussion_by_id_comments(id="<id>")
print(resp)
```

---
