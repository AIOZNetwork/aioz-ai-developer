# Users — TypeScript SDK

> User management — profiles, keys, wallets, and vouchers. Requires: `x-api-key` header.

Reference: [SDK Usage Guide](../README.md#sdk-usage-guide) | [Package README](../README.md)

---

### `deleteApiKeyUser`

**`DELETE /api-key/user`** — Delete user's account By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

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
import { deleteApiKeyUser } from '@aioz-network/aiozai-sdk';

const response = await deleteApiKeyUser();
console.log(response.data);
```

---

### `postApiKeyUserApiKey`

**`POST /api-key/user/api-key`** — Create ApiKey By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.CreateApiKeyRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `active` | `boolean` | No |  |
| `description` | `string` | No |  |
| `name` | `string` | Yes |  |
| `org_username` | `string` | No |  |

**Responses**

**200 OK** — `response.ApiKeyResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.ApiKey` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.ApiKey`**

| Field | Type | Description |
| --- | --- | --- |
| `active` | `boolean` |  |
| `api_key` | `string` |  |
| `api_price` | `number` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `id` | `string` |  |
| `input_format` | `map[string]any` |  |
| `model_id` | `string` |  |
| `name` | `string` |  |
| `output_format` | `map[string]any` |  |
| `total_cost` | `number` |  |
| `total_failed` | `integer` |  |
| `total_request` | `integer` |  |
| `total_success` | `integer` |  |
| `updated_at` | `string` |  |
| `user` | `models.User` |  |
| `user_id` | `string` |  |

**`models.User`**

| Field | Type | Description |
| --- | --- | --- |
| `allow_request_to_join` | `boolean` |  |
| `avatar_url` | `string` |  |
| `bio` | `string` |  |
| `blocked` | `boolean` |  |
| `blocked_at` | `string` |  |
| `email` | `string` |  |
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
| `wallet` | `models.Wallet` |  |
| `wallet_address` | `string` |  |
| `wallet_connection` | `string` |  |

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

**`models.Wallet`**

| Field | Type | Description |
| --- | --- | --- |
| `balance` | `number` |  |
| `debt` | `number` |  |
| `earnings` | `number` |  |
| `free_balance` | `number` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { postApiKeyUserApiKey } from '@aioz-network/aiozai-sdk';

const response = await postApiKeyUserApiKey({
    body: {
        active: '...',  // boolean
    description: '...',  // string
    name: '...',  // string  // required
    org_username: '...',  // string
    },
});
console.log(response.data);
```

---

### `getApiKeyUserChallengeByWalletaddress`

**`GET /api-key/user/challenge/{walletAddress}`** — Get link wallet address challenge By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `walletAddress` | path | `string` | Yes | wallet address |

**Responses**

**200 OK** — `response.GetLinkWalletAddressChallengeResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.GetLinkWalletAddressChallengeData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.GetLinkWalletAddressChallengeData`**

| Field | Type | Description |
| --- | --- | --- |
| `challenge` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getApiKeyUserChallengeByWalletaddress } from '@aioz-network/aiozai-sdk';

const response = await getApiKeyUserChallengeByWalletaddress({ path: { walletAddress: '...' } });
console.log(response.data);
```

---

### `patchApiKeyUserChangePassword`

**`PATCH /api-key/user/change-password`** — Change user's password By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.ChangeUserPasswordRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `new_password` | `string` | Yes | User's new password (required) |
| `old_password` | `string` | Yes | User's old passowrd (required) |

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
import { patchApiKeyUserChangePassword } from '@aioz-network/aiozai-sdk';

const response = await patchApiKeyUserChangePassword({
    body: {
        new_password: '...',  // string  // required
    old_password: '...',  // string  // required
    },
});
console.log(response.data);
```

---

### `putApiKeyUserFollowById`

**`PUT /api-key/user/follow/{id}`** — Follow/Unfollow user By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `id` | path | `string` | Yes | user's id |

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
import { putApiKeyUserFollowById } from '@aioz-network/aiozai-sdk';

const response = await putApiKeyUserFollowById({ path: { id: '...' } });
console.log(response.data);
```

---

### `postApiKeyUserLinkEmail`

**`POST /api-key/user/link-email`** — Verify link email code By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.VerifyLinkEmailCodeRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `code` | `string` | Yes |  |
| `email` | `string` | Yes |  |

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
import { postApiKeyUserLinkEmail } from '@aioz-network/aiozai-sdk';

const response = await postApiKeyUserLinkEmail({
    body: {
        code: '...',  // string  // required
    email: '...',  // string  // required
    },
});
console.log(response.data);
```

---

### `patchApiKeyUserLinkEmailByEmail`

**`PATCH /api-key/user/link-email/{email}`** — Get link email code By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `email` | path | `string` | Yes | user's email |

**Request Body** — `request.GetLinkEmailCodeRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `email` | `string` | No |  |
| `password` | `string` | No |  |
| `username` | `string` | Yes | Username is the username of the user (required) |

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
import { patchApiKeyUserLinkEmailByEmail } from '@aioz-network/aiozai-sdk';

const response = await patchApiKeyUserLinkEmailByEmail({
    body: {
        email: '...',  // string
    password: '...',  // string
    username: '...',  // string  // required
    },
});
console.log(response.data);
```

---

### `postApiKeyUserLinkWallet`

**`POST /api-key/user/link-wallet`** — Verify link wallet address signature By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.VerifyLinkWalletAddressSignatureRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `signature` | `string` | Yes |  |
| `wallet_address` | `string` | Yes |  |

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
import { postApiKeyUserLinkWallet } from '@aioz-network/aiozai-sdk';

const response = await postApiKeyUserLinkWallet({
    body: {
        signature: '...',  // string  // required
    wallet_address: '...',  // string  // required
    },
});
console.log(response.data);
```

---

### `getApiKeyUserMe`

**`GET /api-key/user/me`** — Get user's info By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Responses**

**200 OK** — `response.GetMeResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.GetMeData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.GetMeData`**

| Field | Type | Description |
| --- | --- | --- |
| `user` | `models.User` |  |

**`models.User`**

| Field | Type | Description |
| --- | --- | --- |
| `allow_request_to_join` | `boolean` |  |
| `avatar_url` | `string` |  |
| `bio` | `string` |  |
| `blocked` | `boolean` |  |
| `blocked_at` | `string` |  |
| `email` | `string` |  |
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
| `wallet` | `models.Wallet` |  |
| `wallet_address` | `string` |  |
| `wallet_connection` | `string` |  |

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

**`models.Wallet`**

| Field | Type | Description |
| --- | --- | --- |
| `balance` | `number` |  |
| `debt` | `number` |  |
| `earnings` | `number` |  |
| `free_balance` | `number` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getApiKeyUserMe } from '@aioz-network/aiozai-sdk';

