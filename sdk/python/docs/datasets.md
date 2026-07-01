# Datasets — Python SDK

> Dataset management — upload, process, and share datasets. Requires: `x-api-key` header.

Reference: [SDK Usage Guide](../README.md#sdk-usage-guide) | [Package README](../README.md)

---

### `post_dataset`

**`POST /api-key/dataset`** — Create dataset

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.CreateDatasetRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `author_id` | `string` | No |  |
| `cover` | `string` | Yes |  |
| `description` | `string` | Yes |  |
| `language` | `array[string]` | No | en, vi |
| `license` | `string` | Yes |  |
| `name` | `string` | Yes |  |
| `pretty_name` | `string` | No |  |
| `price` | `number` | No |  |
| `size_category` | `string` | No |  |
| `tags` | `array[string]` | No | art, medical |
| `task_categories` | `array[string]` | No | feature-extraction, text-to-video |
| `thumbnail` | `string` | Yes |  |
| `visibility` | `string` | Yes | One of: `public`, `private` |

**Responses**

**200 OK** — `response.DatasetResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.Dataset` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.Dataset`**

| Field | Type | Description |
| --- | --- | --- |
| `author_avatar` | `string` |  |
| `author_id` | `string` |  |
| `cover` | `string` |  |
| `create_by` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `discussions_count` | `integer` |  |
| `downloads_count` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `is_official` | `boolean` |  |
| `is_released` | `boolean` |  |
| `is_verified` | `boolean` |  |
| `likes_count` | `integer` |  |
| `metadata` | `models.DatasetMetadata` |  |
| `name` | `string` |  |
| `price` | `number` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `thumbnail` | `string` |  |
| `updated_at` | `string` |  |
| `username` | `string` |  |
| `visibility` | `string` |  |

**`models.DatasetMetadata`**

| Field | Type | Description |
| --- | --- | --- |
| `dataset_id` | `string` |  |
| `id` | `string` |  |
| `language` | `array[string]` | en, vi |
| `license` | `string` |  |
| `pretty_name` | `string` |  |
| `size_category` | `string` |  |
| `tags` | `array[string]` | art |
| `task_categories` | `array[string]` | text-to-image |

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
from aiozai_sdk.generated.models import CreateDatasetRequest

request = CreateDatasetRequest(
    author_id="...",  # string
    cover="...",  # string  # required
    description="...",  # string  # required
    language="...",  # array[string]
    license="...",  # string  # required
)
resp = client.datasets.dataset.post_dataset(input=request)
print(resp)
```

---

### `post_dataset_list`

**`POST /api-key/dataset/list`** — Get dataset list

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.GetDatasetListRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `filter_by` | `string` | No | One of: `public`, `community`, `author`, `official`, `permission` |
| `language` | `array[string]` | No |  |
| `license` | `string` | No |  |
| `limit` | `integer` | No |  |
| `offset` | `integer` | No |  |
| `order` | `string` | No | One of: `desc`, `asc` |
| `search` | `string` | No |  |
| `size_category` | `string` | No |  |
| `sort` | `string` | No | One of: `trending`, `likes`, `downloads`, `created`, `created_oldest`, `modified` |
| `tag_type` | `string` | No |  |
| `tags` | `array[string]` | No |  |
| `task_categories` | `array[string]` | No |  |

**Responses**

**200 OK** — `response.DatasetListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.DatasetListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.DatasetListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Dataset]` |  |
| `total` | `integer` |  |

**`models.Dataset`**

| Field | Type | Description |
| --- | --- | --- |
| `author_avatar` | `string` |  |
| `author_id` | `string` |  |
| `cover` | `string` |  |
| `create_by` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `discussions_count` | `integer` |  |
| `downloads_count` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `is_official` | `boolean` |  |
| `is_released` | `boolean` |  |
| `is_verified` | `boolean` |  |
| `likes_count` | `integer` |  |
| `metadata` | `models.DatasetMetadata` |  |
| `name` | `string` |  |
| `price` | `number` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `thumbnail` | `string` |  |
| `updated_at` | `string` |  |
| `username` | `string` |  |
| `visibility` | `string` |  |

**`models.DatasetMetadata`**

| Field | Type | Description |
| --- | --- | --- |
| `dataset_id` | `string` |  |
| `id` | `string` |  |
| `language` | `array[string]` | en, vi |
| `license` | `string` |  |
| `pretty_name` | `string` |  |
| `size_category` | `string` |  |
| `tags` | `array[string]` | art |
| `task_categories` | `array[string]` | text-to-image |

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
from aiozai_sdk.generated.models import GetDatasetListRequest

request = GetDatasetListRequest(
    filter_by="...",  # string
    language="...",  # array[string]
    license="...",  # string
    limit="...",  # integer
    offset="...",  # integer
)
resp = client.datasets.dataset.post_dataset_list(input=request)
print(resp)
```

---

### `post_dataset_list_by_author_by_username`

**`POST /api-key/dataset/list-by-author/{username}`** — Get dataset list by user

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `username` | path | `string` | Yes | Username |

**Request Body** — `request.GetDatasetListByAuthorRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `language` | `array[string]` | No |  |
| `license` | `string` | No |  |
| `limit` | `integer` | No |  |
| `offset` | `integer` | No |  |
| `order` | `string` | No | One of: `desc`, `asc` |
| `search` | `string` | No |  |
| `size_category` | `string` | No |  |
| `sort` | `string` | No | One of: `trending`, `likes`, `downloads`, `created`, `created_oldest`, `modified` |
| `tag_type` | `string` | No |  |
| `tags` | `array[string]` | No |  |
| `task_categories` | `array[string]` | No |  |

**Responses**

**200 OK** — `response.DatasetListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.DatasetListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.DatasetListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Dataset]` |  |
| `total` | `integer` |  |

**`models.Dataset`**

| Field | Type | Description |
| --- | --- | --- |
| `author_avatar` | `string` |  |
| `author_id` | `string` |  |
| `cover` | `string` |  |
| `create_by` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `discussions_count` | `integer` |  |
| `downloads_count` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `is_official` | `boolean` |  |
| `is_released` | `boolean` |  |
| `is_verified` | `boolean` |  |
| `likes_count` | `integer` |  |
| `metadata` | `models.DatasetMetadata` |  |
| `name` | `string` |  |
| `price` | `number` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `thumbnail` | `string` |  |
| `updated_at` | `string` |  |
| `username` | `string` |  |
| `visibility` | `string` |  |

**`models.DatasetMetadata`**

| Field | Type | Description |
| --- | --- | --- |
| `dataset_id` | `string` |  |
| `id` | `string` |  |
| `language` | `array[string]` | en, vi |
| `license` | `string` |  |
| `pretty_name` | `string` |  |
| `size_category` | `string` |  |
| `tags` | `array[string]` | art |
| `task_categories` | `array[string]` | text-to-image |

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
from aiozai_sdk.generated.models import GetDatasetListByAuthorRequest

request = GetDatasetListByAuthorRequest(
    language="...",  # array[string]
    license="...",  # string
    limit="...",  # integer
    offset="...",  # integer
    order="...",  # string
)
resp = client.datasets.dataset.post_dataset_list_by_author_by_username(input=request)
print(resp)
```

---

### `post_dataset_matching_tags`

**`POST /api-key/dataset/matching-tags`** — Get matching datasets tags

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.MatchingDatasetsTagsRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `language` | `array[string]` | No |  |
| `license` | `string` | No |  |
| `size_category` | `string` | No |  |
| `tag_type` | `string` | No |  |
| `tags` | `array[string]` | No |  |
| `task_categories` | `array[string]` | No |  |

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

```python
from aiozai_sdk.generated.models import MatchingDatasetsTagsRequest

request = MatchingDatasetsTagsRequest(
    language="...",  # array[string]
    license="...",  # string
    size_category="...",  # string
    tag_type="...",  # string
    tags="...",  # array[string]
)
resp = client.datasets.dataset.post_dataset_matching_tags(input=request)
print(resp)
```

---

### `get_dataset_organization_by_org`

**`GET /api-key/dataset/organization/{org}`** — Get List Dataset By Org Username

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
| `order` | query | `string` | No |  |
| `sort` | query | `string` | No |  |

**Responses**

**200 OK** — `response.DatasetListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.DatasetListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.DatasetListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Dataset]` |  |
| `total` | `integer` |  |

**`models.Dataset`**

| Field | Type | Description |
| --- | --- | --- |
| `author_avatar` | `string` |  |
| `author_id` | `string` |  |
| `cover` | `string` |  |
| `create_by` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `discussions_count` | `integer` |  |
| `downloads_count` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `is_official` | `boolean` |  |
| `is_released` | `boolean` |  |
| `is_verified` | `boolean` |  |
| `likes_count` | `integer` |  |
| `metadata` | `models.DatasetMetadata` |  |
| `name` | `string` |  |
| `price` | `number` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `thumbnail` | `string` |  |
| `updated_at` | `string` |  |
| `username` | `string` |  |
| `visibility` | `string` |  |

**`models.DatasetMetadata`**

| Field | Type | Description |
| --- | --- | --- |
| `dataset_id` | `string` |  |
| `id` | `string` |  |
| `language` | `array[string]` | en, vi |
| `license` | `string` |  |
| `pretty_name` | `string` |  |
| `size_category` | `string` |  |
| `tags` | `array[string]` | art |
| `task_categories` | `array[string]` | text-to-image |

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
resp = client.datasets.dataset.get_dataset_organization_by_org(org="<org>")
print(resp)
```

