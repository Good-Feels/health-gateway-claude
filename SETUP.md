---
name: health-gateway-setup
description: Connect Health Gateway to Claude after installing the plugin, or troubleshoot a disconnected Health Gateway connector.
disable-model-invocation: true
---

# Connect Health Gateway

Health Gateway gives Claude read-only access to the Apple Health categories the
user chose to sync from the Health Gateway iPhone app.

1. Confirm the user has installed Health Gateway on iPhone, signed in, selected
   Apple Health categories, completed a sync, and has an active subscription.
2. Enable this plugin if it is disabled. The bundled `health-gateway` remote MCP
   connection uses `https://api.healthgateway.app/mcp`.
3. Start one authorization flow and ask the user to finish it in the browser.
   Never start overlapping authorization attempts or repeatedly retry while a
   browser flow is still open.
4. The user should sign in with the same Apple account used in the iPhone app.
   If Health Gateway offers an account-link code, follow the on-screen steps.
5. After the connection reports ready, verify it with a single read-only request:
   “What Health Gateway data is available for me right now?”

If authorization fails, preserve the error message, wait for the current flow
to finish, and retry once. For help, send the user to
https://healthgateway.app/support. Never request an Apple password, Health data,
OAuth token, or authorization code in chat.
