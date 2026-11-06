# AGENTS.md

Instructions for agents using or maintaining the Affitor plugin and extension.

## Start here

- MCP connection and supported clients: https://affitor.com/docs/api-reference/mcp
- Integration runbook: https://affitor.com/docs/skill.md
- API endpoints and fields: https://affitor.com/openapi.json
- Test mode: https://affitor.com/docs/api-reference/test-mode
- Site index: https://affitor.com/llms.txt

## Package source

- `plugins/affitor/.mcp.json`: Claude Code's hosted HTTP MCP connection, using OAuth.
- `gemini-extension.json`: Gemini CLI's hosted HTTP MCP connection, requesting only the read scope.
- `plugins/affitor/skills/affitor/SKILL.md` and `GEMINI.md`: account-reading and application-integration instructions.

## Rules

- The remote server is read-only. Do not claim it provides legacy tracking-write tools or needs a program API key.
- Application integration uses the documented browser tracker and server-side APIs; keep its API keys server-side and use test mode until live events are authorized.
- Never print, commit or embed API keys or OAuth credentials. Do not add private reports or local evidence to this public repository.
- Keep both package versions and descriptions consistent. Validate the affected package before a PR; merging and releases belong to the repository manager.