---

### `get_dataset_by_id`

**`GET /api-key/dataset/{id}`** — Get dataset by id

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Dataset's id |

**Responses**

**200 OK** — `response.DatasetResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.Dataset` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.Dataset`**

| Field | Type | Description |
| --- | --- | --- |
| `author_avatar` | `string` |  |
| `author_id` | `string` |  |
| `cover` | `string` |  |
| `create_by` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `discussions_count` | `integer` |  |
| `downloads_count` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `is_official` | `boolean` |  |
| `is_released` | `boolean` |  |
| `is_verified` | `boolean` |  |
| `likes_count` | `integer` |  |
| `metadata` | `models.DatasetMetadata` |  |
| `name` | `string` |  |
| `price` | `number` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `thumbnail` | `string` |  |
| `updated_at` | `string` |  |
| `username` | `string` |  |
| `visibility` | `string` |  |

**`models.DatasetMetadata`**

| Field | Type | Description |
| --- | --- | --- |
| `dataset_id` | `string` |  |
| `id` | `string` |  |
| `language` | `array[string]` | en, vi |
| `license` | `string` |  |
| `pretty_name` | `string` |  |
| `size_category` | `string` |  |
| `tags` | `array[string]` | art |
| `task_categories` | `array[string]` | text-to-image |

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
resp = client.datasets.dataset.get_dataset_by_id(id="<id>")
print(resp)
```