const response = await getApiKeyUserMe();
console.log(response.data);
```

---

### `getApiKeyUserOffers`

**`GET /api-key/user/offers`** — Get user's offers By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `keyword` | query | `string` | No |  |
| `offerType` | query | `string` | Yes |  |
| `page` | query | `integer` | No | Page is the page number (default: 1) (optional) |
| `pageSize` | query | `integer` | No | PageSize is the page size (default: 10) (optional) |

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
import { getApiKeyUserOffers } from '@aioz-network/aiozai-sdk';

const response = await getApiKeyUserOffers();
console.log(response.data);
```

---

### `getApiKeyUserOrgUsernames`

**`GET /api-key/user/org-usernames`** — Get user's organization usernames By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Responses**

**200 OK** — `response.GetUserOrganizationUsernamesResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.GetUserOrganizationUsernamesData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.GetUserOrganizationUsernamesData`**

| Field | Type | Description |
| --- | --- | --- |
| `users` | `array[models.TinyUser]` |  |

**`models.TinyUser`**

| Field | Type | Description |
| --- | --- | --- |
| `avatar_url` | `string` |  |
| `bio` | `string` |  |
| `github_link` | `string` |  |
| `github_name` | `string` |  |
| `home_page_name` | `string` |  |
| `id` | `string` |  |
| `interests` | `string` |  |
| `name` | `string` |  |
| `twitter_link` | `string` |  |
| `twitter_name` | `string` |  |
| `username` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getApiKeyUserOrgUsernames } from '@aioz-network/aiozai-sdk';

const response = await getApiKeyUserOrgUsernames();
console.log(response.data);
```

---

### `getApiKeyUserPermissionSearch`

**`GET /api-key/user/permission/search`** — Search Users By Api Key

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

```typescript
import { getApiKeyUserPermissionSearch } from '@aioz-network/aiozai-sdk';

