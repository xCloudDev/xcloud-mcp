# Installing the xCloud MCP server in Cline

xCloud MCP is a hosted (remote) server. There is nothing to clone, build or run locally.

1. The user needs an xCloud account (https://xcloud.host).
2. Ask the user to create an API key in the xCloud dashboard with the `mcp:invoke` scope, and to paste it. Do not invent one.
3. Add this to `cline_mcp_settings.json`, replacing `YOUR_XCLOUD_API_KEY`:

```json
{
  "mcpServers": {
    "xcloud": {
      "type": "streamableHttp",
      "url": "https://app.xcloud.host/mcp?profile=compact",
      "headers": {
        "Authorization": "Bearer YOUR_XCLOUD_API_KEY"
      },
      "disabled": false
    }
  }
}
```

The `compact` profile exposes five tools instead of one per operation, which keeps the tool list small. Drop `?profile=compact` for the full tool set.

4. Verify by calling the server and asking: "Who am I on xCloud?" It returns the user's name, email and team.

Write operations (create, change, delete) ask for confirmation before they run.