---

### `put_dataset_by_id`

**`PUT /api-key/dataset/{id}`** — Update Dataset

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Dataset's id |

**Request Body** — `request.UpdateDatasetRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `cover` | `string` | No |  |
| `description` | `string` | No |  |
| `price` | `number` | No |  |
| `thumbnail` | `string` | No |  |
| `visibility` | `string` | No | One of: `public`, `private` |

**Responses**

**200 OK** — `response.DatasetResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.Dataset` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.Dataset`**

| Field | Type | Description |
| --- | --- | --- |
| `author_avatar` | `string` |  |
| `author_id` | `string` |  |
| `cover` | `string` |  |
| `create_by` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `discussions_count` | `integer` |  |
| `downloads_count` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `is_official` | `boolean` |  |
| `is_released` | `boolean` |  |
| `is_verified` | `boolean` |  |
| `likes_count` | `integer` |  |
| `metadata` | `models.DatasetMetadata` |  |
| `name` | `string` |  |
| `price` | `number` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `thumbnail` | `string` |  |
| `updated_at` | `string` |  |
| `username` | `string` |  |
| `visibility` | `string` |  |

**`models.DatasetMetadata`**

| Field | Type | Description |
| --- | --- | --- |
| `dataset_id` | `string` |  |
| `id` | `string` |  |
| `language` | `array[string]` | en, vi |
| `license` | `string` |  |
| `pretty_name` | `string` |  |
| `size_category` | `string` |  |
| `tags` | `array[string]` | art |
| `task_categories` | `array[string]` | text-to-image |

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
from aiozai_sdk.generated.models import UpdateDatasetRequest

request = UpdateDatasetRequest(
    cover="...",  # string
    description="...",  # string
    price="...",  # number
    thumbnail="...",  # string
    visibility="...",  # string
)
resp = client.datasets.dataset.put_dataset_by_id(input=request)
print(resp)
```

---

### `delete_dataset_by_id`

**`DELETE /api-key/dataset/{id}`** — Delete dataset

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Dataset's id |

**Request Body** — `request.DeleteDatasetRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `repository_name` | `string` | No |  |

