# Cursor Marketplace submission

Repository: https://github.com/kamui-project/kamuidash-cursor

Plugin identifier: `kamuidash`

MCP endpoint: `https://api.kamui-platform.com/mcp`

Submission status: **Submitted; receipt confirmed on 2026-10-23 JST.** The page displayed “Thanks for applying” and “We've received your submission.” Marketplace approval and listing remain pending; submission does not establish Cursor compatibility.

[Publisher application draft](publisher-application.md) · [Cursor verification and reviewer walkthrough](reviewer-walkthrough.md)

## Package checklist

- [x] Cursor-format manifest at `.cursor-plugin/plugin.json`.
- [x] Remote MCP definition at the repository root (`mcp.json`).
- [x] Square logo with a white background plate committed at `assets/marketplace-logo.svg` and referenced by relative path. The original PNG is also retained.
- [x] English and Japanese setup, account requirements, pricing, and troubleshooting documentation.
- [x] MIT license for the plugin files.
- [x] No credentials or private account/project identifiers included.
- [x] Submit the publisher application as SIMD LLC with handle `kamuidash` and confirm receipt.
- [ ] Confirm final publisher namespace approval and Marketplace listing.
- [ ] Complete the remaining Cursor checks below; their pending status was disclosed in the submitted description.

## Public endpoint observations

Checked on 2026-10-23 JST using unauthenticated read-only requests:

- `GET /mcp`: HTTP 200, service health response.
- `GET /.well-known/oauth-authorization-server`: HTTP 200, advertises authorization, token, registration endpoints, and S256 PKCE.
- `GET /.well-known/oauth-protected-resource`: HTTP 200, advertises the authorization server and `full` / `offline_access` scopes.
- Unauthenticated `POST /mcp` requests for `initialize` and `tools/list` using curl: HTTP 401 with a `WWW-Authenticate` challenge pointing to the OAuth resource metadata.

The same unauthenticated POST checks using Python urllib were blocked by Cloudflare with HTTP 403 (error 1010, browser signature). This is a client-dependent observation; Cursor transport compatibility remains unverified. No Cloudflare configuration was changed.

These observations do not validate client registration, browser consent, token exchange, tool discovery, or tool execution in Cursor.

## Application and local environment

On 2026-10-23 JST, the owner completed Cursor sign-in and the publisher application was inspected and filled and submitted after the owner explicitly approved the Publisher Terms. The organization name and plugin author are SIMD LLC; the description identifies this as a company submission with the owner-approved contact email. The fixed Owner remains an individual account. The page confirmed receipt with “Thanks for applying.” No approval, review deadline, or application identifier was displayed. See the application draft for the prepared public field values.

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

## Review status

The accepted application used Organization name `SIMD LLC`, handle `kamuidash`, and this public repository URL. The confirmation page said the plugin would be reviewed. Do not submit another application for the same package merely because the review has not completed. Cursor manually reviews submissions and updates; no review turnaround or acceptance is guaranteed here.

## Official references

- [Plugin format and submission checklist](https://cursor.com/docs/reference/plugins)
- [Local plugin testing](https://cursor.com/docs/plugins#test-plugins-locally)
- [Marketplace security and open-source requirements](https://cursor.com/help/security-and-privacy/marketplace-security)
