# Affitor

Affitor runs affiliate programs for software companies. This package connects to the hosted MCP server at **https://mcp.affitor.com/mcp** with OAuth, using the Affitor account and access selected on the consent screen. No program API key is required for the connection.

## Tools from this package

The hosted connection is **read-only**. A brand can inspect its program, partners, applications, commissions and billing; a partner can inspect joined programs, referral links, earnings, commissions and payouts. Use the tool list actually returned for the connected account. It cannot send clicks, leads, sales or refunds, update account data, or move money.

`get_program` includes the program's tracker snippet and setup checklist. Do not call legacy `affitor_track_*`, `affitor_readiness` or `affitor_run_verification` tools: they are not provided by this remote server. A failed sign-in or refusal is not permission to switch accounts or bypass the consent scope.

## Integration runbook

To implement tracking in an application, fetch **https://affitor.com/docs/skill.md** and follow its steps in order. It covers the identifier contract, browser tracker, server-side lead and sale calls, Stripe, and readiness verification through the documented APIs. Endpoints and fields come from **https://affitor.com/openapi.json**; never invent them. The hosted read-only MCP connection does not replace those application integrations.

## Rules

- Keep application API keys and OAuth credentials private: never print or commit them, or ship them to a browser.
- Use documented test mode while integrating until the application's owner authorizes live events. Read-only access never authorizes a tracking or money write.
- When an integration check reports a blocker, fix it first; do not work around it.