**Responses**

**200 OK** — `response.DatasetResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.Dataset` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.Dataset`**

| Field | Type | Description |
| --- | --- | --- |
| `author_avatar` | `string` |  |
| `author_id` | `string` |  |
| `cover` | `string` |  |
| `create_by` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `discussions_count` | `integer` |  |
| `downloads_count` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `is_official` | `boolean` |  |
| `is_released` | `boolean` |  |
| `is_verified` | `boolean` |  |
| `likes_count` | `integer` |  |
| `metadata` | `models.DatasetMetadata` |  |
| `name` | `string` |  |
| `price` | `number` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `thumbnail` | `string` |  |
| `updated_at` | `string` |  |
| `username` | `string` |  |
| `visibility` | `string` |  |

**`models.DatasetMetadata`**

| Field | Type | Description |
| --- | --- | --- |
| `dataset_id` | `string` |  |
| `id` | `string` |  |
| `language` | `array[string]` | en, vi |
| `license` | `string` |  |
| `pretty_name` | `string` |  |
| `size_category` | `string` |  |
| `tags` | `array[string]` | art |
| `task_categories` | `array[string]` | text-to-image |

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
from aiozai_sdk.generated.models import DeleteDatasetRequest

request = DeleteDatasetRequest(
    repository_name="...",  # string
)
resp = client.datasets.dataset.delete_dataset_by_id(input=request)
print(resp)
```

---

### `get_dataset_by_id_download`

**`GET /api-key/dataset/{id}/download`** — Get List Dataset Download

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

**Responses**

**200 OK** — `response.DownloadDatasetListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.DownloadDatasetListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.DownloadDatasetListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.LiteDownloadDataset]` |  |
| `total` | `integer` |  |

**`models.LiteDownloadDataset`**

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

```python
resp = client.datasets.dataset.get_dataset_by_id_download(id="<id>")
print(resp)
```

---

### `get_dataset_by_id_like`

**`GET /api-key/dataset/{id}/like`** — Get List Dataset Like

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

**Responses**

**200 OK** — `response.LikeDatasetListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.LikeDatasetListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.LikeDatasetListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.LiteLikeDataset]` |  |
| `total` | `integer` |  |

**`models.LiteLikeDataset`**

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

```python
resp = client.datasets.dataset.get_dataset_by_id_like(id="<id>")
print(resp)
```

---

### `put_dataset_by_id_metadata`

**`PUT /api-key/dataset/{id}/metadata`** — Update dataset's metadata

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Dataset's id |

**Request Body** — `request.UpdateDatasetMetadataRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `language` | `array[string]` | No | en, vi |
| `license` | `string` | No | mit |
| `pretty_name` | `string` | No | default pretty name |
| `size_category` | `string` | No | n<1k |
| `tags` | `array[string]` | No | art |
| `task_categories` | `array[string]` | No | text-to-image |

**Responses**

**200 OK** — `response.DatasetMetadataResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.DatasetMetadata` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.DatasetMetadata`**

| Field | Type | Description |
| --- | --- | --- |
| `dataset_id` | `string` |  |
| `id` | `string` |  |
| `language` | `array[string]` | en, vi |
| `license` | `string` |  |
| `pretty_name` | `string` |  |
| `size_category` | `string` |  |
| `tags` | `array[string]` | art |
| `task_categories` | `array[string]` | text-to-image |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```python
from aiozai_sdk.generated.models import UpdateDatasetMetadataRequest

request = UpdateDatasetMetadataRequest(
    language="...",  # array[string]
    license="...",  # string
    pretty_name="...",  # string
    size_category="...",  # string
    tags="...",  # array[string]
)
resp = client.datasets.dataset.put_dataset_by_id_metadata(input=request)
print(resp)
```

---

### `get_dataset_by_username_by_name`

**`GET /api-key/dataset/{username}/{name}`** — Get dataset by name

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `username` | path | `string` | Yes | Dataset's username |
| `name` | path | `string` | Yes | Dataset's name |

**Responses**

