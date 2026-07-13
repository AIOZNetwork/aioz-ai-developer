# AIOZ AI Developer

Everything you need to build on the [AIOZ AI](https://aiozai.network) platform: run inference on
models, manage models and datasets, and work with storage, tasks, and organizations.

Pick how you want to build:

| | Use it when |
|---|---|
| **[MCP server](./mcp/)** | You want your coding agent (Claude Code, Cursor, VS Code, …) to use AIOZ AI directly. |
| **[Agent skills](./skills/)** | You're using the MCP server and want your agent to actually know how to run inference. |
| **[SDKs](./sdk/)** | You're writing code. Available for Go, Python, and TypeScript. |

## Get an API key

Log in to [AIOZ AI Platform](https://aiozai.network), go to **Settings → API Keys**, and create
one. You'll need it for everything below.

## MCP server

Give your agent the AIOZ AI toolset. Add it to your client's MCP config:

```json
{
    "mcpServers": {
        "aioz-ai-platform": {
            "command": "npx",
            "args": ["-y", "@aiozai/mcp-server"],
            "env": {
                "AIOZ_AI_API_KEY": "xxxxxxxxxxxxxxxx"
            }
        }
    }
}
```

Then install the skills, so the agent knows the inference lifecycle rather than just the tools:

```bash
npx skills add AIOZNetwork/aioz-ai-developer/skills/aioz-ai-run-inference
npx skills add AIOZNetwork/aioz-ai-developer/skills/aioz-ai-upload-file
```

Full setup, other editors, and a no-Node install: **[mcp/README.md](./mcp/README.md)**.
Tool list: **[mcp/CATALOG.md](./mcp/CATALOG.md)**.

## SDKs

| Language | Package | Docs |
|---|---|---|
| Go | [`aioz-ai-go-client`](https://github.com/AIOZNetwork/aioz-ai-go-client) | [sdk/go/](./sdk/go/) |
| Python | `aiozai-sdk` (PyPI) | [sdk/python/](./sdk/python/) |
| TypeScript | `@aiozai/nodejs-client` (npm) | [sdk/typescript/](./sdk/typescript/) |

All three are generated from the same OpenAPI spec, so they share one design and stay in step with
the API. See **[sdk/README.md](./sdk/README.md)**.

## License

Apache License 2.0. See [LICENSE](./LICENSE).
