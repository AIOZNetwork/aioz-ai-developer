# Core — Python SDK

> Core platform operations — balance, search, offers, reactions, packages, and tasks. Requires: `x-api-key` header.

Reference: [SDK Usage Guide](../README.md#sdk-usage-guide) | [Package README](../README.md)

---

### `api_key_balance_get`

**`GET /api-key/balance`** — Get Api Key Balance

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Responses**

**200 OK** — `response.WalletWithAddressResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.WalletWithAddress` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.WalletWithAddress`**

| Field | Type | Description |
| --- | --- | --- |
| `balance` | `string` |  |
| `debt` | `string` |  |
| `earnings` | `string` |  |
| `free_balance` | `string` |  |
| `wallet_address` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```python
resp = client.api-keys.api-key.api_key_balance_get()
print(resp)
```

---

### `api_key_comments_id_put`

**`PUT /api-key/comments/{id}`** — Update comment By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Comment's id |

**Request Body** — `request.UpdateCommentRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `content` | `string` | No |  |
| `tag_usernames` | `array[string]` | No |  |

**Responses**

**200 OK** — `response.CommentResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.Comment` |  |
| `message` | `string` |  |
| `status` | `string` |  |

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
from aiozai_sdk.generated.models import UpdateCommentRequest

request = UpdateCommentRequest(
    content="...",  # string
    tag_usernames="...",  # array[string]
)
resp = client.commentss.comments.api_key_comments_id_put(body=request)
print(resp)
```

---

### `api_key_comments_id_delete`

**`DELETE /api-key/comments/{id}`** — Delete comment By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Comment's id |

**Responses**

**200 OK** — `response.CommentResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.Comment` |  |
| `message` | `string` |  |
| `status` | `string` |  |

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
resp = client.commentss.comments.api_key_comments_id_delete(id="<id>")
print(resp)
```

---

### `api_key_dataset_id_like_put`

**`PUT /api-key/dataset/{id}/like`** — Like dataset By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Dataset's id |

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

```python
resp = client.reactions.reaction.api_key_dataset_id_like_put(id="<id>")
print(resp)
```

---

### `api_key_dependency_lib_request_post`

**`POST /api-key/dependency/lib-request`** — Create Dependency Package Request By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.CreateDependencyLibRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `package_name` | `string` | No |  |
| `reason` | `string` | No |  |
| `version` | `string` | No |  |

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

```python
from aiozai_sdk.generated.models import CreateDependencyLibRequest

request = CreateDependencyLibRequest(
    package_name="...",  # string
    reason="...",  # string
    version="...",  # string
)
resp = client.dependencys.dependency.api_key_dependency_lib_request_post(body=request)
print(resp)
```

---

### `api_key_dependency_list_post`

**`POST /api-key/dependency/list`** — Get Dependency List By Api Key

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

**200 OK** — `response.DependencyListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.DependencyListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.DependencyListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Dependency]` |  |
| `total` | `integer` |  |

**`models.Dependency`**

| Field | Type | Description |
| --- | --- | --- |
| `active` | `boolean` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `id` | `string` |  |
| `name` | `string` |  |
| `updated_at` | `string` |  |
| `url` | `map[string]any` |  |
| `version` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```python
resp = client.dependencys.dependency.api_key_dependency_list_post()
print(resp)
```

---

### `api_key_dependency_id_get`

**`GET /api-key/dependency/{id}`** — Get Dependency By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Dependency's id |

**Responses**

**200 OK** — `response.DependencyResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.DependencyData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.DependencyData`**

| Field | Type | Description |
| --- | --- | --- |
| `active` | `boolean` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `id` | `string` |  |
| `name` | `string` |  |
| `updated_at` | `string` |  |
| `url` | `string` |  |
| `version` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```python
resp = client.dependencys.dependency.api_key_dependency_id_get(id="<id>")
print(resp)
```

---

### `api_key_discussion_id_comments_get`

**`GET /api-key/discussion/{id}/comments`** — Get comment list By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

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
resp = client.commentss.comments.api_key_discussion_id_comments_get(id="<id>")
print(resp)
```

---

### `api_key_discussion_id_comments_post`

**`POST /api-key/discussion/{id}/comments`** — Create comment By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Discussion's id |

**Request Body** — `request.CreateCommentRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `content` | `string` | No |  |
| `tag_usernames` | `array[string]` | No |  |

**Responses**

**200 OK** — `response.CommentResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.Comment` |  |
| `message` | `string` |  |
| `status` | `string` |  |

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
from aiozai_sdk.generated.models import CreateCommentRequest

request = CreateCommentRequest(
    content="...",  # string
    tag_usernames="...",  # array[string]
)
resp = client.commentss.comments.api_key_discussion_id_comments_post(body=request)
print(resp)
```

---

### `api_key_items_id_react_put`

**`PUT /api-key/items/{id}/react`** — React item By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Item's id |

**Request Body** — `request.ReactItemRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `itemName` | `string` | No |  |
| `reactName` | `string` | No |  |

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

```python
from aiozai_sdk.generated.models import ReactItemRequest

request = ReactItemRequest(
    itemName="...",  # string
    reactName="...",  # string
)
resp = client.reactions.reaction.api_key_items_id_react_put(body=request)
print(resp)
```

---

### `api_key_model_id_like_put`

**`PUT /api-key/model/{id}/like`** — Like model By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's id |

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

```python
resp = client.reactions.reaction.api_key_model_id_like_put(id="<id>")
print(resp)
```

---

### `api_key_model_id_task_post`

**`POST /api-key/model/{id}/task`** — Distribute Task v2 (Api-Key)

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

```python
from aiozai_sdk.generated.models import DistributeTaskWithApiKeyRequest

request = DistributeTaskWithApiKeyRequest(
    
)
resp = client.api-keys.api-key.api_key_model_id_task_post(body=request)
print(resp)
```

---

### `api_key_offer_invite_post`

**`POST /api-key/offer/invite`** — Create invite to join organization By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.MakeInviteOfferRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `org_username` | `string` | Yes | OrgUsername is the username of the organization (required) |
| `role` | `string` | Yes | Role is the role of the new member (required) |
| `username` | `string` | Yes | Username is the username of the new member (required) |

**Responses**

**Error Responses**

| Status | Description |
| --- | --- |
| 201 | Created |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```python
from aiozai_sdk.generated.models import MakeInviteOfferRequest

request = MakeInviteOfferRequest(
    org_username="...",  # string  # required
    role="...",  # string  # required
    username="...",  # string  # required
)
resp = client.offers.offer.api_key_offer_invite_post(body=request)
print(resp)
```

---

### `api_key_offer_join_post`

**`POST /api-key/offer/join`** — Request to join organization By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.MakeJoinOfferRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `join_id` | `string` | Yes | OrgUsername is the username of the organization (required) |

**Responses**

**200 OK** — `response.MakeOfferResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.MakeOfferData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.MakeOfferData`**

| Field | Type | Description |
| --- | --- | --- |
| `offer` | `models.Offer` |  |

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

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```python
from aiozai_sdk.generated.models import MakeJoinOfferRequest

request = MakeJoinOfferRequest(
    join_id="...",  # string  # required
)
resp = client.offers.offer.api_key_offer_join_post(body=request)
print(resp)
```

---

### `api_key_offer_offer_id_accept_put`

**`PUT /api-key/offer/{offer_id}/accept`** — Accept offer By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `offer_id` | path | `string` | Yes | offer_id |

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

```python
resp = client.offers.offer.api_key_offer_offer_id_accept_put(offer_id="<offer_id>")
print(resp)
```

---

### `api_key_offer_offer_id_deny_put`

**`PUT /api-key/offer/{offer_id}/deny`** — Deny offer By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `offer_id` | path | `string` | Yes | offer_id |

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

```python
resp = client.offers.offer.api_key_offer_offer_id_deny_put(offer_id="<offer_id>")
print(resp)
```

---

### `api_key_offer_offer_id_resend_get`

**`GET /api-key/offer/{offer_id}/resend`** — Resend offer By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `offer_id` | path | `string` | Yes | offer_id |

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

```python
resp = client.offers.offer.api_key_offer_offer_id_resend_get(offer_id="<offer_id>")
print(resp)
```

---

### `api_key_offer_offer_id_revoke_delete`

**`DELETE /api-key/offer/{offer_id}/revoke`** — Revoke offer By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `offer_id` | path | `string` | Yes | offer_id |

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

```python
resp = client.offers.offer.api_key_offer_offer_id_revoke_delete(offer_id="<offer_id>")
print(resp)
```

---

### `api_key_package_api_buy_post`

**`POST /api-key/package/api/buy`** — Buy Api Key Package By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.BuyApiKeyPackageRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `api_key_id` | `string` | No |  |
| `model_id` | `string` | No |  |
| `quantity_uses` | `integer` | No |  |

**Responses**

**200 OK** — `response.ApiPackageResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.ApiPackageData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.ApiPackageData`**

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

```python
from aiozai_sdk.generated.models import BuyApiKeyPackageRequest

request = BuyApiKeyPackageRequest(
    api_key_id="...",  # string
    model_id="...",  # string
    quantity_uses="...",  # integer
)
resp = client.packages.package.api_key_package_api_buy_post(body=request)
print(resp)
```

---

### `api_key_package_buy_cost_post`

**`POST /api-key/package/buy/cost`** — Calculate Cost To Buy Package By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.BuyPlaygroundPackageRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `model_id` | `string` | No |  |
| `quantity_uses` | `integer` | No |  |

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

```python
from aiozai_sdk.generated.models import BuyPlaygroundPackageRequest

request = BuyPlaygroundPackageRequest(
    model_id="...",  # string
    quantity_uses="...",  # integer
)
resp = client.packages.package.api_key_package_buy_cost_post(body=request)
print(resp)
```

---

### `api_key_package_master_buy_cost_post`

**`POST /api-key/package/master/buy/cost`** — Calculate Cost To Buy Master Package By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.BuyPlaygroundMasterPackageRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `quantity_uses` | `integer` | No |  |

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

```python
from aiozai_sdk.generated.models import BuyPlaygroundMasterPackageRequest

request = BuyPlaygroundMasterPackageRequest(
    quantity_uses="...",  # integer
)
resp = client.packages.package.api_key_package_master_buy_cost_post(body=request)
print(resp)
```

---

### `api_key_package_playground_buy_post`

**`POST /api-key/package/playground/buy`** — Unlock Playground Package By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.BuyPlaygroundPackageRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `model_id` | `string` | No |  |
| `quantity_uses` | `integer` | No |  |

**Responses**

**200 OK** — `response.ApiPackageResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.ApiPackageData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.ApiPackageData`**

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

```python
from aiozai_sdk.generated.models import BuyPlaygroundPackageRequest

request = BuyPlaygroundPackageRequest(
    model_id="...",  # string
    quantity_uses="...",  # integer
)
resp = client.packages.package.api_key_package_playground_buy_post(body=request)
print(resp)
```

---

### `api_key_package_id_get`

**`GET /api-key/package/{id}`** — Get Api Package By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | ApiPackage's id |

**Responses**

**200 OK** — `response.ApiPackageResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.ApiPackageData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.ApiPackageData`**

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

```python
resp = client.packages.package.api_key_package_id_get(id="<id>")
print(resp)
```

---

### `api_key_permission_get`

**`GET /api-key/permission`** — Get Api Key Permission

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Responses**

**200 OK** — `response.GetApiKeyPermissionResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.GetApiKeyPermissionData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.GetApiKeyPermissionData`**

| Field | Type | Description |
| --- | --- | --- |
| `api_key_packages` | `array[models.ApiKeyPackage]` |  |
| `limit_models` | `boolean` |  |
| `models` | `array[string]` |  |

**`models.ApiKeyPackage`**

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

```python
resp = client.api-keys.api-key.api_key_permission_get()
print(resp)
```

---

### `api_key_platform_task_dataset_id_training_get`

**`GET /api-key/platform/task/dataset/{id}/training`** — Get List Platform Task By DatasetId And UserId By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Dataset's Id |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |

**Responses**

**200 OK** — `response.QueueTaskListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.QueueTaskListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.QueueTaskListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.QueueTask]` |  |
| `total` | `integer` |  |

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

```python
resp = client.platforms.task.api_key_platform_task_dataset_id_training_get(id="<id>")
print(resp)
```

---

### `api_key_platform_task_model_id_verify_get`

**`GET /api-key/platform/task/model/{id}/verify`** — Get List Platform Task By ModelId And UserId By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Model's Id |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |

**Responses**

**200 OK** — `response.QueueTaskListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.QueueTaskListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.QueueTaskListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.QueueTask]` |  |
| `total` | `integer` |  |

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

```python
resp = client.platforms.task.api_key_platform_task_model_id_verify_get(id="<id>")
print(resp)
```

---

### `api_key_platform_task_id_get`

**`GET /api-key/platform/task/{id}`** — Get Platform Task By Id By Api Key

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

```python
resp = client.platforms.task.api_key_platform_task_id_get(id="<id>")
print(resp)
```

---

### `api_key_search_get`

**`GET /api-key/search`** — Multiple Search By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |
| `search` | query | `string` | Yes |  |

**Responses**

**200 OK** — `response.SearchResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.SearchResponseData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.SearchResponseData`**

| Field | Type | Description |
| --- | --- | --- |
| `competition` | `array[object]` |  |
| `dataset` | `array[object]` |  |
| `model` | `array[object]` |  |
| `organization` | `array[object]` |  |
| `user` | `array[object]` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```python
resp = client.searchs.search.api_key_search_get()
print(resp)
```

---

### `api_key_statistics_post`

**`POST /api-key/statistics`** — Get Api Key Statistics

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

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

```python
from aiozai_sdk.generated.models import GetApiKeyStatisticsByModelIdRequest

request = GetApiKeyStatisticsByModelIdRequest(
    from="...",  # string
    to="...",  # string
)
resp = client.api-keys.api-key.api_key_statistics_post(body=request)
print(resp)
```

---

### `api_key_task_post`

**`POST /api-key/task`** — Distribute Task (Api-Key)

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

```python
from aiozai_sdk.generated.models import DistributeTaskRequest

request = DistributeTaskRequest(
    files="...",  # array[object]
    input_params="...",  # map[string]any
    model_id="...",  # string
)
resp = client.api-keys.api-key.api_key_task_post(body=request)
print(resp)
```

---

### `api_key_task_histories_get`

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

```python
resp = client.api-keys.api-key.api_key_task_histories_get()
print(resp)
```

---

### `api_key_task_id_cancel_delete`

**`DELETE /api-key/task/{id}/cancel`** — Cancel Task By Api Key

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

```python
resp = client.api-keys.api-key.api_key_task_id_cancel_delete(id="<id>")
print(resp)
```

---

### `api_key_task_id_detail_get`

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

```python
resp = client.api-keys.api-key.api_key_task_id_detail_get(id="<id>")
print(resp)
```

---

### `api_key_training_task_id_get`

**`GET /api-key/training-task/{id}`** — Get Training Task By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Training Task's id |

**Responses**

**200 OK** — `response.TrainingTaskResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.TrainingTaskData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.TrainingTaskData`**

| Field | Type | Description |
| --- | --- | --- |
| `active` | `boolean` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `id` | `string` |  |
| `metadata` | `string` |  |
| `name` | `string` |  |
| `updated_at` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```python
resp = client.trainings.task.api_key_training_task_id_get(id="<id>")
print(resp)
```

---

### `api_key_training_task_list_get`

**`GET /api-key/training/task/list`** — Get Training Task List By Api Key

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

**200 OK** — `response.TrainingTaskListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.TrainingTaskListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.TrainingTaskListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.TrainingTask]` |  |
| `total` | `integer` |  |

**`models.TrainingTask`**

| Field | Type | Description |
| --- | --- | --- |
| `active` | `boolean` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `id` | `string` |  |
| `metadata` | `map[string]any` |  |
| `name` | `string` |  |
| `updated_at` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```python
resp = client.trainings.task.api_key_training_task_list_get()
print(resp)
```

---
