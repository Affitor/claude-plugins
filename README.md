# Affitor plugins

Affitor for AI coding tools: the Affitor MCP server (track clicks, leads and sales, check readiness) plus the Affitor integration skill.

## Claude Code

```
/plugin marketplace add Affitor/claude-plugins
/plugin install affitor@affitor
```

Claude Code asks for your **Affitor program API key** (Settings → API in Affitor) and keeps it in secure storage.

## Gemini CLI

```
gemini extensions install https://github.com/Affitor/claude-plugins
```

The CLI asks for the same key and keeps it in the system keychain.

Some Google plans moved from Gemini CLI to Antigravity CLI. If you use Antigravity CLI, see [Google's migration guide](https://antigravity.google/docs/cli/gcli-migration).

## Any other MCP client

```json
{
  "mcpServers": {
    "affitor": {
      "command": "npx",
      "args": ["-y", "@affitor/mcp"],
      "env": { "AFFITOR_API_KEY": "your_program_key" }
    }
  }
}
```

The two tools that move money (`affitor_track_sale`, `affitor_track_refund`) are only available when the server runs with `AFFITOR_MCP_WRITE=1`.

## Links
- Integration guide: https://docs.affitor.com/skill.md
- MCP server: https://www.npmjs.com/package/@affitor/mcp
- Affitor: https://affitor.com
