# Cursor Marketplace submission

Repository: https://github.com/kamui-project/kamuidash-cursor

Plugin identifier: `kamuidash`

MCP endpoint: `https://api.kamui-platform.com/mcp`

Submission status: **Not submitted.** Repository preparation does not establish Cursor compatibility or Marketplace approval.

[Publisher application draft](publisher-application.md) · [Cursor verification and reviewer walkthrough](reviewer-walkthrough.md)

## Package checklist

- [x] Cursor-format manifest at `.cursor-plugin/plugin.json`.
- [x] Remote MCP definition at the repository root (`mcp.json`).
- [x] Logo committed at `assets/logo.png` and referenced by relative path.
- [x] English and Japanese setup, account requirements, pricing, and troubleshooting documentation.
- [x] MIT license for the plugin files.
- [x] No credentials or private account/project identifiers included.
- [ ] Confirm identifier availability during submission.
- [ ] Complete the Cursor checks below before submission.

## Public endpoint observations

Checked on 2026-10-23 JST using unauthenticated read-only requests:

- `GET /mcp`: HTTP 200, service health response.
- `GET /.well-known/oauth-authorization-server`: HTTP 200, advertises authorization, token, registration endpoints, and S256 PKCE.
- `GET /.well-known/oauth-protected-resource`: HTTP 200, advertises the authorization server and `full` / `offline_access` scopes.
- Unauthenticated `POST /mcp` requests for `initialize` and `tools/list` using curl: HTTP 401 with a `WWW-Authenticate` challenge pointing to the OAuth resource metadata.

The same unauthenticated POST checks using Python urllib were blocked by Cloudflare with HTTP 403 (error 1010, browser signature). This is a client-dependent observation; Cursor transport compatibility remains unverified. No Cloudflare configuration was changed.

These observations do not validate client registration, browser consent, token exchange, tool discovery, or tool execution in Cursor.

## Application and local environment

On 2026-10-23 JST, the browser reached the publisher application entry point and was redirected to Cursor sign-in. The signed-in form could not yet be inspected or filled. No application or terms acceptance has been submitted.

No Cursor application was found in `/Applications` or the user's `Applications` directory during preparation. This does not rule out another installation location. Local plugin execution has not been attempted.

## Cursor checks still required

Record the Cursor version, date, and results without publishing account identifiers or credentials.

- [ ] Load the local plugin and confirm its MCP server appears in Customize.
- [ ] Complete the browser OAuth flow and confirm the expected account.
- [ ] Discover the current tools and list accessible projects.
- [ ] Inspect an existing app, deployment history, and redacted logs.
- [ ] Confirm repository and branch discovery through the KamuiDash GitHub App.
- [ ] With the test account owner's approval of the target and applicable charges, create a disposable app from a connected repository and verify deployment and runtime status.
- [ ] With approval, redeploy the same app and verify the resulting deployment.
- [ ] Record any capabilities not exercised; do not claim that all tools were tested.

## Submit

After completing the checks, sign in at https://cursor.com/marketplace/publish and submit this repository URL. Cursor manually reviews submissions and updates. No review turnaround or acceptance is guaranteed here.

## Official references

- [Plugin format and submission checklist](https://cursor.com/docs/reference/plugins)
- [Local plugin testing](https://cursor.com/docs/plugins#test-plugins-locally)
- [Marketplace security and open-source requirements](https://cursor.com/help/security-and-privacy/marketplace-security)
