# KamuiDash for Cursor

<img src="assets/logo.png" alt="KamuiDash" width="96" />

Connect Cursor to [KamuiDash](https://dashboard.kamui-platform.com/) to inspect your apps, investigate deployment failures, and deploy from connected GitHub repositories.

[日本語](README.ja.md)

This repository packages the KamuiDash remote MCP connection as a Cursor plugin. The service runs at `https://api.kamui-platform.com/mcp`; no local server or API key is included.

## Requirements

- A Cursor version that supports plugins and remote MCP servers.
- A KamuiDash account with access to the projects you want to manage.
- For repository-based deployments, the KamuiDash GitHub App connected to the intended repository.

## Install for local evaluation

The Cursor Marketplace publisher application was submitted on 2026-10-23 JST and receipt was confirmed. Marketplace approval and listing are pending. Cursor end-to-end authentication and tool execution are pending verification; see the [submission checklist](docs/marketplace.md).

Following [Cursor's local plugin instructions](https://cursor.com/docs/plugins#test-plugins-locally):

```sh
mkdir -p ~/.cursor/plugins/local
git clone https://github.com/kamui-project/kamuidash-cursor.git ~/.cursor/plugins/local/kamuidash
```

Run **Developer: Reload Window** in Cursor, then open **Customize** and locate the plugin and its MCP server. Enterprise installations may require an administrator to allow local plugin imports.

When Cursor requests MCP authentication, sign in to KamuiDash in the browser, check the account and requested access on the consent screen, and approve the connection. The server advertises OAuth discovery and dynamic client registration; a separate client ID or secret should not need to be entered manually. Verify this flow in your Cursor installation before relying on the integration.

### Connect the MCP server directly

To evaluate the connection without installing the plugin, add the following to your existing Cursor MCP configuration (`~/.cursor/mcp.json` for personal use or `.cursor/mcp.json` for a project). Merge it with existing entries rather than replacing the whole file. Use either the plugin or this direct configuration to avoid duplicate server entries.

```json
{
  "mcpServers": {
    "kamuidash": {
      "url": "https://api.kamui-platform.com/mcp"
    }
  }
}
```

## Try it

- “List my KamuiDash projects and summarize their apps and deployment status.”
- “Inspect the latest deployment and runtime logs for my KamuiDash app.”
- “Help me deploy a Node.js app from my connected GitHub repository. Show me the target project, branch, resource settings, and applicable pricing before creating it.”

Repository deployments use the remote GitHub branch. Push your intended changes before requesting a deployment; uncommitted local files are not uploaded by this connection.

Deployment requests are asynchronous. Check deployment history and app runtime status before treating an app as live.

## Access, resource changes, and pricing

The OAuth server advertises `full` and `offline_access` scopes. Access follows the connected KamuiDash account's permissions and is not restricted to one project or read-only operations. Use a dedicated test account for evaluation. Refresh access may keep the connection active until it expires or is revoked.

Creating apps or databases and changing app capacity can incur charges. Updating an app can interrupt a running service. Before asking the agent to change resources, review the target project, source branch, capacity, public exposure, and [current pricing](https://dashboard.kamui-platform.com/en/documents/spec-price-overview), then explicitly approve the intended action.

Manage application secrets and billing settings in the KamuiDash dashboard. Do not paste passwords, API keys, tokens, or database connection strings into chat. Connecting an existing database by ID supplies `DATABASE_URL` automatically.

## Troubleshooting

- **Plugin missing:** confirm that `.cursor-plugin/plugin.json` exists inside the local plugin directory and local imports are allowed, then reload the window.
- **Authentication fails:** use Cursor's MCP output to inspect the error, verify the account shown in the browser, and retry the authentication flow. Discovery availability alone does not prove that a Cursor OAuth flow succeeds.
- **Repository missing:** check the KamuiDash GitHub App installation and the repositories it can access.
- **Deployment pending or failed:** inspect deployment status and logs; an accepted request is not a successful deployment.

Do not include credentials or unredacted logs in public issues. Use the [support form](https://dashboard.kamui-platform.com/en/inquiry) for account-specific assistance.

## Links and license

- [Dashboard](https://dashboard.kamui-platform.com/)
- [Privacy policy](https://dashboard.kamui-platform.com/en/documents/privacy-policy)
- [Terms of use](https://dashboard.kamui-platform.com/en/documents/terms-of-use)
- [Marketplace submission checklist](docs/marketplace.md)
- [Publisher application draft](docs/publisher-application.md)
- [Cursor verification walkthrough](docs/reviewer-walkthrough.md)

The plugin files are licensed under [MIT](LICENSE). Use of the hosted KamuiDash service is governed by its terms and pricing. This license does not grant trademark rights to Kamui branding.
