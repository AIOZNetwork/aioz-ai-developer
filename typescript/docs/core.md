# Core — TypeScript SDK

> Core platform operations — balance, search, offers, reactions, packages, and tasks. Requires: `x-api-key` header.

Reference: [SDK Usage Guide](../README.md#sdk-usage-guide) | [Package README](../README.md)

---

### `getApiKeyBalance`

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
| `balance` | `number` |  |
| `debt` | `number` |  |
| `earnings` | `number` |  |
| `free_balance` | `number` |  |
| `wallet_address` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getApiKeyBalance } from '@aiozai/nodejs-client';

const response = await getApiKeyBalance();
console.log(response.data);
```

---

### `putApiKeyCommentsById`

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

```typescript
import { putApiKeyCommentsById } from '@aiozai/nodejs-client';

const response = await putApiKeyCommentsById({
    body: {
        content: '...',  // string
    tag_usernames: '...',  // array[string]
    },
});
console.log(response.data);
```

---

### `deleteApiKeyCommentsById`

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

```typescript
import { deleteApiKeyCommentsById } from '@aiozai/nodejs-client';

const response = await deleteApiKeyCommentsById({ path: { id: '...' } });
console.log(response.data);
```

---

### `putApiKeyDatasetByIdLike`

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

```typescript
import { putApiKeyDatasetByIdLike } from '@aiozai/nodejs-client';

const response = await putApiKeyDatasetByIdLike({ path: { id: '...' } });
console.log(response.data);
```

---

### `postApiKeyDependencyLibRequest`

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

```typescript
import { postApiKeyDependencyLibRequest } from '@aiozai/nodejs-client';

const response = await postApiKeyDependencyLibRequest({
    body: {
        package_name: '...',  // string
    reason: '...',  // string
    version: '...',  // string
    },
});
console.log(response.data);
```

---

### `postApiKeyDependencyList`

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

```typescript
import { postApiKeyDependencyList } from '@aiozai/nodejs-client';

const response = await postApiKeyDependencyList();
console.log(response.data);
```

---

### `getApiKeyDependencyById`

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

```typescript
import { getApiKeyDependencyById } from '@aiozai/nodejs-client';

const response = await getApiKeyDependencyById({ path: { id: '...' } });
console.log(response.data);
```

---

### `getApiKeyDiscussionByIdComments`

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

```typescript
import { getApiKeyDiscussionByIdComments } from '@aiozai/nodejs-client';

const response = await getApiKeyDiscussionByIdComments({ path: { id: '...' } });
console.log(response.data);
```

---

### `postApiKeyDiscussionByIdComments`

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

```typescript
import { postApiKeyDiscussionByIdComments } from '@aiozai/nodejs-client';

const response = await postApiKeyDiscussionByIdComments({
    body: {
        content: '...',  // string
    tag_usernames: '...',  // array[string]
    },
});
console.log(response.data);
```

---

### `putApiKeyItemsByIdReact`

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

```typescript
import { putApiKeyItemsByIdReact } from '@aiozai/nodejs-client';

const response = await putApiKeyItemsByIdReact({
    body: {
        itemName: '...',  // string
    reactName: '...',  // string
    },
});
console.log(response.data);
```

---

### `putApiKeyModelByIdLike`

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

```typescript
import { putApiKeyModelByIdLike } from '@aiozai/nodejs-client';

const response = await putApiKeyModelByIdLike({ path: { id: '...' } });
console.log(response.data);
```

---

### `postApiKeyModelByIdTask`

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

```typescript
import { postApiKeyModelByIdTask } from '@aiozai/nodejs-client';

const response = await postApiKeyModelByIdTask({
    body: {
        
    },
});
console.log(response.data);
```

---

### `postApiKeyOfferInvite`

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

```typescript
import { postApiKeyOfferInvite } from '@aiozai/nodejs-client';

const response = await postApiKeyOfferInvite({
    body: {
        org_username: '...',  // string  // required
    role: '...',  // string  // required
    username: '...',  // string  // required
    },
});
console.log(response.data);
```

---

### `postApiKeyOfferJoin`

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

```typescript
import { postApiKeyOfferJoin } from '@aiozai/nodejs-client';

const response = await postApiKeyOfferJoin({
    body: {
        join_id: '...',  // string  // required
    },
});
console.log(response.data);
```

---

### `putApiKeyOfferByOffer_idAccept`

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

```typescript
import { putApiKeyOfferByOffer_idAccept } from '@aiozai/nodejs-client';

const response = await putApiKeyOfferByOffer_idAccept({ path: { offer_id: '...' } });
console.log(response.data);
```

---

### `putApiKeyOfferByOffer_idDeny`

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

```typescript
import { putApiKeyOfferByOffer_idDeny } from '@aiozai/nodejs-client';

const response = await putApiKeyOfferByOffer_idDeny({ path: { offer_id: '...' } });
console.log(response.data);
```

---

### `getApiKeyOfferByOffer_idResend`

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

```typescript
import { getApiKeyOfferByOffer_idResend } from '@aiozai/nodejs-client';

