# Storage — TypeScript SDK

> File storage — upload, download, and manage files. Requires: `x-api-key` header.

Reference: [SDK Usage Guide](../README.md#sdk-usage-guide) | [Package README](../README.md)

---

### `postStorageUploadCreatePresignedUrl`

**`POST /api-key/storage/upload/create-presigned-url`** — Create Presigned Url

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.CreatePresignedUrlRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `folder` | `string` | Yes | One of: `avatars`, `thumbnails`, `covers`, `samples`, `documents` |
| `mime` | `string` | Yes |  |
| `name` | `string` | Yes |  |
| `org_username` | `string` | No |  |
| `size` | `integer` | Yes |  |

**Responses**

**200 OK** — `response.CreatePresignedUrlResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.CreatePresignedUrlData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.CreatePresignedUrlData`**

| Field | Type | Description |
| --- | --- | --- |
| `download_url` | `string` |  |
| `endpoint` | `string` |  |
| `fields` | `string` |  |
| `message` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { createAiozAIClient, services } from '@aiozai/nodejs-client';

const { rawClient } = createAiozAIClient({ apiKey: process.env.AIOZ_AI_API_KEY });

const response = await services.storage.postStorageUploadCreatePresignedUrl({
    client: rawClient,
    body: {
        folder: '...',  // string  // required
        mime: '...',  // string  // required
        name: '...',  // string  // required
        org_username: '...',  // string
        size: '...',  // integer  // required
    },
});
console.log(response.data);
```

---

### `getStorageUploadStatistics`

**`GET /api-key/storage/upload/statistics`** — Get user upload statistics

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Responses**

**200 OK** — `response.GetUserUploadStatisticsResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.GetUserUploadStatisticsData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.GetUserUploadStatisticsData`**

| Field | Type | Description |
| --- | --- | --- |
| `folders` | `map[string]response.StorageStatistics` |  |
| `total_files` | `integer` |  |
| `total_size` | `integer` |  |

**`response.StorageStatistics`**

| Field | Type | Description |
| --- | --- | --- |
| `total_files` | `integer` |  |
| `total_size` | `integer` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { createAiozAIClient, services } from '@aiozai/nodejs-client';

const { rawClient } = createAiozAIClient({ apiKey: process.env.AIOZ_AI_API_KEY });

const response = await services.storage.getStorageUploadStatistics({ client: rawClient });
console.log(response.data);
```

---

### `getStorageUploadByFolder`

**`GET /api-key/storage/upload/{folder}`** — Get user uploads by folder

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `folder` | path | `string` | Yes | Folder name |
| `orgUsername` | query | `string` | No |  |
| `page` | query | `integer` | No |  |
| `pageSize` | query | `integer` | No |  |
| `type` | query | `string` | No |  |

**Responses**

**200 OK** — `response.GetUserUploadsResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.GetUserUploadsData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.GetUserUploadsData`**

| Field | Type | Description |
| --- | --- | --- |
| `files` | `array[response.ObjectInfo]` |  |
| `total` | `integer` |  |
| `total_pages` | `integer` |  |

**`response.ObjectInfo`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `string` |  |
| `download_url` | `string` |  |
| `folder` | `string` |  |
| `id` | `string` |  |
| `is_expired` | `boolean` |  |
| `key` | `string` |  |
| `mime` | `string` |  |
| `size` | `integer` |  |
| `status` | `boolean` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { createAiozAIClient, services } from '@aiozai/nodejs-client';

const { rawClient } = createAiozAIClient({ apiKey: process.env.AIOZ_AI_API_KEY });

const response = await services.storage.getStorageUploadByFolder({
    client: rawClient,
    path: { folder: '...' },
});
console.log(response.data);
```

---

### `deleteStorageW3sUrl`

**`DELETE /api-key/storage/w3s/url`** — Delete Url

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.DeleteUrlRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `url` | `string` | Yes |  |

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

const response = await services.storage.deleteStorageW3sUrl({
    client: rawClient,
    body: {
        url: '...',  // string  // required
    },
});
console.log(response.data);
```

---
