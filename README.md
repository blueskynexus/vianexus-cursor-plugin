# viaNexus for Cursor

Institutional-grade financial data inside Cursor, powered by the [viaNexus](https://blueskydataplatform.com) MCP server from the BlueSky Data Platform.

Query market data, fundamentals, earnings transcripts, news, and macro indicators directly from your editor.

## Requires a viaNexus subscription

This plugin connects Cursor to your viaNexus account. To use it you need:

1. **A viaNexus subscription** — sign up at [blueskydataplatform.com](https://blueskydataplatform.com)
2. **An API key (`sk_...`)** — generated from your viaNexus dashboard after subscribing
3. **The `VIANEXUS_API_KEY` env var set in Cursor** — Cursor will prompt you for it on install, or you can set it manually

Without a valid key the MCP server will reject every request. The plugin itself is free; access to data requires a paid subscription.

## Install

1. Click **Install** on the [Cursor marketplace listing](https://cursor.com/marketplace) (TBD link once published)
2. When prompted, paste your viaNexus API key — Cursor stores it as `VIANEXUS_API_KEY`
3. Start a new chat and ask Cursor a financial question — it will route through the viaNexus MCP

## What's inside

- `.cursor-plugin/plugin.json` — plugin manifest
- `mcp.json` — points Cursor at the viaNexus MCP server (`https://mcp-service-857389207619.us-central1.run.app`) and wires `x-api-key` auth from `VIANEXUS_API_KEY`
- `assets/logo.svg` — viaNexus brandmark

## Manual MCP config (without the plugin)

If you'd rather skip the marketplace and wire the MCP server directly, add this to your Cursor `mcp.json`:

```json
{
  "mcpServers": {
    "vianexus": {
      "url": "https://mcp-service-857389207619.us-central1.run.app",
      "headers": {
        "x-api-key": "${env:VIANEXUS_API_KEY}"
      }
    }
  }
}
```

Then export `VIANEXUS_API_KEY=sk_...` in your shell.

## Support

- Docs: [blueskydataplatform.com](https://blueskydataplatform.com)
- Email: dilpreet.kaur@blueskydataplatform.com

## License

MIT
