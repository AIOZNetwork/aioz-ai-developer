# Public — Python SDK

> Public endpoints — health checks, public listings, and medals. Public — no authentication required.

Reference: [SDK Usage Guide](../README.md#sdk-usage-guide) | [Package README](../README.md)

---

### `public_content_terms_privacy_get`

**`GET /public/content/terms-privacy`** — Get Content Config By Static Keys

**Responses**

**200 OK** — `response.ContentConfigResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.ContentConfig` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.ContentConfig`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `key` | `string` |  |
| `updated_at` | `string` |  |
| `value` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```python
resp = client.publics.public.public_content_terms_privacy_get()
print(resp)
```

---

### `public_content_keys_get`

**`GET /public/content/{keys}`** — Get Content Config By List Keys

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `keys` | path | `string` | Yes | List Keys |

**Responses**

**200 OK** — `response.ContentConfigListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.ContentConfigListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.ContentConfigListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.ContentConfig]` |  |
| `total` | `integer` |  |

**`models.ContentConfig`**

| Field | Type | Description |
| --- | --- | --- |
| `created_at` | `string` |  |
| `id` | `string` |  |
| `key` | `string` |  |
| `updated_at` | `string` |  |
| `value` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```python
resp = client.publics.public.public_content_keys_get(keys="<keys>")
print(resp)
```

---

### `public_cost_estimating_post`

**`POST /public/cost/estimating`** — Estimate Cost

**Request Body** — `request.EstimateCostRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `total_size` | `number` | Yes |  |

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
from aiozai_sdk.generated.models import EstimateCostRequest

request = EstimateCostRequest(
    total_size="...",  # number  # required
)
resp = client.publics.public.public_cost_estimating_post(body=request)
print(resp)
```

---

### `public_metadata_get`

**`GET /public/metadata`** — GetListMetadata

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `category` | query | `string` | No |  |
| `types` | query | `array` | No |  |

**Responses**

**200 OK** — `response.MetadataResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.Metadata` |  |
| `message` | `string` |  |
| `status` | `string` |  |

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
resp = client.publics.public.public_metadata_get()
print(resp)
```

---

### `public_repository_ownerUsername_repositoryName_content_readme_get`

**`GET /public/repository/{ownerUsername}/{repositoryName}/content/readme`** — Get readme file content public

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `ownerUsername` | path | `string` | Yes | repository's owner |
| `repositoryName` | path | `string` | Yes | repository's name |
| `repoType` | query | `string` | No | allow: dataset, model |

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
resp = client.publics.public.public_repository_ownerUsername_repositoryName_content_readme_get(ownerUsername="<ownerUsername>", repositoryName="<repositoryName>")
print(resp)
```

---

### `public_search_get`

**`GET /public/search`** — Multiple Search

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
resp = client.publics.public.public_search_get()
print(resp)
```

---

### `public_search_user_get`

**`GET /public/search/user`** — Search Public Users

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |
| `search` | query | `string` | Yes |  |

**Responses**

**200 OK** — `response.UserListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.UserListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.UserListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.UserInfo]` |  |
| `total` | `integer` |  |

**`models.UserInfo`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `bio` | `string` |  |
| `fullname` | `string` |  |
| `github_link` | `string` |  |
| `home_page` | `string` |  |
| `id` | `string` |  |
| `interests` | `string` |  |
| `twitter_link` | `string` |  |
| `twitter_name` | `string` |  |
| `type` | `string` |  |
| `username` | `string` |  |
| `visibility` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```python
resp = client.publics.public.public_search_user_get()
print(resp)
```

---

### `public_token_price_get`

