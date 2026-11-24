# xCloud MCP

Official remote MCP server for [xCloud](https://xcloud.host), the server and site hosting control panel. Ask your AI assistant to manage servers, sites, WordPress, SSL, backups and deploys.

Nothing to install: it is a hosted server.

| | |
|---|---|
| Endpoint | `https://app.xcloud.host/mcp` |
| Transport | Streamable HTTP |
| Auth | OAuth in the browser, or an xCloud API key with the `mcp:invoke` scope as `Authorization: Bearer <key>` |
| Registry name | `host.xcloud/mcp` ([official MCP Registry](https://registry.modelcontextprotocol.io/v0/servers?search=xcloud)) |
| Docs | https://xcloud.host/mcp/ |

Free with every xCloud account ([sign up](https://xcloud.host)). Reads run straight away; anything that creates, changes or deletes asks first.

## Connect

Any client that speaks Streamable HTTP:

```json
{
  "mcpServers": {
    "xcloud": { "url": "https://app.xcloud.host/mcp" }
  }
}
```

OAuth starts on first use. Clients that cap the tool list can use the compact profile: `https://app.xcloud.host/mcp?profile=compact`.

Clients that only run local servers can bridge with [mcp-remote](https://www.npmjs.com/package/mcp-remote):

```bash
npx mcp-remote https://app.xcloud.host/mcp
```

Cline: see [llms-install.md](llms-install.md).

Then ask: *"Who am I on xCloud?"* It should answer with your name, email and team.

## Example prompts

- List all my xCloud servers with CPU, RAM and disk usage, and flag any above 80%.
- Which WordPress sites have plugin updates pending?
- Issue an SSL certificate for example.com.
- Take a backup of my shop site, then deploy the latest commit.
