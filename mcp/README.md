# AIOZ AI Platform MCP Server

The AIOZ AI Platform MCP server gives your coding agent direct access to the AIOZ AI Platform:
run inference on models, manage models and datasets, upload files, check balances and task
history, and work with organizations and repositories.

For the full tool list, see the [MCP Catalog](./CATALOG.md).

> [!NOTE]
> You need an editor or app that supports MCP servers. Verified with **VS Code, Cursor, Trae,
> Antigravity, and Claude Desktop**.

## Prerequisites

- An **AIOZ AI Platform account**.
- An **API key**. Log in to [AIOZ AI Platform](https://aiozai.network), go to
  **Settings → API Keys**, and create one. Public tools (browsing public models and datasets)
  work without a key.

## Install

The server runs locally over `stdio`. Add it to your client's MCP config with your API key in
the `env` block, and every tool call is authenticated automatically.

The `npx` command below downloads the right binary for your platform on first run and caches it.
It needs Node.js. If you don't have Node, use a [pre-built binary](#pre-built-binary-no-nodejs)
instead.

**VS Code** (`.vscode/mcp.json`, or run **MCP: Open User Configuration** for all workspaces):

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

**Cursor** (`.cursor/mcp.json`), **Claude Desktop** (`claude_desktop_config.json`), **Trae**
(`mcp.json`), **Antigravity** (`mcp_config.json`) all use the same shape, with `mcpServers`
instead of `servers`:

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

Where to find the config in each app:

| App | How to open it |
|---|---|
| VS Code | `⌘/Ctrl + Shift + P` → **MCP: Open User Configuration** (global) or **MCP: Open Workspace Folder MCP Configuration** |
| Cursor | **Settings → Cursor Settings → Tools & MCP → + Add Custom MCP** |
| Trae | **Settings → MCP → Add → Add Manually** |
| Antigravity | Side panel → **Agent session → "..." → MCP Servers → Manage MCP Servers → View raw config**, then **Refresh** |
| Claude Desktop | **Settings → Developer → Edit Config** |

### Pre-built binary (no Node.js)

Download your platform's binary from the [Releases](https://github.com/AIOZNetwork/aioz-ai-developer/releases)
page:

| Platform | Binary |
|---|---|
| Linux x86-64 | `aioz-ai-mcp-linux-amd64` |
| Linux ARM64 | `aioz-ai-mcp-linux-arm64` |
| macOS Intel | `aioz-ai-mcp-darwin-amd64` |
| macOS Apple Silicon | `aioz-ai-mcp-darwin-arm64` |
| Windows x86-64 | `aioz-ai-mcp-windows-amd64.exe` |

Make it executable (`chmod +x`, macOS and Linux), then use the same config as above with the
`npx` command swapped for the binary's path:

```json
"command": "/path/to/aioz-ai-mcp",
"args": [],
```

## Agent skills (recommended)

The tools alone don't teach an agent the inference lifecycle. Two skills do:

```bash
npx skills add AIOZNetwork/aioz-ai-developer/skills/aioz-ai-run-inference
npx skills add AIOZNetwork/aioz-ai-developer/skills/aioz-ai-upload-file
```

See [skills/](../skills/) for what they cover.

## API key

Set `AIOZ_AI_API_KEY` in the `env` block of your config, as shown above. The server attaches it to
every request, so tools work without passing a key per call.

To use a different key for one specific call, pass `x_api_key` on that call. It overrides the
configured key for that call only.
