# AGENTS.md

Instructions for AI coding agents (Claude Code, Cursor, Codex, Gemini CLI, Windsurf) that integrate Affitor affiliate tracking into an app.

## Start here
- Integration runbook: https://affitor.com/docs/skill.md. Fetch it and follow its steps in order (identifier contract, browser tracker, server-side lead and sale calls, Stripe, readiness check).
- Endpoints and fields: https://affitor.com/openapi.json. Never invent fields or endpoints that are not in the spec.
- Test mode (prove the integration without real commissions): https://affitor.com/docs/api-reference/test-mode
- Site index for agents: https://affitor.com/llms.txt

## Tools in this repo
- `plugins/affitor/skills/affitor/SKILL.md`: the same runbook as a skill.
- `plugins/affitor/.mcp.json`: the local Affitor MCP server (`npx -y @affitor/mcp`), configured with the program API key.

## Rules
- The program API key is a server-side secret: never print it, commit it, or ship it to a browser.
- Send test events (test mode) until the founder says the integration is done.
- `affitor_track_sale` and `affitor_track_refund` move money and are only available when the MCP server runs with `AFFITOR_MCP_WRITE=1`.
- When the readiness check reports a blocker, fix that first; do not work around it.
