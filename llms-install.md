# Installing the PostOnce MCP server (for AI agents)

PostOnce is a hosted remote MCP server. There is nothing to clone, build or run locally.

- Endpoint: `https://postonce.to/mcp`
- Transport: Streamable HTTP
- Auth: OAuth 2.1 (dynamic client registration and PKCE). No API key is needed.

## Cline

Add this entry under `mcpServers` in `cline_mcp_settings.json`:

```json
{
  "mcpServers": {
    "postonce": {
      "type": "streamableHttp",
      "url": "https://postonce.to/mcp",
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

Then ask the user to open the **MCP Servers** panel in Cline and click **Authenticate** on the `postonce` server. Their browser opens to sign in with PostOnce and approve access. When they're done, the server lists its tools.

The user needs a PostOnce account with at least one social account connected. New accounts are free for 7 days at https://postonce.to, with no card required.

## Check that it works

Call `list_active_accounts`. It returns the user's connected social accounts. If it returns none, ask the user to connect one at https://postonce.to/dashboard and call it again.

## Other clients

Clients without OAuth can send the header `Authorization: Bearer <PostOnce API key>` instead. The user creates an API key at https://postonce.to/dashboard/preferences, which needs a paid PostOnce plan. Never ask the user to paste a key into chat. Have them put it in the client's config themselves.

Full docs: https://postonce.to/integrations/mcp