**200 OK** — `response.DatasetResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.Dataset` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.Dataset`**

| Field | Type | Description |
| --- | --- | --- |
| `author_avatar` | `string` |  |
| `author_id` | `string` |  |
| `cover` | `string` |  |
| `create_by` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `discussions_count` | `integer` |  |
| `downloads_count` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `is_official` | `boolean` |  |
| `is_released` | `boolean` |  |
| `is_verified` | `boolean` |  |
| `likes_count` | `integer` |  |
| `metadata` | `models.DatasetMetadata` |  |
| `name` | `string` |  |
| `price` | `number` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `thumbnail` | `string` |  |
| `updated_at` | `string` |  |
| `username` | `string` |  |
| `visibility` | `string` |  |

**`models.DatasetMetadata`**

| Field | Type | Description |
| --- | --- | --- |
| `dataset_id` | `string` |  |
| `id` | `string` |  |
| `language` | `array[string]` | en, vi |
| `license` | `string` |  |
| `pretty_name` | `string` |  |
| `size_category` | `string` |  |
| `tags` | `array[string]` | art |
| `task_categories` | `array[string]` | text-to-image |

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
resp = client.datasets.dataset.get_dataset_by_username_by_name(username="<username>", name="<name>")
print(resp)
```

---

### `post_public_dataset_list`

**`POST /public/dataset/list`** — GetPublicDatasetList

**Request Body** — `request.GetDatasetListRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `filter_by` | `string` | No | One of: `public`, `community`, `author`, `official`, `permission` |
| `language` | `array[string]` | No |  |
| `license` | `string` | No |  |
| `limit` | `integer` | No |  |
| `offset` | `integer` | No |  |
| `order` | `string` | No | One of: `desc`, `asc` |
| `search` | `string` | No |  |
| `size_category` | `string` | No |  |
| `sort` | `string` | No | One of: `trending`, `likes`, `downloads`, `created`, `created_oldest`, `modified` |
| `tag_type` | `string` | No |  |
| `tags` | `array[string]` | No |  |
| `task_categories` | `array[string]` | No |  |

**Responses**

**200 OK** — `response.DatasetListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.DatasetListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.DatasetListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Dataset]` |  |
| `total` | `integer` |  |

**`models.Dataset`**

| Field | Type | Description |
| --- | --- | --- |
| `author_avatar` | `string` |  |
| `author_id` | `string` |  |
| `cover` | `string` |  |
| `create_by` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `discussions_count` | `integer` |  |
| `downloads_count` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `is_official` | `boolean` |  |
| `is_released` | `boolean` |  |
| `is_verified` | `boolean` |  |
| `likes_count` | `integer` |  |
| `metadata` | `models.DatasetMetadata` |  |
| `name` | `string` |  |
| `price` | `number` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `thumbnail` | `string` |  |
| `updated_at` | `string` |  |
| `username` | `string` |  |
| `visibility` | `string` |  |

**`models.DatasetMetadata`**

| Field | Type | Description |
| --- | --- | --- |
| `dataset_id` | `string` |  |
| `id` | `string` |  |
| `language` | `array[string]` | en, vi |
| `license` | `string` |  |
| `pretty_name` | `string` |  |
| `size_category` | `string` |  |
| `tags` | `array[string]` | art |
| `task_categories` | `array[string]` | text-to-image |

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
from aiozai_sdk.generated.models import GetDatasetListRequest

request = GetDatasetListRequest(
    filter_by="...",  # string
    language="...",  # array[string]
    license="...",  # string
    limit="...",  # integer
    offset="...",  # integer
)
resp = client.datasets.dataset.post_public_dataset_list(input=request)
print(resp)
```

---

### `post_public_dataset_list_by_author_by_username`

**`POST /public/dataset/list-by-author/{username}`** — Get public dataset list by user

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `username` | path | `string` | Yes | Username |

