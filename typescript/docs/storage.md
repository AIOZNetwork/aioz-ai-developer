# Storage — TypeScript SDK

> File storage — upload, download, and manage files. Requires: `x-api-key` header.

Reference: [SDK Usage Guide](../README.md#sdk-usage-guide) | [Package README](../README.md)

---

### `postApiKeyStorageUploadCreatePresignedUrl`

**`POST /api-key/storage/upload/create-presigned-url`** — Create Presigned Url By Api Key

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
| 400 | Bad Request — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { postApiKeyStorageUploadCreatePresignedUrl } from '@aiozai/nodejs-client';

const response = await postApiKeyStorageUploadCreatePresignedUrl({
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

### `getApiKeyStorageUploadStatistics`

**`GET /api-key/storage/upload/statistics`** — Get user upload statistics by api key

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
| `count` | `integer` |  |
| `folders` | `map[string]any` |  |
| `storage` | `integer` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getApiKeyStorageUploadStatistics } from '@aiozai/nodejs-client';

const response = await getApiKeyStorageUploadStatistics();
console.log(response.data);
```

---

### `getApiKeyStorageUploadByFolder`

**`GET /api-key/storage/upload/{folder}`** — Get user uploads by folder by api key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `page` | query | `integer` | No | Page is the page number (default: 1) (optional) |
| `pageSize` | query | `integer` | No | PageSize is the page size (default: 10) (optional) |
| `search` | query | `string` | No |  |

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
| `count` | `integer` |  |
| `storage` | `integer` |  |
| `urls` | `array[string]` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getApiKeyStorageUploadByFolder } from '@aiozai/nodejs-client';

const response = await getApiKeyStorageUploadByFolder();
console.log(response.data);
```

---

### `deleteApiKeyStorageW3sUrl`

**`DELETE /api-key/storage/w3s/url`** — Delete Url By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.DeleteUrlRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `url` | `string` | Yes |  |

**Responses**

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { deleteApiKeyStorageW3sUrl } from '@aiozai/nodejs-client';

const response = await deleteApiKeyStorageW3sUrl({
    body: {
        url: '...',  // string  // required
    },
});
console.log(response.data);
```

---
