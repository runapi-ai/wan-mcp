<h1 align="center">RunAPI Wan MCP Server</h1>

<p align="center">
  <strong>Wan API access for AI agents: run image and video generation operations, poll asynchronous results, and check pricing through one focused MCP server.</strong>
</p>

<p align="center">
  <sub>Works with Claude Code, Codex, Cursor, Windsurf, VS Code, Roo Code, and any MCP-compatible host.</sub>
</p>

<p align="center">
  <a href="https://www.npmjs.com/package/@runapi.ai/wan-mcp"><img src="https://img.shields.io/npm/v/%40runapi.ai/wan-mcp?style=flat-square&color=blue" alt="npm version"></a>
  <a href="https://github.com/runapi-ai/wan-mcp"><img src="https://img.shields.io/badge/GitHub-runapi--ai%2Fwan--mcp-24292f?style=flat-square" alt="GitHub repository"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-Apache_2.0-blue?style=flat-square" alt="Apache-2.0 license"></a>
  <img src="https://img.shields.io/badge/Type-MCP_Server-blue?style=flat-square" alt="MCP Server">
  <img src="https://img.shields.io/badge/Models-18-16a34a?style=flat-square" alt="18 models">
</p>

<p align="center">
  <a href="#install">Install</a> |
  <a href="#tools">Tools</a> |
  <a href="#models">Models</a> |
  <a href="#agent-prompts">Agent Prompts</a> |
  <a href="#configuration">Configuration</a> |
  <a href="#links">Links</a>
</p>

---

## Why This Package?

`@runapi.ai/wan-mcp` is a focused Model Context Protocol server for the **Wan** model line on RunAPI.
It gives MCP-compatible assistants direct access to 6 endpoints and 18 model variants without loading the full RunAPI catalog.

Use this per-model server when an agent should stay scoped to Wan. Use [`@runapi.ai/mcp`](https://github.com/runapi-ai/mcp) when one assistant should discover every RunAPI model line.

---

## Install

Add it to Claude Code:

```bash
claude mcp add wan -s user -- npx -y @runapi.ai/wan-mcp
```

Use project scope when the server should be shared with a repository:

```bash
claude mcp add wan -s project -- npx -y @runapi.ai/wan-mcp
```

Codex, Cursor, Windsurf, VS Code, Roo Code, and other MCP hosts can use the same stdio command:

```json
{
  "mcpServers": {
    "wan": {
      "command": "npx",
      "args": ["-y", "@runapi.ai/wan-mcp"]
    }
  }
}
```

`check_pricing` works before sign-in. For task creation and status polling, ask your assistant to call the `login` tool. It opens a browser login and saves credentials to `~/.config/runapi/config.json`, the same file used by `runapi login`.
Headless and CI hosts can still set `RUNAPI_API_KEY` before starting the MCP host.

Ready-made examples are in [`examples/`](examples/) for Claude, Cursor, Windsurf, VS Code, and Roo Code.

---

## Tools

| Tool | Auth | Purpose |
|---|---|---|
| `animate` | Yes | Create a Wan animate task and optionally wait for a terminal status. Returns the task id, status, output URLs, and pricing snapshot. |
| `edit_video` | Yes | Create a Wan edit video task and optionally wait for a terminal status. Returns the task id, status, output URLs, and pricing snapshot. |
| `image_to_video` | Yes | Create a Wan image to video task and optionally wait for a terminal status. Returns the task id, status, output URLs, and pricing snapshot. |
| `speech_to_video` | Yes | Create a Wan speech to video task and optionally wait for a terminal status. Returns the task id, status, output URLs, and pricing snapshot. |
| `text_to_image` | Yes | Create a Wan text to image task and optionally wait for a terminal status. Returns the task id, status, output URLs, and pricing snapshot. |
| `text_to_video` | Yes | Create a Wan text to video task and optionally wait for a terminal status. Returns the task id, status, output URLs, and pricing snapshot. |
| `get_task` | Yes | Fetch the current status and latest payload for an existing task. |
| `check_pricing` | No | Look up the current pricing snapshot for a Wan model and endpoint. |

---

## Models

Wan covers 18 model variants across 6 endpoints. Each tool accepts the models listed for it:

| Tool | Models |
|---|---|
| `animate` | `wan-2.2-animate-move`, `wan-2.2-animate-replace` |
| `edit_video` | `wan-2.6-edit-video`, `wan-2.6-flash-edit-video`, `wan-2.7-edit-video` |
| `image_to_video` | `wan-2.2-a14b-image-to-video-turbo`, `wan-2.5-image-to-video`, `wan-2.6-flash-image-to-video`, `wan-2.6-image-to-video`, `wan-2.7-image-to-video` |
| `speech_to_video` | `wan-2.2-a14b-speech-to-video-turbo` |
| `text_to_image` | `wan-2.7-image`, `wan-2.7-image-pro` |
| `text_to_video` | `wan-2.2-a14b-text-to-video-turbo`, `wan-2.5-text-to-video`, `wan-2.6-text-to-video`, `wan-2.7-r2v`, `wan-2.7-text-to-video` |

Model availability can change between releases. Use `check_pricing` or the [Wan model page](https://runapi.ai/models/wan) for the current catalog view.

---

## Agent Prompts

Ask your assistant in natural language; it can inspect pricing, create the task, and return the task id plus output URLs.

### Create a task

```text
Run a Wan animate task with RunAPI.
```

The assistant can call `check_pricing`, then `animate`, and return the task id, status, and output URLs.

### Submit without waiting

```text
Create the task but don't wait for it to finish.
```

The assistant calls the create tool with `wait: false` and returns the task id. Check on it later with `get_task`.

### Check pricing before creating

```text
Check current Wan pricing, then create the task if it matches my request.
```

The assistant calls `check_pricing` and can link to the [Wan model page](https://runapi.ai/models/wan) for the canonical catalog entry.

---

## Configuration

The server resolves auth in this order:

1. `RUNAPI_API_KEY` environment variable, useful for headless and CI hosts
2. `~/.config/runapi/config.json`, created by the MCP `login` tool or `runapi login`
3. No key, which still allows `check_pricing`

The config file is normally managed by login. A pre-provisioned headless config can use:

```json
{
  "apiKey": "your_runapi_key"
}
```

Do not commit real API keys.

---

## Links

| Resource | URL |
|---|---|
| Wan model page | [https://runapi.ai/models/wan](https://runapi.ai/models/wan) |
| npm package | [@runapi.ai/wan-mcp](https://www.npmjs.com/package/@runapi.ai/wan-mcp) |
| GitHub repository | [runapi-ai/wan-mcp](https://github.com/runapi-ai/wan-mcp) |
| RunAPI MCP overview | [runapi.ai/mcp](https://runapi.ai/mcp) |
| RunAPI docs | [runapi.ai/docs](https://runapi.ai/docs) |

---

## License

Licensed under the [Apache License, Version 2.0](LICENSE).