**Request Body** — `request.GetDatasetListByAuthorRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `language` | `array[string]` | No |  |
| `license` | `string` | No |  |
| `limit` | `integer` | No |  |
| `offset` | `integer` | No |  |
| `order` | `string` | No | One of: `desc`, `asc` |
| `search` | `string` | No |  |
| `size_category` | `string` | No |  |
| `sort` | `string` | No | One of: `trending`, `likes`, `downloads`, `created`, `created_oldest`, `modified` |
| `tag_type` | `string` | No |  |
| `tags` | `array[string]` | No |  |
| `task_categories` | `array[string]` | No |  |

**Responses**

**200 OK** — `response.DatasetListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.DatasetListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.DatasetListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Dataset]` |  |
| `total` | `integer` |  |

**`models.Dataset`**

| Field | Type | Description |
| --- | --- | --- |
| `author_avatar` | `string` |  |
| `author_id` | `string` |  |
| `cover` | `string` |  |
| `create_by` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `discussions_count` | `integer` |  |
| `downloads_count` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `is_official` | `boolean` |  |
| `is_released` | `boolean` |  |
| `is_verified` | `boolean` |  |
| `likes_count` | `integer` |  |
| `metadata` | `models.DatasetMetadata` |  |
| `name` | `string` |  |
| `price` | `number` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `thumbnail` | `string` |  |
| `updated_at` | `string` |  |
| `username` | `string` |  |
| `visibility` | `string` |  |

**`models.DatasetMetadata`**

| Field | Type | Description |
| --- | --- | --- |
| `dataset_id` | `string` |  |
| `id` | `string` |  |
| `language` | `array[string]` | en, vi |
| `license` | `string` |  |
| `pretty_name` | `string` |  |
| `size_category` | `string` |  |
| `tags` | `array[string]` | art |
| `task_categories` | `array[string]` | text-to-image |

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
from aiozai_sdk.generated.models import GetDatasetListByAuthorRequest

request = GetDatasetListByAuthorRequest(
    language="...",  # array[string]
    license="...",  # string
    limit="...",  # integer
    offset="...",  # integer
    order="...",  # string
)
resp = client.datasets.dataset.post_public_dataset_list_by_author_by_username(input=request)
print(resp)
```

---

### `post_public_dataset_matching_tags`

**`POST /public/dataset/matching-tags`** — Get matching public datasets tags

**Request Body** — `request.MatchingDatasetsTagsRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `language` | `array[string]` | No |  |
| `license` | `string` | No |  |
| `size_category` | `string` | No |  |
| `tag_type` | `string` | No |  |
| `tags` | `array[string]` | No |  |
| `task_categories` | `array[string]` | No |  |

**Responses**

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request |
| 500 | Internal Server Error |

**Example**

```python
from aiozai_sdk.generated.models import MatchingDatasetsTagsRequest

request = MatchingDatasetsTagsRequest(
    language="...",  # array[string]
    license="...",  # string
    size_category="...",  # string
    tag_type="...",  # string
    tags="...",  # array[string]
)
resp = client.datasets.dataset.post_public_dataset_matching_tags(input=request)
print(resp)
```

---

### `get_public_dataset_metadata`

**`GET /public/dataset/metadata`** — Get Dataset Metadata

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

```python
resp = client.datasets.dataset.get_public_dataset_metadata()
print(resp)
```

---

### `get_public_dataset_organization_by_org`

**`GET /public/dataset/organization/{org}`** — Get List Dataset By Org Username

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `org` | path | `string` | Yes | Org's username |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |
| `order` | query | `string` | No |  |
| `sort` | query | `string` | No |  |

**Responses**

**200 OK** — `response.DatasetListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.DatasetListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.DatasetListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Dataset]` |  |
| `total` | `integer` |  |

**`models.Dataset`**

| Field | Type | Description |
| --- | --- | --- |
| `author_avatar` | `string` |  |
| `author_id` | `string` |  |
| `cover` | `string` |  |
| `create_by` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `discussions_count` | `integer` |  |
| `downloads_count` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `is_official` | `boolean` |  |
| `is_released` | `boolean` |  |
| `is_verified` | `boolean` |  |
| `likes_count` | `integer` |  |
| `metadata` | `models.DatasetMetadata` |  |
| `name` | `string` |  |
| `price` | `number` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `thumbnail` | `string` |  |
| `updated_at` | `string` |  |
| `username` | `string` |  |
| `visibility` | `string` |  |

**`models.DatasetMetadata`**

| Field | Type | Description |
| --- | --- | --- |
| `dataset_id` | `string` |  |
| `id` | `string` |  |
| `language` | `array[string]` | en, vi |
| `license` | `string` |  |
| `pretty_name` | `string` |  |
| `size_category` | `string` |  |
| `tags` | `array[string]` | art |
| `task_categories` | `array[string]` | text-to-image |

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
resp = client.datasets.dataset.get_public_dataset_organization_by_org(org="<org>")
print(resp)
```

---

### `get_public_dataset_trending`

**`GET /public/dataset/trending`** — Get List Datasets Trending

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |

**Responses**

**200 OK** — `response.DatasetListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.DatasetListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.DatasetListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Dataset]` |  |
| `total` | `integer` |  |

