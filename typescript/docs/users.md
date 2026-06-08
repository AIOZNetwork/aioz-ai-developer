# Users — TypeScript SDK

> User management — profiles, keys, wallets, and vouchers. Requires: `x-api-key` header.

Reference: [SDK Usage Guide](../README.md#sdk-usage-guide) | [Package README](../README.md)

---

### `deleteUser`

**`DELETE /api-key/user`** — Delete user's account

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
import { deleteUser } from '@aiozai/nodejs-client';

const response = await deleteUser();
console.log(response.data);
```

---

### `postUserApiKey`

**`POST /api-key/user/api-key`** — Create ApiKey

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
| `balance` | `string` |  |
| `debt` | `string` |  |
| `earnings` | `string` |  |
| `free_balance` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { postUserApiKey } from '@aiozai/nodejs-client';

const response = await postUserApiKey({
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

### `getUserChallengeByWalletaddress`

**`GET /api-key/user/challenge/{walletAddress}`** — Get link wallet address challenge

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
import { getUserChallengeByWalletaddress } from '@aiozai/nodejs-client';

const response = await getUserChallengeByWalletaddress({ path: { walletAddress: '...' } });
console.log(response.data);
```

---

### `patchUserChangePassword`

**`PATCH /api-key/user/change-password`** — Change user's password

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
import { patchUserChangePassword } from '@aiozai/nodejs-client';

const response = await patchUserChangePassword({
    body: {
        new_password: '...',  // string  // required
    old_password: '...',  // string  // required
    },
});
console.log(response.data);
```

---

### `putUserFollowById`

**`PUT /api-key/user/follow/{id}`** — Follow/Unfollow user

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
import { putUserFollowById } from '@aiozai/nodejs-client';

const response = await putUserFollowById({ path: { id: '...' } });
console.log(response.data);
```

---

### `postUserLinkEmail`

**`POST /api-key/user/link-email`** — Verify link email code

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
import { postUserLinkEmail } from '@aiozai/nodejs-client';

const response = await postUserLinkEmail({
    body: {
        code: '...',  // string  // required
    email: '...',  // string  // required
    },
});
console.log(response.data);
```

---

### `patchUserLinkEmailByEmail`

**`PATCH /api-key/user/link-email/{email}`** — Get link email code

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
import { patchUserLinkEmailByEmail } from '@aiozai/nodejs-client';

const response = await patchUserLinkEmailByEmail({
    body: {
        email: '...',  // string
    password: '...',  // string
    username: '...',  // string  // required
    },
});
console.log(response.data);
```

---

### `postUserLinkWallet`

**`POST /api-key/user/link-wallet`** — Verify link wallet address signature

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
import { postUserLinkWallet } from '@aiozai/nodejs-client';

const response = await postUserLinkWallet({
    body: {
        signature: '...',  // string  // required
    wallet_address: '...',  // string  // required
    },
});
console.log(response.data);
```

---

### `getUserMe`

**`GET /api-key/user/me`** — Get user's info

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
| `balance` | `string` |  |
| `debt` | `string` |  |
| `earnings` | `string` |  |
| `free_balance` | `string` |  |

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { getUserMe } from '@aiozai/nodejs-client';

const response = await getUserMe();
console.log(response.data);
```

---

### `getUserOffers`

**`GET /api-key/user/offers`** — Get user's offers

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
import { getUserOffers } from '@aiozai/nodejs-client';

const response = await getUserOffers();
console.log(response.data);
```

---

### `getUserOrgUsernames`

**`GET /api-key/user/org-usernames`** — Get user's organization usernames

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
import { getUserOrgUsernames } from '@aiozai/nodejs-client';

const response = await getUserOrgUsernames();
console.log(response.data);
```

---

### `getUserPermissionSearch`

**`GET /api-key/user/permission/search`** — Search Users

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
import { getUserPermissionSearch } from '@aiozai/nodejs-client';

const response = await getUserPermissionSearch();
console.log(response.data);
```

---

### `patchUserProfile`

**`PATCH /api-key/user/profile`** — Update user's profile

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
import { patchUserProfile } from '@aiozai/nodejs-client';

const response = await patchUserProfile({
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

### `getUserPublicKey`

**`GET /api-key/user/public-key`** — Get source control public keys

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
import { getUserPublicKey } from '@aiozai/nodejs-client';

const response = await getUserPublicKey();
console.log(response.data);
```

---

### `postUserPublicKey`

**`POST /api-key/user/public-key`** — Create source control public key

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
import { postUserPublicKey } from '@aiozai/nodejs-client';

const response = await postUserPublicKey({
    body: {
        key: '...',  // string  // required
    read_only: '...',  // boolean
    title: '...',  // string  // required
    },
});
console.log(response.data);
```

---

### `deleteUserPublicKeyByKeyid`

**`DELETE /api-key/user/public-key/{keyId}`** — Delete source control public key

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
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { deleteUserPublicKeyByKeyid } from '@aiozai/nodejs-client';

const response = await deleteUserPublicKeyByKeyid({ path: { keyId: '...' } });
console.log(response.data);
```

---

### `postUserStatisticsEarnings`

**`POST /api-key/user/statistics/earnings`** — Get User Earnings Statistics

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
import { postUserStatisticsEarnings } from '@aiozai/nodejs-client';

const response = await postUserStatisticsEarnings({
    body: {
        from: '...',  // string
    to: '...',  // string
    },
});
console.log(response.data);
```

---

### `postUserStatisticsSpendingCost`

**`POST /api-key/user/statistics/spending-cost`** — Get User Spending Cost Statitics

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
import { postUserStatisticsSpendingCost } from '@aiozai/nodejs-client';

const response = await postUserStatisticsSpendingCost({
    body: {
        from: '...',  // string
    to: '...',  // string
    },
});
console.log(response.data);
```

---

### `postUserVoucherClaim`

**`POST /api-key/user/voucher/claim`** — User Claim Free Balance By Voucher

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
import { postUserVoucherClaim } from '@aiozai/nodejs-client';

const response = await postUserVoucherClaim({
    body: {
        voucher_code: '...',  // string  // required
    },
});
console.log(response.data);
```

---

### `getUserWalletDepositHistory`

**`GET /api-key/user/wallet/deposit/history`** — Get List User Deposit History

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
import { getUserWalletDepositHistory } from '@aiozai/nodejs-client';

const response = await getUserWalletDepositHistory();
console.log(response.data);
```

---

### `postUserWalletTransactionAnalytics`

**`POST /api-key/user/wallet/transaction/analytics`** — Get User Transaction Analytics

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
import { postUserWalletTransactionAnalytics } from '@aiozai/nodejs-client';

const response = await postUserWalletTransactionAnalytics({
    body: {
        from: '...',  // string
    to: '...',  // string
    },
});
console.log(response.data);
```

---

### `getUserWalletTransactionHistory`

**`GET /api-key/user/wallet/transaction/history`** — Get List Transaction History By User

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
import { getUserWalletTransactionHistory } from '@aiozai/nodejs-client';

const response = await getUserWalletTransactionHistory();
console.log(response.data);
```

---

### `postUserWalletTransactionRecent`

**`POST /api-key/user/wallet/transaction/recent`** — Get List Recent Transaction By User

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
import { postUserWalletTransactionRecent } from '@aiozai/nodejs-client';

const response = await postUserWalletTransactionRecent({
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

### `getUserWalletWithdrawHistory`

**`GET /api-key/user/wallet/withdraw/history`** — Get List User Withdrawal History

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
| `amount` | `string` |  |
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
import { getUserWalletWithdrawHistory } from '@aiozai/nodejs-client';

const response = await getUserWalletWithdrawHistory();
console.log(response.data);
```

---

### `getUserByUsername`

**`GET /api-key/user/{username}`** — Get user's info

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
import { getUserByUsername } from '@aiozai/nodejs-client';

const response = await getUserByUsername({ path: { username: '...' } });
console.log(response.data);
```

---
