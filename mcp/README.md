# Installation & Setup: AIOZ AI Platform MCP Server

> [!NOTE]
> You must use a code editor or application that supports MCP servers.

## About the AIOZ AI Platform MCP Server

The AIOZ AI Platform MCP server is a Model Context Protocol (MCP) server provided by AIOZ. It allows you to integrate AI capabilities with the AIOZ AI Platform ecosystem, providing context-aware AI assistance for managing models, datasets, organizations, and platform resources within your IDE.

For a full list of available tools, see the [AIOZ AI Platform MCP Catalog](./CATALOG.md).

## Prerequisites

- An **AIOZ AI Platform account**.
- An **API Key** for authenticated tools — create one in **Settings → API Keys**.
- One of the supported IDEs: **VS Code, Antigravity, Cursor, Trae, Claude Desktop**.

---

## Option 1 — Remote MCP Server

The remote server is hosted by AIOZ. No installation required — add your API Key to the `headers` field in your IDE config and you're ready.

> **Authentication:** Add `"x-api-key": "xxxxxx"` to the `headers` field. The server reads it automatically on every request — no need to pass it per tool call.

### VS Code

1. Press `⌘ Shift P` (Mac) or `Ctrl Shift P` (Windows/Linux) and select:
   - **MCP: Open User Configuration** — applies globally.
   - **MCP: Open Workspace Folder MCP Configuration** — applies to the current workspace only.
2. Paste into `mcp.json`:

```json
{
    "servers": {
        "aioz-ai-platform": {
            "type": "http",
            "url": "https://mcp.aiozai.network/mcp",
            "headers": {
                "x-api-key": "xxxxxxxxxxxxxxxx"
            }
        }
    }
}
```

3. Click **Start** above the server name.


### Antigravity

1. Open the side panel → **Agent session** → **"..."** → **MCP Servers**.
2. Select **Manage MCP Servers** → **View raw config**.
3. Add to `mcp_config.json`:

```json
{
    "mcpServers": {
        "aioz-ai-platform": {
            "type": "http",
            "serverURL": "https://mcp.aiozai.network/mcp",
            "headers": {
                "x-api-key": "xxxxxxxxxxxxxxxx"
            }
        }
    }
}
```

4. Return to **Managed MCP servers** and click **Refresh**.

### Cursor

1. Open **Cursor** → **Settings** → **Cursor Settings** → **Tools & MCP** tab.
2. Click **+ Add Custom MCP** and enter:

```json
{
    "mcpServers": {
        "aioz-ai-platform": {
            "type": "http",
            "url": "https://mcp.aiozai.network/mcp",
            "headers": {
                "x-api-key": "xxxxxxxxxxxxxxxx"
            }
        }
    }
}
```

### Trae

1. Open **TRAE** → **Settings** → **MCP** → **Add** → **Add Manually**.
2. Fill in:

```json
{
    "mcpServers": {
        "aioz-ai-platform": {
            "url": "https://mcp.aiozai.network/mcp",
            "headers": {
                "x-api-key": "xxxxxxxxxxxxxxxx"
            }
        }
    }
}
```

---

## Option 2 — Self-hosted (Run Locally)

Run the server on your own machine via `stdio`. Set your API Key once in the IDE config and every tool call uses it automatically.

> **Authentication:** Set `AIOZ_AI_API_KEY` in the `env` field of your IDE config. The server injects it into every request — no `x_api_key` parameter needed per tool call. Pass `x_api_key` explicitly only when you need to use a different key for a specific call.

### Method A — npx (easiest, no manual install)

The `@aiozai/mcp-server` npm package downloads the right binary for your platform automatically on first run and caches it in `~/.cache/aioz-ai-mcp/`.

#### VS Code — `.vscode/mcp.json`

```json
{
    "servers": {
        "aioz-ai-platform": {
            "type": "stdio",
            "command": "npx",
            "args": ["-y", "@aiozai/mcp-server"],
            "env": {
                "AIOZ_AI_API_KEY": "xxxxxxxxxxxxxxxx"
            }
        }
    }
}
```

#### Antigravity — `mcp_config.json`

```json
{
    "mcpServers": {
        "aioz-ai-platform": {
            "type": "stdio",
            "command": "npx",
            "args": ["-y", "@aiozai/mcp-server"],
            "env": {
                "AIOZ_AI_API_KEY": "xxxxxxxxxxxxxxxx"
            }
        }
    }
}
```

#### Cursor — `.cursor/mcp.json`

```json
{
    "mcpServers": {
        "aioz-ai-platform": {
            "type": "stdio",
            "command": "npx",
            "args": ["-y", "@aiozai/mcp-server"],
            "env": {
                "AIOZ_AI_API_KEY": "xxxxxxxxxxxxxxxx"
            }
        }
    }
}
```

#### Trae — `mcp.json`

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

#### Claude Desktop — `claude_desktop_config.json`

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

### Method B — pre-built binary

Download the binary for your platform from the [GitHub Releases](https://github.com/AIOZNetwork/aioz-ai-developer/releases) page:

| Platform | Binary |
|---|---|
| Linux x86-64 | `aioz-ai-mcp-linux-amd64` |
| Linux ARM64 | `aioz-ai-mcp-linux-arm64` |
| macOS Intel | `aioz-ai-mcp-darwin-amd64` |
| macOS Apple Silicon | `aioz-ai-mcp-darwin-arm64` |
| Windows x86-64 | `aioz-ai-mcp-windows-amd64.exe` |

Make it executable (macOS/Linux), then use the same IDE configs above replacing `"command": "npx"` / `"args": ["-y", "@aiozai/mcp-server"]` with:

```json
"command": "/path/to/aioz-ai-mcp"
```

### Environment variables

| Variable | Default | Description |
|---|---|---|
| `AIOZ_AI_API_KEY` | _(none)_ | Pre-configured API Key. When set, all authenticated tools work without `x_api_key` per call. |
| `AIOZ_API_BASE_URL` | `https://api.aiozai.network/api/v1` | Override the AIOZ API endpoint. |
| `MCP_TRANSPORT` | `stdio` | Transport mode: `stdio`, `sse`, `streamable`, or `all`. |
| `MCP_HTTP_PORT` | `8888` | HTTP port used when transport is `sse`, `streamable`, or `all`. |

---

## Authentication (API Key)

Your API Key is required to call authenticated tools. There are two ways to provide it, depending on which option you chose above.

### Remote MCP — via `headers` field (recommended)

Add your API Key to the `headers` field in your IDE config (shown in each IDE section above). The server reads it from every incoming request automatically — no `x_api_key` parameter needed per tool call.

### Self-hosted — via `AIOZ_AI_API_KEY` env var (recommended)

Set `AIOZ_AI_API_KEY` in the `env` field of your IDE config (shown in each method above). The server injects it automatically and the `x_api_key` parameter becomes optional.

If you need to use a different key for a specific call, pass `x_api_key` explicitly — it overrides the pre-configured value for that call only.

**How to create an API Key:**

1. Log in to [AIOZ AI Platform](https://aiozai.network).
2. Go to **Settings → API Keys**.
3. Click **Create new key**, then copy the value.

> Public tools (e.g. browsing public models and datasets) do not require an API Key.
