# Notifications — TypeScript SDK

> Notification management — view and manage notifications. Requires: `x-api-key` header.

Reference: [SDK Usage Guide](../README.md#sdk-usage-guide) | [Package README](../README.md)

---

### `getNotification`

**`GET /api-key/notification`** — Get all notifications

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |
| `sort` | query | `string` | No |  |
| `status` | query | `string` | No |  |

**Responses**

**200 OK** — `response.ListNotificationResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.ListNotificationData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.ListNotificationData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Notification]` |  |
| `total` | `integer` |  |

**`models.Notification`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `string` |  |
| `data` | `map[string]any` |  |
| `id` | `string` |  |
| `message` | `string` |  |
| `status` | `string` |  |
| `title` | `string` |  |
| `updated_at` | `string` |  |
| `user_id` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getNotification } from '@aiozai/nodejs-client';

const response = await getNotification();
console.log(response.data);
```

---

### `deleteNotification`

**`DELETE /api-key/notification`** — Delete all notifications

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `status` | query | `string` | No |  |

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
import { deleteNotification } from '@aiozai/nodejs-client';

const response = await deleteNotification();
console.log(response.data);
```

---

### `putNotificationList`

**`PUT /api-key/notification/list`** — Mark list notification

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.UpdateListNotificationStatusByIdsRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `ids` | `array[string]` | Yes |  |
| `status` | `string` | Yes |  |

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
import { putNotificationList } from '@aiozai/nodejs-client';

const response = await putNotificationList({
    body: {
        ids: '...',  // array[string]  // required
    status: '...',  // string  // required
    },
});
console.log(response.data);
```

---

### `deleteNotificationList`

**`DELETE /api-key/notification/list`** — DeleteNotificationByIds

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.DeleteNotificationByIdsRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `ids` | `array[string]` | Yes |  |

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
import { deleteNotificationList } from '@aiozai/nodejs-client';

const response = await deleteNotificationList({
    body: {
        ids: '...',  // array[string]  // required
    },
});
console.log(response.data);
```

---

### `getNotificationStatistics`

**`GET /api-key/notification/statistics`** — GetNotifyStatisticsByUserId

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Responses**

**200 OK** — `response.NotificationStatisticsResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.NotificationStatisticsData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.NotificationStatisticsData`**

| Field | Type | Description |
| --- | --- | --- |
| `total` | `integer` |  |
| `total_read` | `integer` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getNotificationStatistics } from '@aiozai/nodejs-client';

const response = await getNotificationStatistics();
console.log(response.data);
```

---

### `putNotificationById`

**`PUT /api-key/notification/{id}`** — Update notification by id

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Notification's id |
| `status` | query | `string` | Yes | Notification status |

**Request Body** — `request.UpdateNotificationByIdRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `status` | `string` | Yes |  |

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
import { putNotificationById } from '@aiozai/nodejs-client';

const response = await putNotificationById({
    body: {
        status: '...',  // string  // required
    },
});
console.log(response.data);
```

---

### `deleteNotificationById`

**`DELETE /api-key/notification/{id}`** — Delete notification by id

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | Notification's id |

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
import { deleteNotificationById } from '@aiozai/nodejs-client';

const response = await deleteNotificationById({ path: { id: '...' } });
console.log(response.data);
```

---
