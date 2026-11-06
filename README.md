# Affitor plugins

Read your Affitor affiliate program in Claude Code or Gemini CLI: partners, commissions, earnings, payouts and billing. Both packages connect to the hosted, read-only MCP server at **https://mcp.affitor.com/mcp** using OAuth. No program API key or local MCP server is required.

The integration guide is included for building Affitor tracking into your application. The hosted MCP connection cannot send tracking events, change data or move money.

## Claude Code

```text
/plugin marketplace add Affitor/claude-plugins
/plugin install affitor@affitor
```

Open `/mcp`, select Affitor, and follow the sign-in flow. Sign in with your Affitor account and review the read-only access on the consent screen. Available tools depend on the brand or partner account you connect.

For an existing installation, run `/plugin marketplace update affitor` and `/plugin update affitor@affitor`, then restart Claude Code and reconnect through `/mcp` if prompted. This replaces the old API-key server; an old program key is not an OAuth credential.

## Gemini CLI

```sh
gemini extensions install https://github.com/Affitor/claude-plugins
```

Start Gemini CLI and run `/mcp auth affitor` to sign in with your Affitor account. The extension requests only the `read` scope and discovers OAuth endpoints automatically. Review the read-only consent before connecting.

For an existing installation, run `gemini extensions update affitor`, restart Gemini CLI, and authenticate again if prompted. Remove any separate, manually configured legacy Affitor server if it would otherwise load alongside this extension. Do not paste an old program API key into OAuth settings.

## Manual remote configuration

Claude Code and clients using its MCP configuration format:

```json
{
  "mcpServers": {
    "affitor": {
      "type": "http",
      "url": "https://mcp.affitor.com/mcp"
    }
  }
}
```

For Gemini CLI, use `httpUrl` and request the read scope:

```json
{
  "mcpServers": {
    "affitor": {
      "httpUrl": "https://mcp.affitor.com/mcp",
      "oauth": { "enabled": true, "scopes": ["read"] }
    }
  }
}
```

Use your client's OAuth sign-in flow after adding the server. Other clients can have different configuration fields; follow the [MCP setup guide](https://affitor.com/docs/api-reference/mcp).

## Integration guide

Fetch [the current integration runbook](https://affitor.com/docs/skill.md) when implementing tracking in your application. Use its documented browser tracker and server-side APIs. Application API keys remain server-side secrets; they are separate from this read-only OAuth connection.

## Links

- MCP setup and supported clients: https://affitor.com/docs/api-reference/mcp
- Integration guide: https://affitor.com/docs/skill.md
- API specification: https://affitor.com/openapi.json
- Affitor: https://affitor.com