**`GET /public/token/price`** — Get Aioz Price

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
resp = client.publics.public.public_token_price_get()
print(resp)
```

---

### `public_user_username_get`

**`GET /public/user/{username}`** — Get user's info

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `username` | path | `string` | Yes | username |

**Responses**

**200 OK** — `response.GetUserByUsernameAndGuestIdResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.GetUserByUsernameAndGuestIdData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.GetUserByUsernameAndGuestIdData`**

| Field | Type | Description |
| --- | --- | --- |
| `user` | `models.LiteUser` |  |

**`models.LiteUser`**

| Field | Type | Description |
| --- | --- | --- |
| `allow_request_to_join` | `boolean` |  |
| `avatar_url` | `string` |  |
| `bio` | `string` |  |
| `blocked` | `boolean` |  |
| `followers` | `array[models.Follow]` |  |
| `followers_count` | `integer` |  |
| `followings` | `array[models.Follow]` |  |
| `followings_count` | `integer` |  |
| `github_link` | `string` |  |
| `github_name` | `string` |  |
| `home_page_name` | `string` |  |
| `id` | `string` |  |
| `interests` | `string` |  |
| `invite_offers` | `array[models.Offer]` |  |
| `invite_offers_count` | `integer` |  |
| `is_following` | `boolean` |  |
| `join_id` | `string` |  |
| `join_offers` | `array[models.Offer]` |  |
| `join_offers_count` | `integer` |  |
| `members` | `array[models.Member]` |  |
| `members_count` | `integer` |  |
| `name` | `string` |  |
| `role` | `string` |  |
| `token` | `string` |  |
| `twitter_link` | `string` |  |
| `twitter_name` | `string` |  |
| `type` | `string` |  |
| `username` | `string` |  |
| `verified` | `boolean` |  |
| `visibility` | `string` |  |

**`models.Follow`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `name` | `string` |  |
| `username` | `string` |  |

**`models.Follow`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `id` | `string` |  |
| `name` | `string` |  |
| `username` | `string` |  |

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

**`models.Member`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar_url` | `string` |  |
| `full_name` | `string` |  |
| `id` | `string` |  |
| `username` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```python
resp = client.publics.public.public_user_username_get(username="<username>")
print(resp)
```

---

### `public_user_username_existed_get`

**`GET /public/user/{username}/existed`** — Check if a username have already existed

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `username` | path | `string` | Yes | username |

**Responses**

**200 OK** — `response.CheckUsernameExistResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.CheckUsernameExistData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.CheckUsernameExistData`**

| Field | Type | Description |
| --- | --- | --- |
| `existed` | `boolean` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```python
resp = client.publics.public.public_user_username_existed_get(username="<username>")
print(resp)
```

---

### `public_user_username_medals_get`

**`GET /public/user/{username}/medals`** — Get user medals by medal name

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
resp = client.medalss.medals.public_user_username_medals_get(username="<username>")
print(resp)
```

---

### `public_user_username_medals_statistics_get`

**`GET /public/user/{username}/medals/statistics`** — Get user medal statistics by username

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
resp = client.medalss.medals.public_user_username_medals_statistics_get(username="<username>")
print(resp)
```

---

### `public_user_username_organizations_get`

**`GET /public/user/{username}/organizations`** — Get public user's organizations by username

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `username` | path | `string` | Yes | username |
| `keyword` | query | `string` | No |  |
| `page` | query | `integer` | No | Page is the page number (default: 1) (optional) |
| `pageSize` | query | `integer` | No | PageSize is the page size (default: 10) (optional) |

**Responses**

**200 OK** — `response.GetUserOrganizationsResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.GetUserOrganizationsData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.GetUserOrganizationsData`**

| Field | Type | Description |
| --- | --- | --- |
| `organizations` | `array[models.OrganizationInfo]` |  |
| `total` | `integer` |  |

**`models.OrganizationInfo`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar` | `string` |  |
| `full_name` | `string` |  |
| `id` | `string` |  |
| `org_type` | `string` |  |
| `permission` | `map[string]any` |  |
| `type` | `string` |  |
| `username` | `string` |  |
| `verified` | `boolean` |  |
| `visibility` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```python
resp = client.publics.public.public_user_username_organizations_get(username="<username>")
print(resp)
```

---