const response = await getApiKeyUserPermissionSearch();
console.log(response.data);
```

---

### `patchApiKeyUserProfile`

**`PATCH /api-key/user/profile`** — Update user's profile By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.UpdateUserProfileRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `avatar` | `string` | No | Avatar is the avatar of the user (optional) |
| `bio` | `string` | No | Bio is the full name of the user (optional) |
| `full_name` | `string` | No | FullName is the full name of the user (optional) |
| `github_link` | `string` | No | GithubLink is the github link of the user (optional) |
| `github_name` | `string` | No | TwitterLink is the twitter link of the user (optional) |
| `home_page_name` | `string` | No | HomePage is the homepage of the user (optional) |
| `interests` | `string` | No | Interests is the interests of the user (optional) |
| `twitter_link` | `string` | No | TwitterLink is the twitter link of the user (optional) |
| `twitter_name` | `string` | No | TwitterName is the twitter name of the user (optional) |

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
import { patchApiKeyUserProfile } from '@aioz-network/aiozai-sdk';

const response = await patchApiKeyUserProfile({
    body: {
        avatar: '...',  // string
    bio: '...',  // string
    full_name: '...',  // string
    github_link: '...',  // string
    github_name: '...',  // string
    },
});
console.log(response.data);
```

---

### `getApiKeyUserPublicKey`

**`GET /api-key/user/public-key`** — Get source control public keys By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Responses**

**200 OK** — `response.GetPublicKeysResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.GetPublicKeysData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.GetPublicKeysData`**

| Field | Type | Description |
| --- | --- | --- |
| `keys` | `array[models.PublicKey]` |  |

**`models.PublicKey`**

| Field | Type | Description |
| --- | --- | --- |
| `created` | `string` |  |
| `fingerprint` | `string` |  |
| `id` | `integer` |  |
| `key` | `string` |  |
| `key_type` | `string` |  |
| `title` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getApiKeyUserPublicKey } from '@aioz-network/aiozai-sdk';

const response = await getApiKeyUserPublicKey();
console.log(response.data);
```

---

### `postApiKeyUserPublicKey`

**`POST /api-key/user/public-key`** — Create source control public key By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.CreatePublicKeyRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `key` | `string` | Yes | Key is the ssh public key (required) |
| `read_only` | `boolean` | No | ReadOnly is the flag to indicate if the key is read only (default: false) (optional) |
| `title` | `string` | Yes | Title is the title of the key (required) |

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
import { postApiKeyUserPublicKey } from '@aioz-network/aiozai-sdk';

const response = await postApiKeyUserPublicKey({
    body: {
        key: '...',  // string  // required
    read_only: '...',  // boolean
    title: '...',  // string  // required
    },
});
console.log(response.data);
```

---

### `deleteApiKeyUserPublicKeyByKeyid`

**`DELETE /api-key/user/public-key/{keyId}`** — Delete source control public key By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `keyId` | path | `integer` | Yes | key's id |

**Responses**

**200 OK** — `response.SuccessResponse`

| Field | Type | Description |
| --- | --- | --- |
| `message` | `string` |  |
| `status` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { deleteApiKeyUserPublicKeyByKeyid } from '@aioz-network/aiozai-sdk';

const response = await deleteApiKeyUserPublicKeyByKeyid({ path: { keyId: '...' } });
console.log(response.data);
```

---

### `postApiKeyUserStatisticsEarnings`

**`POST /api-key/user/statistics/earnings`** — Get User Earnings Statistics By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.GetTransactionAnalyticsRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `from` | `string` | No | 2023-05-07 15:04:05 |
| `to` | `string` | No | 2024-05-07 15:04:05 |

**Responses**

**200 OK** — `response.UserEarningsStatisticsResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.UserEarningsStatistics` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.UserEarningsStatistics`**

| Field | Type | Description |
| --- | --- | --- |
| `api_calls` | `integer` |  |
| `api_calls_amount` | `number` |  |
| `dataset_used` | `integer` |  |
| `dataset_used_amount` | `number` |  |
| `model_used` | `integer` |  |
| `model_used_amount` | `number` |  |
| `playground_used` | `integer` |  |
| `playground_used_amount` | `number` |  |
| `total` | `number` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { postApiKeyUserStatisticsEarnings } from '@aioz-network/aiozai-sdk';