const response = await getApiKeyOfferByOffer_idResend({ path: { offer_id: '...' } });
console.log(response.data);
```

---

### `deleteApiKeyOfferByOffer_idRevoke`

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

```typescript
import { deleteApiKeyOfferByOffer_idRevoke } from '@aiozai/nodejs-client';

const response = await deleteApiKeyOfferByOffer_idRevoke({ path: { offer_id: '...' } });
console.log(response.data);
```

---

### `postApiKeyPackageApiBuy`

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

```typescript
import { postApiKeyPackageApiBuy } from '@aiozai/nodejs-client';

const response = await postApiKeyPackageApiBuy({
    body: {
        api_key_id: '...',  // string
    model_id: '...',  // string
    quantity_uses: '...',  // integer
    },
});
console.log(response.data);
```

---

### `postApiKeyPackageBuyCost`

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

```typescript
import { postApiKeyPackageBuyCost } from '@aiozai/nodejs-client';

const response = await postApiKeyPackageBuyCost({
    body: {
        model_id: '...',  // string
    quantity_uses: '...',  // integer
    },
});
console.log(response.data);
```

---

### `postApiKeyPackageMasterBuyCost`

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

```typescript
import { postApiKeyPackageMasterBuyCost } from '@aiozai/nodejs-client';

const response = await postApiKeyPackageMasterBuyCost({
    body: {
        quantity_uses: '...',  // integer
    },
});
console.log(response.data);
```

---

### `postApiKeyPackagePlaygroundBuy`

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

```typescript
import { postApiKeyPackagePlaygroundBuy } from '@aiozai/nodejs-client';

const response = await postApiKeyPackagePlaygroundBuy({
    body: {
        model_id: '...',  // string
    quantity_uses: '...',  // integer
    },
});
console.log(response.data);
```

---

### `getApiKeyPackageById`

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

```typescript
import { getApiKeyPackageById } from '@aiozai/nodejs-client';

const response = await getApiKeyPackageById({ path: { id: '...' } });
console.log(response.data);
```

---

### `getApiKeyPermission`

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

```typescript
import { getApiKeyPermission } from '@aiozai/nodejs-client';

const response = await getApiKeyPermission();
console.log(response.data);
```

---

### `getApiKeyPlatformTaskDatasetByIdTraining`

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

```typescript
import { getApiKeyPlatformTaskDatasetByIdTraining } from '@aiozai/nodejs-client';

const response = await getApiKeyPlatformTaskDatasetByIdTraining({ path: { id: '...' } });
console.log(response.data);
```

---

### `getApiKeyPlatformTaskModelByIdVerify`

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

```typescript
import { getApiKeyPlatformTaskModelByIdVerify } from '@aiozai/nodejs-client';

const response = await getApiKeyPlatformTaskModelByIdVerify({ path: { id: '...' } });
console.log(response.data);
```

---

### `getApiKeyPlatformTaskById`

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

```typescript
import { getApiKeyPlatformTaskById } from '@aiozai/nodejs-client';

const response = await getApiKeyPlatformTaskById({ path: { id: '...' } });
console.log(response.data);
```

---

### `getApiKeySearch`

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

```typescript
import { getApiKeySearch } from '@aiozai/nodejs-client';

const response = await getApiKeySearch();
console.log(response.data);
```

---

### `postApiKeyStatistics`

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

```typescript
import { postApiKeyStatistics } from '@aiozai/nodejs-client';

const response = await postApiKeyStatistics({
    body: {
        from: '...',  // string
    to: '...',  // string
    },
});
console.log(response.data);
```

---

### `postApiKeyTask`

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

```typescript
import { postApiKeyTask } from '@aiozai/nodejs-client';

const response = await postApiKeyTask({
    body: {
        files: '...',  // array[object]
    input_params: '...',  // map[string]any
    model_id: '...',  // string
    },
});
console.log(response.data);
```

---

### `getApiKeyTaskHistories`

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
import { getApiKeyTaskHistories } from '@aiozai/nodejs-client';

const response = await getApiKeyTaskHistories();
console.log(response.data);
```

---

### `deleteApiKeyTaskByIdCancel`

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

```typescript
import { deleteApiKeyTaskByIdCancel } from '@aiozai/nodejs-client';

const response = await deleteApiKeyTaskByIdCancel({ path: { id: '...' } });
console.log(response.data);
```

---

### `getApiKeyTaskByIdDetail`

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
import { getApiKeyTaskByIdDetail } from '@aiozai/nodejs-client';

const response = await getApiKeyTaskByIdDetail({ path: { id: '...' } });
console.log(response.data);
```

---

### `getApiKeyTrainingTaskById`

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

```typescript
import { getApiKeyTrainingTaskById } from '@aiozai/nodejs-client';

const response = await getApiKeyTrainingTaskById({ path: { id: '...' } });
console.log(response.data);
```

---

### `getApiKeyTrainingTaskList`

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

```typescript
import { getApiKeyTrainingTaskList } from '@aiozai/nodejs-client';

const response = await getApiKeyTrainingTaskList();
console.log(response.data);
```

---
