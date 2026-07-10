# Public — Python SDK

> Public endpoints — metadata, token prices, and cost estimation. Public — no authentication required.

Reference: [SDK Usage Guide](../README.md#sdk-usage-guide) | [Package README](../README.md)

---

### `post_public_cost_estimating`

**`POST /api-key/public/cost/estimating`** — Estimate storage cost

**Request Body** — `request.EstimateCostRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `total_size` | `number` | Yes |  |

**Responses**

**200 OK** — `response.EstimateStorageCostResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `utils.StorageCost` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`utils.StorageCost`**

| Field | Type | Description |
| --- | --- | --- |
| `bandwidth` | `number` |  |
| `delivery` | `number` |  |
| `storage` | `number` |  |
| `symbol` | `string` |  |
| `unit` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```python
from aiozai_sdk.generated.models import EstimateCostRequest

request = EstimateCostRequest(
    total_size="...",  # number  # required
)
resp = client.public.public.post_public_cost_estimating(input=request)
print(resp)
```

---

### `get_public_metadata`

**`GET /api-key/public/metadata`** — Get list metadata

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `category` | query | `string` | No |  |
| `types` | query | `array` | No |  |

**Responses**

**200 OK** — `response.GetListMetadataResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `array[models.MetadataListByType]` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.MetadataListByType`**

| Field | Type | Description |
| --- | --- | --- |
| `items` | `array[models.LiteMetadata]` |  |
| `type` | `string` |  |

**`models.LiteMetadata`**

| Field | Type | Description |
| --- | --- | --- |
| `id` | `string` |  |
| `label` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```python
resp = client.public.public.get_public_metadata()
print(resp)
```

---

### `get_public_token_price`

**`GET /api-key/public/token/price`** — Get Aioz token price

**Responses**

**200 OK** — `response.GetTokenPriceResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `utils.GetTokenInfoData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`utils.GetTokenInfoData`**

| Field | Type | Description |
| --- | --- | --- |
| `change_percentage_24h` | `number` |  |
| `circulating_supply` | `number` |  |
| `current_price` | `number` |  |
| `fully_diluted_valuation` | `number` |  |
| `high_24_h` | `number` |  |
| `last_updated` | `string` |  |
| `low_24_h` | `number` |  |
| `market_cap` | `number` |  |
| `rank` | `integer` |  |
| `total_supply` | `number` |  |
| `volume_24_h` | `number` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```python
resp = client.public.public.get_public_token_price()
print(resp)
```

---

### `get_public_user_by_username_medals`

**`GET /api-key/public/user/{username}/medals`** — Get user medals by medal name

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `username` | path | `string` | Yes | Username |
| `limit` | query | `integer` | No |  |
| `medalName` | query | `string` | Yes |  |
| `offset` | query | `integer` | No |  |

**Responses**

**200 OK** — `response.UserMedalListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.UserMedalListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.UserMedalListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.UserMedal]` |  |
| `total` | `integer` |  |

**`models.UserMedal`**

| Field | Type | Description |
| --- | --- | --- |
| `competition` | `models.Competition` |  |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `medal_name` | `string` |  |
| `rank` | `integer` |  |
| `updated_at` | `string` |  |
| `user_id` | `string` |  |

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

```python
resp = client.public.public.get_public_user_by_username_medals(username="<username>")
print(resp)
```

---

### `get_public_user_by_username_medals_statistics`

**`GET /api-key/public/user/{username}/medals/statistics`** — Get user medal statistics by username

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `username` | path | `string` | Yes | Username |

**Responses**

**200 OK** — `response.MedalStatisticResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.MedalStatistic` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.MedalStatistic`**

| Field | Type | Description |
| --- | --- | --- |
| `count` | `integer` |  |
| `medal_name` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```python
resp = client.public.public.get_public_user_by_username_medals_statistics(username="<username>")
print(resp)
```

---
