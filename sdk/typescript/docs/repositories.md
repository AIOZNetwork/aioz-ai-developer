# Repositories — TypeScript SDK

> Repository management — code and file repositories. Requires: `x-api-key` header.

Reference: [SDK Usage Guide](../README.md#sdk-usage-guide) | [Package README](../README.md)

---

### `getRepositoryByOwnerusernameByRepositorynameContentReadme`

**`GET /api-key/repository/{ownerUsername}/{repositoryName}/content/readme`** — Get readme file content

**Headers**

| Header | Value | Required |
| --- | --- | --- |
| `x-api-key` | Your API key | Yes |

**Parameters**

| Name | Location | Type | Required | Description |
| --- | --- | --- | --- | --- |
| `ownerUsername` | path | `string` | Yes | repository's owner |
| `repositoryName` | path | `string` | Yes | repository's name |
| `path` | query | `string` | No | Path is the path of the file (required) |
| `ref` | query | `string` | No | Ref is the ref of the commit, name of the branch, default: main (optional) |
| `repoType` | query | `string` | No |  |

**Responses**

**Error Responses**

| Status | Description |
| --- | --- |
| 400 | Bad Request — [response.FailResponse](../README.md#common-response-types) |
| 500 | Internal Server Error — [response.ErrorResponse](../README.md#common-response-types) |

**Example**

```typescript
import { createAiozAIClient, services } from '@aiozai/nodejs-client';

const { rawClient } = createAiozAIClient({ apiKey: process.env.AIOZ_AI_API_KEY });

const response = await services.repositories.getRepositoryByOwnerusernameByRepositorynameContentReadme({
    client: rawClient,
    path: { ownerUsername: '...', repositoryName: '...' },
});
console.log(response.data);
```

---
