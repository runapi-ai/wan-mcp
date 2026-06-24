# @runapi.ai/wan-mcp

RunAPI MCP server for the **Wan** model line. Create tasks,
poll their status, and check pricing through a single RunAPI API key.

## Tools

- `animate` — create a Wan task (animate) and (optionally) poll until it reaches a terminal status. Returns the task id, status, output URLs, and a price snapshot. Models: `wan-2.2-animate-move`, `wan-2.2-animate-replace`, `wan-2.6-edit-video`, `wan-2.6-flash-edit-video`, `wan-2.7-edit-video`, `wan-2.2-a14b-image-to-video-turbo`, `wan-2.5-image-to-video`, `wan-2.6-flash-image-to-video`, `wan-2.6-image-to-video`, `wan-2.7-image-to-video`, `wan-2.2-a14b-speech-to-video-turbo`, `wan-2.7-image`, `wan-2.7-image-pro`, `wan-2.2-a14b-text-to-video-turbo`, `wan-2.5-text-to-video`, `wan-2.6-text-to-video`, `wan-2.7-r2v`, `wan-2.7-text-to-video`.
- `edit_video` — create a Wan task (edit video) and (optionally) poll until it reaches a terminal status. Returns the task id, status, output URLs, and a price snapshot. Models: `wan-2.2-animate-move`, `wan-2.2-animate-replace`, `wan-2.6-edit-video`, `wan-2.6-flash-edit-video`, `wan-2.7-edit-video`, `wan-2.2-a14b-image-to-video-turbo`, `wan-2.5-image-to-video`, `wan-2.6-flash-image-to-video`, `wan-2.6-image-to-video`, `wan-2.7-image-to-video`, `wan-2.2-a14b-speech-to-video-turbo`, `wan-2.7-image`, `wan-2.7-image-pro`, `wan-2.2-a14b-text-to-video-turbo`, `wan-2.5-text-to-video`, `wan-2.6-text-to-video`, `wan-2.7-r2v`, `wan-2.7-text-to-video`.
- `image_to_video` — create a Wan task (image to video) and (optionally) poll until it reaches a terminal status. Returns the task id, status, output URLs, and a price snapshot. Models: `wan-2.2-animate-move`, `wan-2.2-animate-replace`, `wan-2.6-edit-video`, `wan-2.6-flash-edit-video`, `wan-2.7-edit-video`, `wan-2.2-a14b-image-to-video-turbo`, `wan-2.5-image-to-video`, `wan-2.6-flash-image-to-video`, `wan-2.6-image-to-video`, `wan-2.7-image-to-video`, `wan-2.2-a14b-speech-to-video-turbo`, `wan-2.7-image`, `wan-2.7-image-pro`, `wan-2.2-a14b-text-to-video-turbo`, `wan-2.5-text-to-video`, `wan-2.6-text-to-video`, `wan-2.7-r2v`, `wan-2.7-text-to-video`.
- `speech_to_video` — create a Wan task (speech to video) and (optionally) poll until it reaches a terminal status. Returns the task id, status, output URLs, and a price snapshot. Models: `wan-2.2-animate-move`, `wan-2.2-animate-replace`, `wan-2.6-edit-video`, `wan-2.6-flash-edit-video`, `wan-2.7-edit-video`, `wan-2.2-a14b-image-to-video-turbo`, `wan-2.5-image-to-video`, `wan-2.6-flash-image-to-video`, `wan-2.6-image-to-video`, `wan-2.7-image-to-video`, `wan-2.2-a14b-speech-to-video-turbo`, `wan-2.7-image`, `wan-2.7-image-pro`, `wan-2.2-a14b-text-to-video-turbo`, `wan-2.5-text-to-video`, `wan-2.6-text-to-video`, `wan-2.7-r2v`, `wan-2.7-text-to-video`.
- `text_to_image` — create a Wan task (text to image) and (optionally) poll until it reaches a terminal status. Returns the task id, status, output URLs, and a price snapshot. Models: `wan-2.2-animate-move`, `wan-2.2-animate-replace`, `wan-2.6-edit-video`, `wan-2.6-flash-edit-video`, `wan-2.7-edit-video`, `wan-2.2-a14b-image-to-video-turbo`, `wan-2.5-image-to-video`, `wan-2.6-flash-image-to-video`, `wan-2.6-image-to-video`, `wan-2.7-image-to-video`, `wan-2.2-a14b-speech-to-video-turbo`, `wan-2.7-image`, `wan-2.7-image-pro`, `wan-2.2-a14b-text-to-video-turbo`, `wan-2.5-text-to-video`, `wan-2.6-text-to-video`, `wan-2.7-r2v`, `wan-2.7-text-to-video`.
- `text_to_video` — create a Wan task (text to video) and (optionally) poll until it reaches a terminal status. Returns the task id, status, output URLs, and a price snapshot. Models: `wan-2.2-animate-move`, `wan-2.2-animate-replace`, `wan-2.6-edit-video`, `wan-2.6-flash-edit-video`, `wan-2.7-edit-video`, `wan-2.2-a14b-image-to-video-turbo`, `wan-2.5-image-to-video`, `wan-2.6-flash-image-to-video`, `wan-2.6-image-to-video`, `wan-2.7-image-to-video`, `wan-2.2-a14b-speech-to-video-turbo`, `wan-2.7-image`, `wan-2.7-image-pro`, `wan-2.2-a14b-text-to-video-turbo`, `wan-2.5-text-to-video`, `wan-2.6-text-to-video`, `wan-2.7-r2v`, `wan-2.7-text-to-video`.
- `get_task` — fetch the current status and latest payload for a task.
- `check_pricing` — look up pricing for a model in this line.

## Configuration

Set a RunAPI API key via the `RUNAPI_API_KEY` environment variable, or write
it to `~/.config/runapi/config.json`:

```bash
mkdir -p ~/.config/runapi
echo '{"api_key":"YOUR_KEY"}' > ~/.config/runapi/config.json
```

Get an API key at https://runapi.ai. Pricing is listed at
https://runapi.ai/pricing.

## Usage

Run the server over stdio:

```bash
npx -y @runapi.ai/wan-mcp
```

Add it to an MCP client (see `examples/` for per-client configs):

```json
{
  "mcpServers": {
    "wan": {
      "command": "npx",
      "args": ["-y", "@runapi.ai/wan-mcp"],
      "env": { "RUNAPI_API_KEY": "${RUNAPI_API_KEY}" }
    }
  }
}
```

## License

Apache-2.0