const response = await postApiKeyUserStatisticsEarnings({
    body: {
        from: '...',  // string
    to: '...',  // string
    },
});
console.log(response.data);
```

---

### `postApiKeyUserStatisticsSpendingCost`

**`POST /api-key/user/statistics/spending-cost`** — Get User Spending Cost Statitics By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.GetUserSpendingCostStatisticsRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `from` | `string` | No | 2023-05-07 15:04:05 |
| `to` | `string` | No | 2023-05-07 15:04:05 |

**Responses**

**200 OK** — `response.UserSpendingCostStatisticsResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.UserSpendingCostStatistics` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.UserSpendingCostStatistics`**

| Field | Type | Description |
| --- | --- | --- |
| `api_calls` | `integer` |  |
| `api_calls_amount` | `number` |  |
| `bandwidth` | `number` |  |
| `bandwidth_amount` | `number` |  |
| `dataset_used` | `integer` |  |
| `dataset_used_amount` | `number` |  |
| `model_used` | `integer` |  |
| `model_used_amount` | `number` |  |
| `playground_used` | `integer` |  |
| `playground_used_amount` | `number` |  |
| `storage` | `number` |  |
| `storage_amount` | `number` |  |
| `total` | `number` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { postApiKeyUserStatisticsSpendingCost } from '@aioz-network/aiozai-sdk';

const response = await postApiKeyUserStatisticsSpendingCost({
    body: {
        from: '...',  // string
    to: '...',  // string
    },
});
console.log(response.data);
```

---

### `postApiKeyUserVoucherClaim`

**`POST /api-key/user/voucher/claim`** — User Claim Free Balance By Voucher By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.UserClaimFreeBalanceByVoucherRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `voucher_code` | `string` | Yes |  |

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
import { postApiKeyUserVoucherClaim } from '@aioz-network/aiozai-sdk';

const response = await postApiKeyUserVoucherClaim({
    body: {
        voucher_code: '...',  // string  // required
    },
});
console.log(response.data);
```

---

### `getApiKeyUserWalletDepositHistory`

**`GET /api-key/user/wallet/deposit/history`** — Get List User Deposit History By Api Key

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

**200 OK** — `response.TxInListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.TxInListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.TxInListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.TxIn]` |  |
| `total` | `integer` |  |

**`models.TxIn`**

| Field | Type | Description |
| --- | --- | --- |
| `aioz_usd_rate` | `number` |  |
| `amount` | `string` |  |
| `block_number` | `integer` |  |
| `cosmos_tx_hash` | `string` |  |
| `created_at` | `string` |  |
| `credit` | `string` |  |
| `evm_tx_hash` | `string` |  |
| `sender` | `string` |  |
| `status` | `boolean` |  |
| `updated_at` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getApiKeyUserWalletDepositHistory } from '@aioz-network/aiozai-sdk';

const response = await getApiKeyUserWalletDepositHistory();
console.log(response.data);
```

---

### `postApiKeyUserWalletTransactionAnalytics`

**`POST /api-key/user/wallet/transaction/analytics`** — Get User Transaction Analytics By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.GetUserTransactionAnalyticsRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `from` | `string` | No | 2023-05-07 15:04:05 |
| `to` | `string` | No | 2023-05-07 15:04:05 |

**Responses**

**200 OK** — `response.TransactionAnalyticsResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `models.TransactionAnalytics` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`models.TransactionAnalytics`**

| Field | Type | Description |
| --- | --- | --- |
| `earnings_analytics` | `models.EarningsAnalytics` |  |
| `spending_analytics` | `models.SpendingAnalytics` |  |

**`models.EarningsAnalytics`**

| Field | Type | Description |
| --- | --- | --- |
| `api_call_earnings` | `number` |  |
| `dataset_earnings` | `number` |  |
| `model_earnings` | `number` |  |
| `playground_earnings` | `number` |  |
| `total_earnings` | `number` |  |

**`models.SpendingAnalytics`**

| Field | Type | Description |
| --- | --- | --- |
| `api_call_used` | `number` |  |
| `bandwidth` | `number` |  |
| `dataset_used` | `number` |  |
| `model_used` | `number` |  |
| `package` | `number` |  |
| `playground_used` | `number` |  |
| `storage` | `number` |  |
| `total_spending` | `number` |  |
| `verify_model` | `number` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { postApiKeyUserWalletTransactionAnalytics } from '@aioz-network/aiozai-sdk';

