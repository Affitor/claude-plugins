# Affitor

Affitor tracks affiliate **click → lead (signup) → sale** and credits each sale to the partner who referred the customer.

## The integration runbook
The full, current runbook lives at **https://docs.affitor.com/skill.md**. Fetch it and follow its steps in order. It covers the identifier contract, the browser tracker, server-side lead and sale calls, Stripe, and the readiness check. Fields and endpoints come from the OpenAPI spec it links; never invent others.

## Tools from this extension
The `affitor` MCP server runs locally (`npx -y @affitor/mcp`) with the program API key you entered when you installed the extension:
- `affitor_get_integration_plan`: the steps this program still needs, for its stack;
- `affitor_readiness`: is tracking live, and what is still missing;
- `affitor_run_verification`: run a test click → lead → sale chain and report what it proves;
- `affitor_track_click`, `affitor_track_lead`: test events;
- `affitor_track_sale`, `affitor_track_refund`: only when the server runs with `AFFITOR_MCP_WRITE=1`, because they move money. Use `testMode` while integrating.

## Rules
- The API key is a server-side secret: never print it, write it into a file, or ship it to a browser.
- Prefer test events (`testMode`) until the founder says the integration is done.
- When readiness reports a blocker, fix that first; do not work around it.
