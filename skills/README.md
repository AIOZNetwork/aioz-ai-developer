# AIOZ AI Agent Skills

Skills that teach a coding agent how to use the [AIOZ AI Platform MCP server](../mcp/README.md)
correctly: the async inference lifecycle, the pre-flight checks, and the presigned file upload
flow.

This directory is the canonical home for these skills. Install them from here.

| Skill | Use it for |
|---|---|
| [`aioz-ai-run-inference`](./aioz-ai-run-inference/) | Running a model end to end: find it, read its schema and cost, check balance, submit, poll, read the result. |
| [`aioz-ai-upload-file`](./aioz-ai-upload-file/) | Getting a public `download_url` for a local file, so you can pass it to a model that takes a file input. |

## Install

The skills are installed with [skills.sh](https://skills.sh). Run these from your project root:

```bash
npx skills add AIOZNetwork/aioz-ai-developer/skills/aioz-ai-run-inference
npx skills add AIOZNetwork/aioz-ai-developer/skills/aioz-ai-upload-file
```

Install both. `aioz-ai-run-inference` hands off to `aioz-ai-upload-file` whenever a model takes a
file input, so on its own it cannot complete a file-based run.

The skills only tell the agent *how* to drive the tools. You still need the MCP server itself
connected, which is a separate step: see the [install guide](../mcp/README.md).

## Requirements

Both skills work in any MCP client, with one exception. **File upload requires a client that can
execute code** (Claude Code, Cursor, VS Code, or similar), because the byte upload to S3 is a
direct HTTP request that the agent makes itself rather than an MCP tool call. In a client without
code execution, such as Claude Desktop, `aioz-ai-upload-file` will tell you it cannot proceed
instead of failing silently. Text and parameter based inference works everywhere.

## Keeping skills and server in step

The skills describe the tool surface of a particular server version. If you upgrade one, upgrade
the other. `npx skills update` pulls the latest version of a skill, which can drift ahead of an
older pinned binary.