const response = await postApiKeyUserWalletTransactionAnalytics({
    body: {
        from: '...',  // string
    to: '...',  // string
    },
});
console.log(response.data);
```

---

### `getApiKeyUserWalletTransactionHistory`

**`GET /api-key/user/wallet/transaction/history`** — Get List Transaction History By User By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `limit` | query | `integer` | No |  |
| `offset` | query | `integer` | No |  |
| `type` | query | `string` | No |  |

**Responses**

**200 OK** — `response.TransactionListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.TransactionListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.TransactionListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Transaction]` |  |
| `total` | `integer` |  |
| `total_amount` | `number` |  |
| `total_value` | `number` |  |

**`models.Transaction`**

| Field | Type | Description |
| --- | --- | --- |
| `action` | `string` |  |
| `aioz_usd_rate` | `number` |  |
| `amount` | `number` |  |
| `burn` | `number` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `id` | `string` |  |
| `object_id` | `string` |  |
| `object_type` | `string` |  |
| `updated_at` | `string` |  |
| `user_id` | `string` |  |
| `value` | `number` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getApiKeyUserWalletTransactionHistory } from '@aioz-network/aiozai-sdk';

const response = await getApiKeyUserWalletTransactionHistory();
console.log(response.data);
```

---

### `postApiKeyUserWalletTransactionRecent`

**`POST /api-key/user/wallet/transaction/recent`** — Get List Recent Transaction By User By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Request Body** — `request.GetListRecentTransactionByUserRequest`

| Field | Type | Required | Description |
| --- | --- | --- | --- |
| `from` | `string` | No | 2023-05-07 15:04:05 |
| `limit` | `integer` | No |  |
| `offset` | `integer` | No |  |
| `to` | `string` | No | 2023-05-07 15:04:05 |
| `type` | `string` | No |  |

**Responses**

**200 OK** — `response.TransactionListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.TransactionListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.TransactionListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.Transaction]` |  |
| `total` | `integer` |  |
| `total_amount` | `number` |  |
| `total_value` | `number` |  |

**`models.Transaction`**

| Field | Type | Description |
| --- | --- | --- |
| `action` | `string` |  |
| `aioz_usd_rate` | `number` |  |
| `amount` | `number` |  |
| `burn` | `number` |  |
| `created_at` | `string` |  |
| `description` | `string` |  |
| `id` | `string` |  |
| `object_id` | `string` |  |
| `object_type` | `string` |  |
| `updated_at` | `string` |  |
| `user_id` | `string` |  |
| `value` | `number` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { postApiKeyUserWalletTransactionRecent } from '@aioz-network/aiozai-sdk';

const response = await postApiKeyUserWalletTransactionRecent({
    body: {
        from: '...',  // string
    limit: '...',  // integer
    offset: '...',  // integer
    to: '...',  // string
    type: '...',  // string
    },
});
console.log(response.data);
```

---

### `getApiKeyUserWalletWithdrawHistory`

**`GET /api-key/user/wallet/withdraw/history`** — Get List User Withdrawal History By Api Key

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

**200 OK** — `response.WithdrawalListResponse`

| Field | Type | Description |
| --- | --- | --- |
| `data` | `response.WithdrawalListData` |  |
| `message` | `string` |  |
| `status` | `string` |  |

**`response.WithdrawalListData`**

| Field | Type | Description |
| --- | --- | --- |
| `records` | `array[models.TreasuryWithdrawal]` |  |
| `total` | `integer` |  |

**`models.TreasuryWithdrawal`**

| Field | Type | Description |
| --- | --- | --- |
| `amount` | `number` |  |
| `created_at` | `string` |  |
| `evm_tx_hash` | `string` |  |
| `from_service` | `string` |  |
| `id` | `string` |  |
| `recipient` | `string` |  |
| `sender` | `string` |  |
| `updated_at` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getApiKeyUserWalletWithdrawHistory } from '@aioz-network/aiozai-sdk';

const response = await getApiKeyUserWalletWithdrawHistory();
console.log(response.data);
```

---

### `getApiKeyUserByUsername`

**`GET /api-key/user/{username}`** — Get user's info By Api Key

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

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

```typescript
import { getApiKeyUserByUsername } from '@aioz-network/aiozai-sdk';

const response = await getApiKeyUserByUsername({ path: { username: '...' } });
console.log(response.data);
```

---
