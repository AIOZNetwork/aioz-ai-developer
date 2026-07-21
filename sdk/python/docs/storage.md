# Storage — Python SDK

> File storage — upload, download, and manage files. Requires: `x-api-key` header.

Reference: [SDK Usage Guide](../README.md#sdk-usage-guide) | [Package README](../README.md)

---

### `post_storage_upload_create_presigned_url`

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

```python
from aiozai_sdk.generated.models import RequestCreatePresignedUrlRequest

request = RequestCreatePresignedUrlRequest(
    folder="...",  # string  # required
    mime="...",  # string  # required
    name="...",  # string  # required
    org_username="...",  # string
    size="...",  # integer  # required
)
resp = client.storage.storage.post_storage_upload_create_presigned_url(input=request)
print(resp)
```

---

### `get_storage_upload_statistics`

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

```python
resp = client.storage.storage.get_storage_upload_statistics()
print(resp)
```

---

### `get_storage_upload_by_folder`

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

```python
resp = client.storage.storage.get_storage_upload_by_folder(folder="<folder>")
print(resp)
```

---

### `delete_storage_w3s_url`

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

```python
from aiozai_sdk.generated.models import RequestDeleteUrlRequest

request = RequestDeleteUrlRequest(
    url="...",  # string  # required
)
resp = client.storage.storage.delete_storage_w3s_url(input=request)
print(resp)
```

---