**`models.Dataset`**

| Field | Type | Description |
| --- | --- | --- |
| `author_avatar` | `string` |  |
| `author_id` | `string` |  |
| `cover` | `string` |  |
| `create_by` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `discussions_count` | `integer` |  |
| `downloads_count` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `is_official` | `boolean` |  |
| `is_released` | `boolean` |  |
| `is_verified` | `boolean` |  |
| `likes_count` | `integer` |  |
| `metadata` | `models.DatasetMetadata` |  |
| `name` | `string` |  |
| `price` | `number` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `thumbnail` | `string` |  |
| `updated_at` | `string` |  |
| `username` | `string` |  |
| `visibility` | `string` |  |

**`models.DatasetMetadata`**

| Field | Type | Description |
| --- | --- | --- |
| `dataset_id` | `string` |  |
| `id` | `string` |  |
| `language` | `array[string]` | en, vi |
| `license` | `string` |  |
| `pretty_name` | `string` |  |
| `size_category` | `string` |  |
| `tags` | `array[string]` | art |
| `task_categories` | `array[string]` | text-to-image |

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
resp = client.datasets.dataset.get_public_dataset_trending()
print(resp)
```

---

### `get_public_dataset_by_id`

**`GET /public/dataset/{id}`** — Get public dataset by id

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Dataset's id |

**Responses**

**200 OK** — `response.DatasetResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.Dataset` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.Dataset`**

| Field | Type | Description |
| --- | --- | --- |
| `author_avatar` | `string` |  |
| `author_id` | `string` |  |
| `cover` | `string` |  |
| `create_by` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `discussions_count` | `integer` |  |
| `downloads_count` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `is_official` | `boolean` |  |
| `is_released` | `boolean` |  |
| `is_verified` | `boolean` |  |
| `likes_count` | `integer` |  |
| `metadata` | `models.DatasetMetadata` |  |
| `name` | `string` |  |
| `price` | `number` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `thumbnail` | `string` |  |
| `updated_at` | `string` |  |
| `username` | `string` |  |
| `visibility` | `string` |  |

**`models.DatasetMetadata`**

| Field | Type | Description |
| --- | --- | --- |
| `dataset_id` | `string` |  |
| `id` | `string` |  |
| `language` | `array[string]` | en, vi |
| `license` | `string` |  |
| `pretty_name` | `string` |  |
| `size_category` | `string` |  |
| `tags` | `array[string]` | art |
| `task_categories` | `array[string]` | text-to-image |

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
resp = client.datasets.dataset.get_public_dataset_by_id(id="<id>")
print(resp)
```

---

### `get_public_dataset_by_username_by_name`

**`GET /public/dataset/{username}/{name}`** — Get public dataset by name

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `username` | path | `string` | Yes | Dataset's username |
| `name` | path | `string` | Yes | Dataset's name |

**Responses**

**200 OK** — `response.DatasetResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.Dataset` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.Dataset`**

| Field | Type | Description |
| --- | --- | --- |
| `author_avatar` | `string` |  |
| `author_id` | `string` |  |
| `cover` | `string` |  |
| `create_by` | `string` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `discussions_count` | `integer` |  |
| `downloads_count` | `integer` |  |
| `id` | `string` |  |
| `is_liked_by_user` | `boolean` |  |
| `is_official` | `boolean` |  |
| `is_released` | `boolean` |  |
| `is_verified` | `boolean` |  |
| `likes_count` | `integer` |  |
| `metadata` | `models.DatasetMetadata` |  |
| `name` | `string` |  |
| `price` | `number` |  |
| `reacted` | `models.Reaction` |  |
| `reactions_statistics` | `array[models.ReactionStats]` |  |
| `thumbnail` | `string` |  |
| `updated_at` | `string` |  |
| `username` | `string` |  |
| `visibility` | `string` |  |

**`models.DatasetMetadata`**

| Field | Type | Description |
| --- | --- | --- |
| `dataset_id` | `string` |  |
| `id` | `string` |  |
| `language` | `array[string]` | en, vi |
| `license` | `string` |  |
| `pretty_name` | `string` |  |
| `size_category` | `string` |  |
| `tags` | `array[string]` | art |
| `task_categories` | `array[string]` | text-to-image |

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
resp = client.datasets.dataset.get_public_dataset_by_username_by_name(username="<username>", name="<name>")
print(resp)
```

---
